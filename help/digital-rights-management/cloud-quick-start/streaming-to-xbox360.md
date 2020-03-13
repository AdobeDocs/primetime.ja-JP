---
description: 'null'
seo-description: 'null'
seo-title: プレイヤーにXSTSトークンを設定する
title: プレイヤーにXSTSトークンを設定する
uuid: 8995e029-deee-4e23-9cda-a50de8c4f2c0
translation-type: tm+mt
source-git-commit: c37061c116b8a6bc8ce085dc89dc8aadd0a2e490

---


# Xbox360へのストリーミング（オプション） {#streaming-to-xboc360}

Primetime DRMはXbox360プラットフォームでご利用いただけます。 ただし、DRMポリシーの完全なスイートではなく、保護されたストリーミングの使用例のみがサポートされます。 デバイスドメイングループなど、非ストリーミングDRMポリシーの権限はサポートされていません。 Xbox360では、コンテンツを再生しようとすると、サポートされていない権限が無視されます。

XboxのPrimetime DRMポリシーの権限は次のとおりです。
* デジタル出力保護
* ライセンスのオフラインキャッシュの終了日
* ライセンス開始日
* ライセンスの終了日
* 再生時間（秒）

iOS、Android、デスクトップなど、別のPrimetimeプラットフォーム用にパッケージ済みのコンテンツは、Xbox360にストリーミング再生するために再パッケージ化する必要がない場合があります。

Xbox360の注意点の1つは、M3U8でEXT-X-KEYタグが検出されるたびに、キーサーバに常に接続する必要があることです。 DRMポリシーの設定(policy.requireKeyServer)によってiOS PrimetimeビデオプレーヤーがlocalhostからAES復号キーを取得するiOSとは異なり、Xboxは常にリモートキーサーバーから復号キーを取得しようとします。 XboxアプリにlocalhostからAES復号鍵を取得するように指示するDRMポリシーがありません。 この要件のため、EXT-X-KEYエントリはM3U8内で、Primetime Cloud DRMエンドポイントを指している必要があります。 このURLは、OfflinePackager.jar設定ファイルconfig_hls.xmlの&lt;key_url>を介して設定されます。

コンテンツを1回パッケージ化し、すべてのPrimetimeターゲットにストリーム配信し、iOSデバイスでリモートキーサーバーからキーを取得しないように設定する場合は、policy.requireKeyServer=false（policy_ios_localkeyserver.polなど）のプロパティを持つDRMポリシーを使用してコンテンツをパッケージ化できます。 iOSデバイスはAESキーをローカルで取得しますが、Xboxデバイスはこのプロパティを無視し、Primetime Cloud DRMキーサーバーにアクセスして復号キーを取得します。

>！メモ
>
>Xbox360のすべてのリクエストは、カスタム認証/>エンタイトルメントを利用する必要があります。これは、Xbox360プラットフォームでは、Xbox Live/Xbox Secure Token Server(XSTS)トークンを使用して認証を行うためです。
>Primetime Cloud DRMライセンスサーバーは、XSTSトークンを使用して、Xboxデバイスとユーザーの両方の整合性を検証し、>ライセンスの要求を行います。 ただし、XSTSトークンを検証するには、>様のお客様のXbox Liveベンダーの秘密鍵が必要です。Primetime Cloud DRMはこの鍵を保存しません。 このため、Primetime Cloud DRMはXbox 360クライアントから>aライセンスの要求を受け取ると、Primetime Cloud DRM >はXSTSトークンをPrimetimeのお客様のバックエンド/認証/エンタイトルメントサーバーに転送します。 Primetime顧客のサーバー
>は、XSTSトークンを解析して検証し、顧客のアプリケーション発行者キーを使用して>署名されていることを確認します。
>Xbox360クライアントからXSTSトークンを渡すには、MediaPlayer.RequestKeyAttribute >eventに応答してトークンを>同期的に設定します。詳しくは、以下を参照してください。プレ **イヤーにXSTSトークンを設定します。** バックエンド認証/エンタイトルメントサーバーの例は、ソフトウェアリリースの「Custom Authentication」>「Entitlement directory」に含まれています。XSTSトークンの検証については、以下で詳しく説明しています。 **Xbox Live XSTSトークンの検証。**


## プレイヤーにXSTSトークンを設定する {#set-the-xsts-token-in-your-player}

Xbox360では、イベントに応じてトークンを非同期で設定し `MediaPlayer.RequestKeyAttribute` ます。

XSTSトークンを設定します。

ソフトウェアにバンドルされているサンプルアプリでは、XSTSトークンをプレーヤーに設定する方法を示しています。 以下に、サンプルプレーヤーからの関連コードスニペットを示します。

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

## Xbox Live XSTSトークンの検証 {#xbox-live-xsts-token-validation}

XSTS要求の場合、このフィールド `customerSpecificAuthToken` にはBase64エンコードされたXSTSトークンが含まれます。 サンプルコー `XSTSValidator` ドは、Base64でデコードされたトークンを調べて、要素が存在するかどうかを調 `EncryptedAssertion` べます。ただし、他の方法を使用して、Xbox以外のリクエストとXbox以外のリクエストを区別できます。 例えば、別のURLを使用できます。

応答メッセージに返されたポリシーは、Xboxキーの要求で提供されるDRMメタデータの元のポリシーより優先されます。 Xboxクライアントでは、ポリシー機能の一部のみがサポートされ、元のポリシーを上書きするのはこれらのフィールドだけです。

トークンの解読と検証をサポートするために必要な追加の設定手順があります。 および秘密鍵証明書をJKS [!DNL xsts_partner_cert.pfx] 形式 [!DNL x_secure_token_service.part.xboxlive.com.cer] キーストアに読み込み、システムプロパティとしてバックエンドのエンタイトルメントサーバーに提供する必要がありま `xsts-keystore`す。 デフォルトでは、パートナーに [!DNL .pfx] はエイリアスが `xsts`、トークン検証証明書にはエイリアスが割り当てられま `xsts-verify-cert`す。 システムプロパティを使用して、これらを上書きすることもできます。 最後に、デフォルト値を持たないシステ `xsts-keystore-password` ムプロパティがあり、キーストアのパスワードが含まれています。 コードで読み取られるシステムプロ `XSTSValidator` パティを以下にまとめます。

| システムプロパティ | デフォルト値 | コメント |
|---|---|---|
| xsts-keystore | xsts.jks | バリデーターが使用するJKS形式キーストア。 |
| xsts-keystore-password |  | キーストアのパスワード |
| xsts-alias | xsts | キーストアから復号キーを取得するために使用されるエイリアス |
| xsts-verify-cert-alias | xsts-verify-cert | キーストアから検証証明書を取得するために使用されるエイリアス |

## XSTSバリデーター用のJKSの作成{#create-jks-for-an-xsts-validator}

1. パートナーファイル内のプライベート証明書のエイリアス名を確認し [!DNL .pfx] ます。

   ```
   keytool -list -storetype pkcs12 -keystore xsts_partner_cert.pfx -v 
   ```

1. に変 [!DNL .pfx] 換しま [!DNL .jks]す。

   ```
   keytool -importkeystore -srckeystore xsts_partner_cert.pfx -srcstoretype PKCS12 \  
           -keystore xsts.jks -srcalias  
   <alias> -destalias xsts
   ```

   (ここ `<alias>` では、手順1で見つけたプライベート証明書のエイリアス名です)。
1. インポート [!DNL x_secure_token_service.part.xboxlive.com.cer]:

   ```
   keytool -importcert -alias xsts-verify-cert -keystore xsts.jks \  
           -file x_secure_token_service.part.xboxlive.com.cer 
   ```

1. Tomcatのホ [!DNL xsts.jks] ームディレクトリに置き、Tomcat用に定義 `-Dxsts-keystore-password=****` します。

とで異な [!DNL xsts_partner_cert.pfx] るパスワ [!DNL xsts.jks] ードを使用している場合は、でパスワードを `xsts` 更新して同 `jks` じパスワードにします。

```
keytool -keypasswd -keystore xsts.jks -alias xsts 
```
