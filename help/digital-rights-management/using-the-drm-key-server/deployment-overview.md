---
seo-title: Primetime DRMキーサーバーのデプロイの概要
title: Primetime DRMキーサーバーのデプロイの概要
uuid: 86630675-c15d-4f32-8212-d7343f4f92e0
translation-type: tm+mt
source-git-commit: 105dedcfe47a5f454a067e66a95827e638290742

---


# Primetime DRMキーサーバーのデプロイ {#deploy-the-primetime-drm-key-server}

Primetime DRMキーサーバーをデプロイする前に、必要なバージョンのJavaとTomcatがインストールされていることを確認します。 「 [DRMキーサーバーの要件」を参照してください](../../digital-rights-management/using-the-drm-key-server/requirements.md)。

Primetime DRMキーサーバーのダウンロードには、以下が含まれま [!DNL faxsks.war]す。 このWARファイルをデプロイするには、Tomcatのディレクトリにファイルをコピー [!DNL webapps] します。 WARファイルを以前にデプロイした場合は、Tomcatのディレクトリにある、パック解除済みのWARディレクトリを手動で削 [!DNL faxsks] 除する必要がある場合が [!DNL webapps] あります)。 TomcatがWARファイルを展開しないようにするには、Tomcatのデ [!DNL server.xml] ィレクトリでファイルを編集 [!DNL conf] し、属性をに設 `unpackWARs` 定します `false`。

Primetime DRMキーサーバーは、オプションで、（WindowsまたはLinuxで）プラットフォーム固有のラ`jsafe.dll` イブラリを使用してパ `libjsafe.so` フォーマンスを向上させます。 環境変数（またはLinux）で指定した場 `thirdparty/cryptoj/platform` 所に、使用しているプラットフォームに適 `PATH` したライブラリを `LD_LIBRARY_PATH` からコピーします。

>[!NOTE]
>
>64ビット版のライブラリは、オペレーテ [!DNL jsafe] ィングシステムとJDKの両方が64ビットをサポートしている場合にのみ使用し、それ以外の場合は32ビット版を使用します。

## SSL設定 {#ssl-configuration}

SSLは、リモートHTTPSキー配信に必要です。 SSL接続は、アプリケーションサーバー（TomcatでSSLを設定するなど）で処理するか、別のサーバー（ロードバランサー、SSLアクセラレーター、Apacheなど）で処理することができます。 リモートHTTPSキーの配信にはSSL接続が必要です。 サーバーには、信頼できるCAによって発行されたSSL証明書が必要です。

SSLを設定するための様々なオプションがあります。 ApacheおよびTomcatでのクライアント認証を使用したSSLの設定例を次に示します。

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

次の例は、Tomcat SSLの設定を示しています。 証明書とキーファイルを生成するには：

```
Generate key:  
 openssl genrsa -des3 -out server.key 1024 
Generate CSR: 
 openssl req -new -key server.key -out server.csr 
Generate Certificate: 
 openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.cer
```

共通名の入力を求められたら、サーバーの完全修飾ドメイン名(FQDN)を使用します。

とをTomcat [!DNL server.cer]ディレク [!DNL server.key] トリにコピーします。 で次のコネクタを指定しま [!DNL conf/server.xml]す。

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

次の2つのJavaシステムプロパティを設定して、Primetime DRMキーサーバーの設定ファイルとログファイルの場所を変更するオプションがあります。

* `KeyServer.ConfigRoot`  — このディレクトリには、Primetime DRMキーサーバーのすべての設定ファイルが含まれます。 これらのファイルの内容について詳しくは、「キーサーバー設定フ [ァイル」を参照してくださ](#key-server-configuration-files)い。 設定しなかった場合、デフォルトはで [!DNL CATALINA_BASE/keyserver]す。

* `KeyServer.LogRoot` - iOSキーサーバーのアプリケーションログを含むログディレクトリ。 設定しなかった場合、デフォルトは `KeyServer.ConfigRoot`

* `XboxKeyServer.LogRoot` - Xboxキーサーバーのアプリケーションログを格納するログディレクトリです。 設定しなかった場合、デフォルトはと同じで `KeyServer.ConfigRoot`す。

またはを使用してTomcatを起 [!DNL catalina.bat] 動する [!DNL catalina.sh] 場合、これらのシステムプロパティは、環境変数を使用して簡単に設定で `JAVA_OPTS` きます。 ここで設定したJavaオプションは、Tomcatの起動時に使用されます。 例えば、次のように設定します。

```
JAVA_OPTS=-DKeyServer.ConfigRoot=”absolute-path-to-config-folder” 
  -DKeyServer.LogRoot=”absolute-path-to-log-folder”
```

## Primetime DRM秘密鍵証明書 {#primetime-drm-credentials}

Primetime DRM iOSおよびXbox 360クライアントからのキー要求を処理するには、Primetime DRMキーサーバーにアドビが発行した一連の資格情報を設定する必要があります。 これらの秘密鍵証明書は、PKCS#12 ( [!DNL .pfx])ファイルに保存するか、HSMに保存できます。

ファイ [!DNL .pfx] ルは任意の場所に配置できますが、設定を容易にするために、テナントの設定ディレ [!DNL .pfx] クトリにファイルを配置することをお勧めします。 詳しくは、「キーサーバー設定フ [ァイル」を参照してくださ](#key-server-configuration-files)い。

### HSMの設定 {#section_13A19E3E32934C5FA00AEF621F369877}

HSMを使用してサーバー秘密鍵証明書を保存する場合は、秘密鍵と証明書をHSMに読み込み、 *pkcs11.cfg* 設定ファイルを作成する必要があります。 このファイルは、 *KeyServer.ConfigRootディレクトリ内に存在する必要があります* 。 詳しくは、 [!DNL <Primetime DRM Key Server>/configsディレクトリ] （PKCS 11構成ファイルの例）。 の形式について詳しくは、Sun PKCS11 [!DNL pkcs11.cfg]プロバイダのドキュメントを参照してください。

HSMおよびSun PKCS11の設定ファイルが正しく設定されていることを確認するには、ファイルが存在するディレクトリ（Java JREおよびJDKと共にインストールされている）から次のコマンドを [!DNL pkcs11.cfg][!DNL keytool] 使用します。

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

リストに自分の秘密鍵証明書が表示される場合は、HSMが適切に設定され、キーサーバーがその秘密鍵証明書にアクセスできるようになります。

## キーサーバー設定ファイル {#key-server-configuration-files}

Primetime DRMキーサーバーには、次の2種類の設定ファイルが必要です。

* グローバル設定ファイル、 [!DNL flashaccess-keyserver-global.xml]
* 各テナントのテナント設定ファイル、 [!DNL flashaccess-keyserver-tenant.xml]

設定ファイルに変更が加えられた場合は、変更を有効にするためにサーバーを再起動する必要があります。

設定ファイル内のパスワードをクリアテキストで使用できないようにするには、グローバル設定ファイルとテナント設定ファイルで指定されているすべてのパスワードを暗号化する必要があります。 パスワードの暗号化について詳しくは、『Using [*the Primetime *DRM Server for Protected Streaming**](../protected-streaming/understanding-deployment/drm-for-protected-streaming-utilities/password-scrambler.md)』の「Password Scrambler」を参照してください。

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

設定フ [!DNL flashaccess-keyserver-global.xml] ァイルには、キーサーバーのすべてのテナントに適用される設定が含まれます。 このファイルは、に配置する必要がありま `KeyServer.ConfigRoot`す。 グローバル設定フ [!DNL configs] ァイルの例については、ディレクトリを参照してください。 グローバル設定ファイルには、次が含まれます。

* ログ：ログ・レベルと、ログ・ファイルのロール頻度を指定します。
* HSMパスワード — HSMを使用してサーバーの秘密鍵証明書を保存する場合にのみ必要です。

グローバル設定ファイルの例( [!DNL <Primetime DRM Key Server>/configsを参照して] 、詳細を確認してください。

## テナント構成ファイル {#tenant-configuration-files}

および [!DNL flashaccess-ioskeyserver-tenant.xml] 設定フ [!DNL flashaccess-xboxkeyserver-tenant.xml] ァイルには、Primetime DRMキーサーバーの特定のテナントに適用される設定が含まれます。 各テナントは、にこれらの設定ファイルの独自のインスタンスを置いていま [!DNL <KeyServer.ConfigRoot>/faxsks/tenants/tenantname]す。 テナント設定フ [!DNL configs/faxsks/tenants/sampletenant] ァイルの例については、ディレクトリを参照してください。

テナント構成ファイル内のすべてのファイルパスは、絶対パスまたはテナントの構成ディレクトリ( [!DNL <KeyServer.ConfigRoot>/faxsks/tenants/tenantname])を基準とする相対パスとして指定できます。

すべてのテナント構成ファイルには、次が含まれます。

* キーサーバー資格情報 — アドビが発行する1つ以上のキーサーバー資格情報（証明書および秘密鍵）を指定します。 ファイルへのパスとパスワード、また [!DNL .pfx] はHSMに保存されている秘密鍵証明書のエイリアスとして指定できます。 ここでは、ファイルパス、キーエイリアス、またはその両方として指定できる資格情報がいくつかあります。

iOSテナン **ト設定ファイルには** 、次のものが含まれます。

* キー配信期間 — （オプション）キー配信要求のタイムスタンプ有効期間（秒）を指定します。 デフォルト値は500秒です。

Xbox 360テナ **ントの構成ファイルには** 、次のものが含まれます。

* XSTS証明書 — XSTSトークンの復号化に使用するアプリケーション開発者の証明書を指定します。
* XSTS署名証明書 — XSTSトークンの署名を検証するために使用する証明書を指定します。
* Packager Whitelist — キーサーバーによって信頼されるPackager証明書。 リストにパッケージャーの証明書が含まれていない場合は、すべてのパッケージャーの証明書が信頼されます。

## ログファイル {#log-files}

Primetime DRMキーサーバーアプリケーション(および [!DNL flashaccess-ioskeyserver_*.log] )によって生成さ [!DNL flashaccess-xboxkeyserver_*.log]れたログファイルは、で指定されたディレクトリに配置されま `KeyServer.LogRoot`す。

ログファイルは、クライアントの種類によって区別されます。 クライアントタイプごとに2つのログがあります。

* アクセ *スログ* — 要求と応答のみを監視します。
* コンテキ *ストログ* — 詳細なエラーメッセージとスタックトレースが含まれます。

## キーサーバの起動 {#starting-the-key-server}

キーサーバーを起動するには、Tomcatを起動します。