---
title: Primetime DRMキーサーバーのデプロイの概要
description: Primetime DRMキーサーバーのデプロイの概要
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '1075'
ht-degree: 0%

---


# Primetime DRMキーサーバーのデプロイ{#deploy-the-primetime-drm-key-server}

Primetime DRMキーサーバーをデプロイする前に、必要なバージョンのJavaとTomcatがインストールされていることを確認します。 「[DRMキーサーバーの要件](../../digital-rights-management/using-the-drm-key-server/requirements.md)」を参照してください。

Primetime DRMキーサーバーのダウンロードには[!DNL faxsks.war]が含まれます。 このWARファイルを配備するには、Tomcatの[!DNL webapps]ディレクトリにファイルをコピーします。 WARファイルを以前にデプロイした場合は、Tomcatの[!DNL webapps]ディレクトリにある[!DNL faxsks]を手動で削除する必要があります。 TomcatがWARファイルを開くのを防ぐには、Tomcatの[!DNL conf]ディレクトリで[!DNL server.xml]ファイルを編集し、`unpackWARs`属性を`false`に設定します。

Primetime DRMキーサーバーは、オプションで、パフォーマンスを向上させるために、プラットフォーム固有のライブラリ（Windowsでは`jsafe.dll`、Linuxでは`libjsafe.so`）を使用します。 プラットフォームに適したライブラリを`thirdparty/cryptoj/platform`から`PATH`環境変数（Linuxでは`LD_LIBRARY_PATH`）で指定された場所にコピーします。

>[!NOTE]
>
>64ビット版の[!DNL jsafe]ライブラリは、オペレーティングシステムとJDKの両方が64ビットをサポートしている場合にのみ使用し、それ以外の場合は32ビット版を使用します。

## SSL設定{#ssl-configuration}

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

[!DNL server.cer]と[!DNL server.key]をTomcatディレクトリにコピーします。 [!DNL conf/server.xml]に次のコネクタを指定します。

```
<Connector port="8443" protocol="HTTP/1.1" SSLEnabled="true" 
 maxThreads="150" scheme="https" secure="true" 
 sslProtocol="TLS" 
 SSLCertificateFile="${catalina.base}/server.cer" 
 SSLCertificateKeyFile="${catalina.base}/server.key" 
 SSLPassword="password-for-key-file" 
 SSLVerifyClient="require"/>
```

## Javaシステムのプロパティ{#java-system-properties}

次の2つのJavaシステムプロパティを設定して、Primetime DRMキーサーバーの設定ファイルとログファイルの場所を変更できます。

* `KeyServer.ConfigRoot`  — このディレクトリには、Primetime DRMキーサーバーのすべての設定ファイルが含まれています。これらのファイルの内容について詳しくは、[キーサーバー構成ファイル](#key-server-configuration-files)を参照してください。 設定しない場合、デフォルトは[!DNL CATALINA_BASE/keyserver]です。

* `KeyServer.LogRoot` - iOSキーサーバーのアプリケーションログを含むログディレクトリです。設定しない場合、デフォルトは`KeyServer.ConfigRoot`と同じです

* `XboxKeyServer.LogRoot` - Xboxキーサーバーのアプリケーションログを格納するログディレクトリです。設定しない場合、デフォルトは`KeyServer.ConfigRoot`と同じです。

[!DNL catalina.bat]または[!DNL catalina.sh]を使用してTomcatを開始する場合は、`JAVA_OPTS`環境変数を使用して、これらのシステムプロパティを簡単に設定できます。 ここで設定したJavaオプションは、Tomcatの起動時に使用されます。 例えば、次のように設定します。

```
JAVA_OPTS=-DKeyServer.ConfigRoot=”absolute-path-to-config-folder” 
  -DKeyServer.LogRoot=”absolute-path-to-log-folder”
```

## Primetime DRM秘密鍵証明書{#primetime-drm-credentials}

Primetime DRM iOSおよびXbox 360クライアントからのキー要求を処理するには、Primetime DRMキーサーバーにAdobeが発行した一連の資格情報を設定する必要があります。 これらの秘密鍵証明書は、PKCS#12 ([!DNL .pfx])ファイルに格納するか、HSMに格納することができます。

[!DNL .pfx]ファイルはどこにでも配置できますが、設定を容易にするために、Adobeはテナントの設定ディレクトリに[!DNL .pfx]ファイルを配置することを推奨します。 詳しくは、[キーサーバー構成ファイル](#key-server-configuration-files)を参照してください。

### HSM設定{#section_13A19E3E32934C5FA00AEF621F369877}

HSMを使用してサーバー秘密鍵証明書を保存する場合は、秘密鍵と証明書をHSMに読み込んで、*pkcs11.cfg*&#x200B;設定ファイルを作成する必要があります。 このファイルは、*KeyServer.ConfigRoot*&#x200B;ディレクトリに存在する必要があります。 PKCS 11設定ファイルの例については、`<Primetime DRM Key Server>/configs`ディレクトリを参照してください。 [!DNL pkcs11.cfg]の形式について詳しくは、Sun PKCS11プロバイダーのドキュメントを参照してください。

HSMおよびSun PKCS11の設定ファイルが正しく設定されていることを確認するには、[!DNL pkcs11.cfg]ファイルが存在するディレクトリ（[!DNL keytool]はJava JREおよびJDKと共にインストールされています）から次のコマンドを使用します。

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

リストに秘密鍵証明書が表示される場合、HSMは正しく設定され、キーサーバーは秘密鍵証明書にアクセスできます。

## キーサーバー構成ファイル{#key-server-configuration-files}

Primetime DRMキーサーバーには、次の2種類の設定ファイルが必要です。

* グローバル構成ファイル[!DNL flashaccess-keyserver-global.xml]
* 各テナントのテナント構成ファイル[!DNL flashaccess-keyserver-tenant.xml]

設定ファイルに変更が加えられた場合は、サーバーを再起動して、変更を有効にする必要があります。

構成ファイル内のパスワードをクリアテキストで使用できないようにするには、グローバル構成ファイルとテナント構成ファイルで指定されているすべてのパスワードを暗号化する必要があります。 パスワードの暗号化について詳しくは、「*保護されたストリーミング用Primetime DRMサーバーの使用*](../protected-streaming/understanding-deployment/drm-for-protected-streaming-utilities/password-scrambler.md)」の「[*パスワードスクランブラ*」を参照してください。

## 構成ディレクトリ構造{#configuration-directory-structure}

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

## グローバル構成ファイル{#global-configuration-file}

[!DNL flashaccess-keyserver-global.xml]構成ファイルには、キーサーバーのすべてのテナントに適用される設定が含まれています。 このファイルは`KeyServer.ConfigRoot`に配置する必要があります。 グローバル設定ファイルの例については、[!DNL configs]ディレクトリを参照してください。 グローバル設定ファイルには、次の情報が含まれます。

* ログ：ログ・レベルと、ログ・ファイルがロールされる頻度を指定します。
* HSMパスワード — サーバー秘密鍵証明書の保存にHSMが使用される場合にのみ必要です。

詳しくは、`<Primetime DRM Key Server>/configs`にあるグローバル設定ファイルの例のコメントを参照してください。

## テナント構成ファイル{#tenant-configuration-files}

[!DNL flashaccess-ioskeyserver-tenant.xml]および[!DNL flashaccess-xboxkeyserver-tenant.xml]設定ファイルには、Primetime DRMキーサーバーの特定のテナントに適用される設定が含まれています。 各テナントは、[!DNL <KeyServer.ConfigRoot>/faxsks/tenants/tenantname]に配置されたこれらの設定ファイルの独自のインスタンスを持ちます。 テナント設定ファイルの例については、[!DNL configs/faxsks/tenants/sampletenant]ディレクトリを参照してください。

テナント構成ファイル内のすべてのファイルパスは、絶対パスまたはテナントの構成ディレクトリ([!DNL <KeyServer.ConfigRoot>/faxsks/tenants/tenantname])を基準とした相対パスとして指定できます。

テナント構成ファイルには、次のものが含まれます。

* キーサーバー資格情報 —Adobeが発行する1つ以上のキーサーバー資格情報（証明書および秘密鍵）を指定します。 [!DNL .pfx]ファイルとパスワードへのパス、またはHSMに保存されている秘密鍵証明書のエイリアスとして指定できます。 ここでは、ファイルパス、キーエイリアス、またはその両方の資格情報を指定できます。

**iOS**&#x200B;テナント構成ファイルには、次が含まれます。

* キー配信ーウィンドウ — （オプション）キー配信リクエストのタイムスタンプ有効期間（秒）を指定します。 デフォルト値は500秒です。

**Xbox 360**&#x200B;テナント構成ファイルには、次のものが含まれます。

* XSTS秘密鍵証明書 — XSTSトークンの復号化に使用するアプリケーション開発者の秘密鍵証明書を指定します
* XSTS署名証明書 — XSTSトークン上の署名の検証に使用する証明書を指定します。
* Packagerの許可リスト — キーサーバーによって信頼されるPackager証明書。 リストにPackager証明書が含まれていない場合は、すべてのPackager証明書が信頼されます。

## ログファイル{#log-files}

Primetime DRMキーサーバーアプリケーション（[!DNL flashaccess-ioskeyserver_*.log]と[!DNL flashaccess-xboxkeyserver_*.log]）によって生成されるログファイルは、`KeyServer.LogRoot`によって指定されたディレクトリにあります。

ログファイルは、クライアントの種類によって区別されます。 クライアントタイプごとに2つのログがあります。

* *アクセスログ* — 要求と応答のみを監視します。
* A *コンテキストログ* — 詳細なエラーメッセージとスタックトレースが含まれます。

## キーサーバーの起動{#starting-the-key-server}

キーサーバーを開始するには、開始Tomcatを使用します。