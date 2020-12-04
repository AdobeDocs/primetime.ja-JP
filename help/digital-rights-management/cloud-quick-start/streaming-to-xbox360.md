---
description: 'null'
seo-description: 'null'
seo-title: プレイヤーにXSTSトークンを設定する
title: プレイヤーにXSTSトークンを設定する
uuid: 8995e029-deee-4e23-9cda-a50de8c4f2c0
translation-type: tm+mt
source-git-commit: c37061c116b8a6bc8ce085dc89dc8aadd0a2e490
workflow-type: tm+mt
source-wordcount: '843'
ht-degree: 0%

---


# Xbox360へのストリーミング（オプション） {#streaming-to-xboc360}

Primetime DRMはXbox360プラットフォームでご利用いただけます。 ただし、DRMポリシーの完全な権限スイートではなく、保護されたストリーミングの使用例のみがサポートされます。 デバイスドメイングループなどの非ストリーミングDRMポリシー権限はサポートされません。 Xbox360は、コンテンツを再生しようとすると、未サポートの権限を無視します。

Xbox用のPrimetime DRMポリシーの権限は次のとおりです。
* デジタル出力保護
* ライセンスのオフラインキャッシュの終了日
* ライセンス開始日
* ライセンスの終了日
* 再生時間（秒）

iOS、Android、デスクトップなど、別のPrimetimeプラットフォーム用にパッケージ済みのコンテンツがXbox360にストリーミングされる場合は、そのコンテンツをXbox360に再パッケージする必要はありません。

Xbox360の注意点の1つは、M3U8でEXT-X-KEYタグを検出するたびに、キーサーバーに常に接続する必要があるということです。 DRMポリシーの設定(policy.requireKeyServer)によってiOS PrimetimeビデオプレーヤーがlocalhostからAES復号キーを取得するiOSとは異なり、Xboxは常にリモートキーサーバーから復号キーを取得しようとします。 XboxアプリにAES暗号化解除を取得するよう指示するDRMポリシーがありません
キーをlocalhostから取得します。 この要件のため、EXT-X-KEYエントリは、Primetime Cloud DRMエンドポイントを指すM3U8内に存在する必要があります。 このURLは、OfflinePackager.jar構成ファイルのconfig_hls.xmlの&lt;key_url>を介して設定されます。

コンテンツを1回パッケージ化し、すべてのPrimetimeターゲットにストリーム配信したり、iOSデバイスでリモートキーサーバーからキーを取得しないように設定したい場合は、policy.requireKeyServer=falseのプロパティを持つDRMポリシーを使用してコンテンツをパッケージ化できます。 iOSデバイスはAESキーをローカルで取得しますが、Xboxデバイスはこのプロパティを無視し、Primetime Cloud DRMキーサーバーにアクセスします
を返します。

>！注意
>
>Xbox360のすべての要求は、カスタム認証/>エンタイトルメントを利用する必要があります。これは、Xbox360プラットフォームでは、Xbox Live/Xbox Secure Token Server(XSTS)トークンを使用して>認証を行うためです。
>Primetime Cloud DRMライセンスサーバーは、XSTSトークンを使用して、Xboxデバイスとユーザーの整合性を検証し、>ライセンスの要求を行います。 ただし、XSTSトークンの検証には、>様のお客様のXbox Live専用ベンダーキーが必要です。これはPrimetime Cloud DRMでは保存されません。 このため、Primetime Cloud DRMはXbox 360クライアントから>aライセンスの要求を受け取ると、Primetime Cloud DRM>はXSTSトークンをPrimetimeのお客様のバックエンド/認証/権利付与サーバーに転送します。 Primetime顧客のサーバー
>は、XSTSトークンを解析して検証し、顧客のアプリケーション発行者キーを使用して>署名されたことを確認します。
>Xbox360クライアントからXSTSトークンを渡すには、MediaPlayer.RequestKeyAttribute >イベントに応じてトークンを>同期的に設定します。詳しくは、以下を参照してください。**XSTSトークンをプレイヤーに設定します。** ソフトウェアリリースには、バックエンド認証/エンタイトルメントサーバーのサンプルが含まれています。XSTSトークンの検証については、次のリンクを参照してください。 **Xbox Live XSTSトークンの検証**


## プレイヤーにXSTSトークンを設定{#set-the-xsts-token-in-your-player}

Xbox360では、`MediaPlayer.RequestKeyAttribute`イベントに応じてトークンを非同期に設定します。

XSTSトークンを設定します。

ソフトウェアにバンドルされているサンプルアプリでは、プレイヤーにXSTSトークンを設定する方法を示しています。 サンプルプレーヤーからの関連コードスニペットを次に示します。

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

## Xbox Live XSTSトークンの検証{#xbox-live-xsts-token-validation}

XSTS要求の場合、`customerSpecificAuthToken`フィールドにはBase64エンコードされたXSTSトークンが含まれます。 サンプル`XSTSValidator`コードは、Base64でデコードされたトークンを調べ、`EncryptedAssertion`要素が存在するかどうかを調べます。ただし、他の方法を使用して、Xbox以外の要求とXbox以外の要求を区別することができます。 例えば、別のURLを使用できます。

応答メッセージに返されたポリシーは、Xboxキーの要求で提供されたDRMメタデータの元のポリシーに優先します。 Xboxクライアントがサポートするポリシー機能の一部のみがサポートされ、元のポリシーを上書きするのはこれらのフィールドのみです。

トークンの復号化と検証をサポートするために必要な追加の設定手順があります。 [!DNL xsts_partner_cert.pfx]秘密鍵証明書と[!DNL x_secure_token_service.part.xboxlive.com.cer]秘密鍵証明書をJKS形式キーストアに読み込み、バックエンドのエンタイトルメントサーバーにシステムプロパティ`xsts-keystore`として提供する必要があります。 デフォルトでは、パートナー[!DNL .pfx]はエイリアス`xsts`を持ち、トークン検証証明書はエイリアス`xsts-verify-cert`を持ちます。 これらは、システムプロパティを使用して上書きすることもできます。 最後に、デフォルトを持たないシステムプロパティ`xsts-keystore-password`があり、キーストアのパスワードが含まれています。 `XSTSValidator`コードで読み取られるシステムプロパティを以下にまとめます。

| システムプロパティ | デフォルト値 | コメント |
|---|---|---|
| xsts-keystore | xsts.jks | バリデーターで使用されるJKS形式キーストアです。 |
| xsts-keystore-password |  | キーストアのパスワード |
| xsts-alias | xsts | キーストアから復号キーを取得するために使用されるエイリアス |
| xsts-verify-cert-alias | xsts-verify-cert | キーストアから検証証明書を取得するために使用されるエイリアス |

## XSTSバリデーター用のJKSの作成{#create-jks-for-an-xsts-validator}

1. パートナー[!DNL .pfx]ファイルにあるプライベート証明書のエイリアス名を調べます。

   ```
   keytool -list -storetype pkcs12 -keystore xsts_partner_cert.pfx -v 
   ```

1. [!DNL .pfx]を[!DNL .jks]に変換します。

   ```
   keytool -importkeystore -srckeystore xsts_partner_cert.pfx -srcstoretype PKCS12 \  
           -keystore xsts.jks -srcalias  
   <alias> -destalias xsts
   ```

   （`<alias>`は、手順1で見つけたプライベート証明書のエイリアス名です）。
1. [!DNL x_secure_token_service.part.xboxlive.com.cer]を読み込みます。

   ```
   keytool -importcert -alias xsts-verify-cert -keystore xsts.jks \  
           -file x_secure_token_service.part.xboxlive.com.cer 
   ```

1. [!DNL xsts.jks]をTomcatのホームディレクトリに置き、Tomcatの`-Dxsts-keystore-password=****`を定義します。

[!DNL xsts_partner_cert.pfx]と[!DNL xsts.jks]が異なるパスワードを使用している場合は、`jks`の`xsts`パスワードを更新して同じパスワードにします。

```
keytool -keypasswd -keystore xsts.jks -alias xsts 
```
