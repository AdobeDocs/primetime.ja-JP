---
seo-title: Primetime DRMキーサーバーのデプロイの概要
title: Primetime DRMキーサーバーのデプロイの概要
uuid: 86630675-c15d-4f32-8212-d7343f4f92e0
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '1077'
ht-degree: 0%

---


# Primetime DRMキーサーバーのデプロイ {#deploy-the-primetime-drm-key-server}

Primetime DRMキーサーバーをデプロイする前に、必要なバージョンのJavaとTomcatがインストールされていることを確認します。 「 [DRM主要サーバーの要件](../../digital-rights-management/using-the-drm-key-server/requirements.md)」を参照してください。

Primetime DRMキーサーバーのダウンロードには、が含まれ [!DNL faxsks.war]ます。 このWARファイルを配備するには、そのファイルをTomcatの [!DNL webapps] ディレクトリにコピーします。 WARファイルを以前にデプロイした場合は、Tomcatのディレクトリにある、パック解除済みのWARディレクトリ [!DNL faxsks] を手動で削除する必要があり [!DNL webapps] ます。 TomcatがWARファイルを開くのを防ぐには、Tomcatの [!DNL server.xml] ディレクトリで [!DNL conf] ファイルを編集し、 `unpackWARs` 属性をに設定し `false`ます。

Primetime DRMキーサーバーは、オプションで、(WindowsまたはLinux`jsafe.dll` で)プラットフォーム固有のライブラリを使用して、パフォーマンス `libjsafe.so` を向上します。 プラットフォーム用の適切なライブラリを、から、 `thirdparty/cryptoj/platform` 環境変数(またはLinux `PATH``LD_LIBRARY_PATH` )で指定された場所にコピーします。

>[!NOTE]
>
>64ビット版のライブラリは、オペレーティングシステムとJDKの両方が64ビットをサポートしている場合にのみ使用してください。それ以外の場合は、32ビット版を使用してください。 [!DNL jsafe]

## SSL設定 {#ssl-configuration}

リモートHTTPSキーの配信にはSSLが必要です。 SSL接続は、アプリケーションサーバーで処理する（TomcatでSSLを設定する）か、別のサーバーで処理する（ロードバランサー、SSLアクセラレーター、Apacheなど）ことができます。 リモートHTTPSキーの配信にはSSL接続が必要です。 サーバーには、信頼できるCAによって発行されたSSL証明書が必要です。

SSLを設定するための様々なオプションがあります。 ApacheおよびTomcatでのクライアント認証を使用したSSLの設定例を以下に示します。

次の例は、Apache SSLの設定を示しています。

```
SSLEngineon 
SSLCertificateFile "certs/server_cert.pem" 
SSLCertificateKeyFile "certs/server_key.pem" 
SSLOptions +StdEnvVars +FakeBasicAuth -ExportCertData +StrictRequire 
SSLRequireSSL 
ProxyRequests Off 
ProxyPass /https://keyserver-name:port/ 
ProxyPassReverse /https://keyserver-name:port/
```

次の例は、Tomcat SSLの設定を示しています。 証明書ファイルと鍵ファイルを生成するには：

```
Generate key:  
 openssl genrsa -des3 -out server.key 1024 
Generate CSR: 
 openssl req -new -key server.key -out server.csr 
Generate Certificate: 
 openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.cer
```

共通名の入力を求められたら、サーバーの完全修飾ドメイン名(FQDN)を使用します。

と [!DNL server.cer]をTomcatディレクトリ [!DNL server.key] にコピーします。 で次のコネクタを指定しま [!DNL conf/server.xml]す。

```
<Connector port="8443" protocol="HTTP/1.1" SSLEnabled="true" 
 maxThreads="150" scheme="https" secure="true" 
 sslProtocol="TLS" 
 SSLCertificateFile="${catalina.base}/server.cer" 
 SSLCertificateKeyFile="${catalina.base}/server.key" 
 SSLPassword="password-for-key-file" 
 SSLVerifyClient="require"/>
```

## Javaシステムのプロパティ {#java-system-properties}

次の2つのJavaシステムプロパティを設定して、Primetime DRMキーサーバーの設定ファイルとログファイルの場所を変更できます。

* `KeyServer.ConfigRoot`  — このディレクトリには、Primetime DRMキーサーバーのすべての設定ファイルが含まれています。 これらのファイルの内容について詳しくは、 [キーサーバー設定ファイルを参照してください](#key-server-configuration-files)。 設定しない場合、デフォルトはで [!DNL CATALINA_BASE/keyserver]す。

* `KeyServer.LogRoot` - iOSキーサーバーのアプリケーションログを含むログディレクトリです。 設定しなかった場合、デフォルトは `KeyServer.ConfigRoot`

* `XboxKeyServer.LogRoot` - Xboxキーサーバーのアプリケーションログを格納するログディレクトリです。 設定しなかった場合、デフォルトはと同じで `KeyServer.ConfigRoot`す。

Tomcatを使用している場合 [!DNL catalina.bat] や、Tomcatに開始す [!DNL catalina.sh] る場合は、 `JAVA_OPTS` 環境変数を使用して、これらのシステムプロパティを簡単に設定できます。 ここで設定したJavaオプションは、Tomcatの起動時に使用されます。 例えば、次のように設定します。

```
JAVA_OPTS=-DKeyServer.ConfigRoot=”absolute-path-to-config-folder” 
  -DKeyServer.LogRoot=”absolute-path-to-log-folder”
```

## Primetime DRM秘密鍵証明書 {#primetime-drm-credentials}

Primetime DRM iOSおよびXbox 360クライアントからのキー要求を処理するには、Primetime DRMキーサーバーにアドビが発行した一連の資格情報を設定する必要があります。 これらの秘密鍵証明書は、PKCS#12 ( [!DNL .pfx])ファイルに格納することも、HSMに格納することもできます。

ファイルはどこにでも配置できますが、設定を簡単にするために、テナントの設定ディレクトリに [!DNL .pfx][!DNL .pfx] ファイルを配置することをお勧めします。 詳しくは、「 [キーサーバー設定ファイル](#key-server-configuration-files)」を参照してください。

### HSMの設定 {#section_13A19E3E32934C5FA00AEF621F369877}

サーバー秘密鍵証明書の保存にHSMを使用する場合は、秘密鍵と証明書をHSMに読み込み、 *pkcs11.cfg* 設定ファイルを作成する必要があります。 このファイルは、KeyServer.ConfigRoot ** ディレクトリに存在する必要があります。 詳しくは、 [!DNL <Primetime DRM Key Server>/configs] ディレクトリ（PKCS 11構成ファイルの例）。 の形式について詳し [!DNL pkcs11.cfg]くは、Sun PKCS11プロバイダーのドキュメントを参照してください。

HSMおよびSun PKCS11の設定ファイルが正しく設定されていることを確認するには、ファイルが存在するディレクトリ（Java JREおよびJDKと共にインストールされている）から次のコマンド [!DNL pkcs11.cfg][!DNL keytool] を使用します。

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

リストに秘密鍵証明書が表示される場合、HSMは正しく設定され、キーサーバーは秘密鍵証明書にアクセスできます。

## キーサーバー設定ファイル {#key-server-configuration-files}

Primetime DRMキーサーバーには、次の2種類の設定ファイルが必要です。

* グローバル設定ファイル、 [!DNL flashaccess-keyserver-global.xml]
* 各テナントのテナント構成ファイル [!DNL flashaccess-keyserver-tenant.xml]

設定ファイルに変更が加えられた場合は、サーバーを再起動して、変更を有効にする必要があります。

構成ファイル内のパスワードをクリアテキストで使用できないようにするには、グローバル構成ファイルとテナント構成ファイルで指定されているすべてのパスワードを暗号化する必要があります。 パスワードの暗号化について詳しくは、「保護されたストリーミング用のPrimetime DRMサーバーの [*使用&#x200B;*」の「*&#x200B;パスワードスクランブラ&#x200B;*](../protected-streaming/understanding-deployment/drm-for-protected-streaming-utilities/password-scrambler.md)」を参照してください。

## 設定ディレクトリの構造 {#configuration-directory-structure}

設定ディレクトリの構造は次のとおりです。

```
KeyServer.ConfigRoot/  
--flashaccess-keyserver-global.xml 
--pkcs11.cfg (optional) 
--faxsks/ 
----tenants/ 
------tenantname/
---------flashaccess-keyserver-tenant.xml 
---------credential.pfx (optional) 
```

## グローバル設定ファイル {#global-configuration-file}

設定ファイルには、キーサーバーのすべてのテナントに適用される設定が含まれています。 [!DNL flashaccess-keyserver-global.xml] このファイルは、に配置する必要があり `KeyServer.ConfigRoot`ます。 グローバル設定ファイルの例については、 [!DNL configs] ディレクトリを参照してください。 グローバル設定ファイルには、次の情報が含まれます。

* ログ：ログ・レベルと、ログ・ファイルをロールする頻度を指定します。
* HSMパスワード — サーバー秘密鍵証明書の保存にHSMが使用される場合にのみ必要です。

詳しくは、 [!DNL <Primetime DRM Key Server>/configs] 」を参照してください。

## テナント構成ファイル {#tenant-configuration-files}

お [!DNL flashaccess-ioskeyserver-tenant.xml] よび [!DNL flashaccess-xboxkeyserver-tenant.xml] 設定ファイルには、Primetime DRMキーサーバーの特定のテナントに適用される設定が含まれています。 各テナントは、に配置されたこれらの設定ファイルの独自のインスタンスを持ち [!DNL <KeyServer.ConfigRoot>/faxsks/tenants/tenantname]ます。 テナント構成ファイルの例については、 [!DNL configs/faxsks/tenants/sampletenant] ディレクトリを参照してください。

テナント構成ファイル内のすべてのファイルパスは、絶対パスまたはテナントの構成ディレクトリを基準とする相対パス( [!DNL <KeyServer.ConfigRoot>/faxsks/tenants/tenantname])として指定できます。

テナント構成ファイルには、次のものが含まれます。

* キーサーバー資格情報 — アドビが発行する1つ以上のキーサーバー資格情報（証明書および秘密鍵）を指定します。 ファイルとパスワードへのパス、またはHSMに保存されている秘密鍵証明書のエイリアスとして指定でき [!DNL .pfx] ます。 ここでは、ファイルパス、キーエイリアス、またはその両方の資格情報を指定できます。

iOS **** テナント設定ファイルには、次の設定が含まれます。

* キー配信ーウィンドウ — （オプション）キー配信リクエストのタイムスタンプ有効期間（秒）を指定します。 デフォルト値は500秒です。

Xbox 360 **テナント構成ファイルには** 、次の設定が含まれます。

* XSTS秘密鍵証明書 — XSTSトークンの復号化に使用するアプリケーション開発者の秘密鍵証明書を指定します
* XSTS署名証明書 — XSTSトークン上の署名の検証に使用する証明書を指定します。
* Packagerの許可リスト — キーサーバーによって信頼されるPackager証明書。 リストにPackager証明書が含まれていない場合は、すべてのPackager証明書が信頼されます。

## ログファイル {#log-files}

Primetime DRMキーサーバーアプリケーション( [!DNL flashaccess-ioskeyserver_*.log] および [!DNL flashaccess-xboxkeyserver_*.log])によって生成されるログファイルは、で指定されたディレクトリにあり `KeyServer.LogRoot`ます。

ログファイルは、クライアントの種類によって区別されます。 クライアントタイプごとに2つのログがあります。

* アク *セスログ* — 要求と応答のみを監視します。
* コン *テキストログ* — 詳細なエラーメッセージとスタックトレースが含まれます。

## キーサーバーの起動 {#starting-the-key-server}

キーサーバーを開始するには、開始Tomcatを使用します。