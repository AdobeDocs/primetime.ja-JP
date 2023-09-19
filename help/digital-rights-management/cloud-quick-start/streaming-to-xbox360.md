---
title: プレーヤーでの XSTS トークンの設定
description: プレーヤーでの XSTS トークンの設定
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 0%

---

# Xbox 360 へのストリーミング（オプション） {#streaming-to-xboc360}

Primetime DRM は Xbox360 プラットフォームで利用できます。 ただし、DRM ポリシー権限の完全なスイートではなく、保護されたストリーミングの使用例のみがサポートされます。 デバイスドメイングループなどの非ストリーミング DRM ポリシー権限はサポートされていません。 Xbox360 は、コンテンツを再生しようとする際に、サポートされていない権利を無視します。

Xbox でサポートされる Primetime DRM ポリシーの権限は次のとおりです。
* デジタル出力保護
* ライセンスオフラインキャッシュの終了日
* ライセンス開始日
* ライセンス終了日
* 再生ウィンドウの時間（秒）

iOS、Android、デスクトップなど、別の Primetime プラットフォーム用に既にパッケージ化されている場合は、Xbox360 にストリーミングするためにコンテンツを再パッケージ化する必要がない場合があります。

Xbox360 で注意すべき点は、M3U8 で EXT-X-KEY タグが検出されるたびに、キーサーバに常に接続する必要があることです。 DRM ポリシー設定 (policy.requireKeyServer) によってiOS Primetime ビデオプレーヤーが localhost から AES 復号キーを取得するiOSとは異なり、Xbox は常にリモートキーサーバーから復号キーを取得しようとします。 Xbox アプリに対して、localhost から AES 復号キーを取得するように指示する DRM ポリシーがありません。 この要件のため、EXT-X-KEY エントリは、Primetime Cloud DRM エンドポイントを指す M3U8 に存在する必要があります。 この URL はで設定されます。 &lt;key_url> OfflinePackager.jar 設定ファイル config_hls.xml に含まれます。

コンテンツを 1 回パッケージ化し、すべての Primetime ターゲットにストリーミングすると共に、iOSデバイスがリモートキーサーバーからキーを取得しないように設定する場合は、 policy.requireKeyServer=false プロパティを持つ DRM ポリシー（ policy_ios_localkeyserver.pol など）を使用してコンテンツをパッケージ化できます。 iOSデバイスは AES キーをローカルで取得しますが、Xbox デバイスはこのプロパティを無視し、Primetime Cloud DRM キーサーバーに連絡して復号化キーを取得します。

>！注意
>
>Xbox360 のすべてのリクエストで、「カスタム認証/> 使用権限」が必要です。これは、Xbox360 プラットフォームでは、Xbox Live が Xbox セキュアトークンサーバー (XSTS) トークンを使用して認証を行うためです。
>Primetime Cloud DRM ライセンスサーバーは、XSTS トークンを使用して、Xbox デバイスとライセンスリクエストを行うユーザーの両方の整合性を検証します。 ただし、XSTS トークンを検証するには、Primetime Cloud DRM が保存していない、お客様のプライベート Xbox Live ベンダーキーが必要です。 このため、Primetime Cloud DRM が Xbox 360 クライアントからライセンスのリクエストを受け取ると、Primetime Cloud DRM は XSTS トークンを Primetime のお客様のバックエンド/認証/権利付与サーバーに転送します。 Primetime 顧客のサーバー
>次に、は XSTS トークンを解析および検証し、顧客のアプリケーション発行者キーを使用して署名されたことを確認します。
>Xbox360 クライアントから XSTS トークンを渡すには、MediaPlayer.RequestKeyAttribute > イベントに同期的にトークンを設定します。詳しくは、以下を参照してください。 **プレーヤーで XSTS トークンを設定します。** ソフトウェアリリースには、カスタム認証と権限付与ディレクトリのバックエンド認証/権限付与サーバーのサンプルが含まれています。XSTS トークンの検証については、以下で詳しく説明します。 **Xbox Live XSTS トークンの検証。**


## プレーヤーでの XSTS トークンの設定 {#set-the-xsts-token-in-your-player}

Xbox360 では、 `MediaPlayer.RequestKeyAttribute` イベント。

XSTS トークンを設定します。

ソフトウェアにバンドルされているサンプルアプリでは、プレーヤーで XSTS トークンを設定する方法を示しています。 サンプルプレーヤーの関連するコードスニペットを次に示します。

```
   MediaPlayer mMediaPlayer;  
 
mMediaPlayer.RequestKeyAttribute += Player_RequestKeyAttribute;  
 
private void Player_RequestKeyAttribute(object sender, RequestKeyAttributeEventArgs args) {  
    string token = "";  
    // XBOX XSTS Token...  
    KeyAttribute keyAttribute = new KeyAttribute(System.Text.Encoding.UTF8.GetBytes(token), null);  
    mMediaPlayer.SetKeyAttribute(args.RequestIdentifier, keyAttribute);  
} 
```

## Xbox Live XSTS トークンの検証 {#xbox-live-xsts-token-validation}

XSTS 要求の場合、 `customerSpecificAuthToken` フィールドには、Base64 エンコードされた XSTS トークンが含まれます。 サンプル `XSTSValidator` コードは、Base64 でデコードされたトークンを調べ、 `EncryptedAssertion` 要素に含まれます。ただし、他の方法を使用して、これらの要求と Xbox 以外の要求を区別することができます。 例えば、別の URL を使用できます。

返信メッセージに返されたポリシーは、Xbox キーのリクエストで提供された DRM メタデータの元のポリシーを上書きします。 Xbox クライアントでは、ポリシー機能の一部のみがサポートされ、元のポリシーを上書きするのはこれらのフィールドだけです。

トークンの復号化と検証をサポートするために必要な追加の設定手順があります。 次を読み込む必要があります： [!DNL xsts_partner_cert.pfx] および [!DNL x_secure_token_service.part.xboxlive.com.cer] 資格情報を JKS 形式のキーストアに格納します。その後、システムプロパティとしてバックエンドの権限付与サーバーに指定します。 `xsts-keystore`. デフォルトでは、パートナー [!DNL .pfx] にエイリアスが含まれている `xsts`の場合、トークン検証証明書にはエイリアスが含まれています。 `xsts-verify-cert`. また、システムプロパティを使用してこれらを上書きすることもできます。 最後に、システムプロパティがあります。 `xsts-keystore-password` にはデフォルト値がなく、キーストアのパスワードが含まれています。 が読み取るシステムプロパティ `XSTSValidator` コードの概要を次に示します。

| システムプロパティ | デフォルト値 | コメント |
|---|---|---|
| xsts-keystore | xsts.jks | バリデーターで使用される JKS 形式キーストア。 |
| xsts-keystore-password | | キーストアのパスワード |
| xsts-alias | xsts | キーストアから復号キーを取得するために使用されるエイリアス |
| xsts-verify-cert-alias | xsts-verify-cert | キーストアから検証証明書を取得するために使用するエイリアス |

## XSTS バリデーター用の JKS の作成{#create-jks-for-an-xsts-validator}

1. プライベート証明書のエイリアス名は、パートナーにあります。 [!DNL .pfx] ファイル。

   ```
   keytool -list -storetype pkcs12 -keystore xsts_partner_cert.pfx -v 
   ```

1. 変換 [!DNL .pfx] から [!DNL .jks].

   ```
   keytool -importkeystore -srckeystore xsts_partner_cert.pfx -srcstoretype PKCS12 \  
           -keystore xsts.jks -srcalias  
   <alias> -destalias xsts
   ```

   ( ここで `<alias>` は、手順 1 で検出したプライベート証明書のエイリアス名です。)
1. インポート [!DNL x_secure_token_service.part.xboxlive.com.cer].

   ```
   keytool -importcert -alias xsts-verify-cert -keystore xsts.jks \  
           -file x_secure_token_service.part.xboxlive.com.cer 
   ```

1. Put [!DNL xsts.jks] Tomcat ホームディレクトリで、 `-Dxsts-keystore-password=****` Tomcat の場合。

次の場合 [!DNL xsts_partner_cert.pfx] および [!DNL xsts.jks] 別のパスワードを使用している場合は、 `xsts` パスワード入力 `jks` 同じにするために。

```
keytool -keypasswd -keystore xsts.jks -alias xsts 
```
