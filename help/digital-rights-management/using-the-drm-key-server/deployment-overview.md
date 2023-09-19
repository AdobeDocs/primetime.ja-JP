---
title: Primetime DRM キーサーバーのデプロイの概要
description: Primetime DRM キーサーバーのデプロイの概要
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1075'
ht-degree: 0%

---

# Primetime DRM キーサーバーのデプロイ {#deploy-the-primetime-drm-key-server}

Primetime DRM キーサーバーをデプロイする前に、必要なバージョンの Java および Tomcat がインストールされていることを確認してください。 詳しくは、 [DRM キーサーバーの要件](../../digital-rights-management/using-the-drm-key-server/requirements.md).

Primetime DRM キーサーバーのダウンロードには以下が含まれます [!DNL faxsks.war]. この WAR ファイルをデプロイするには、そのファイルを Tomcat の [!DNL webapps] ディレクトリ。 WAR ファイルを既に展開している場合は、パック解除された WAR ディレクトリを手動で削除する必要がある場合があります。 [!DNL faxsks] Tomcat の [!DNL webapps] ディレクトリ ) に書き込まれます。 Tomcat が WAR ファイルを展開しないようにするには、 [!DNL server.xml] Tomcat のファイル [!DNL conf] ディレクトリに移動し、 `unpackWARs` 属性 `false`.

Primetime DRM キーサーバーでは、オプションでプラットフォーム固有のライブラリ (`jsafe.dll` (Windows または `libjsafe.so` （Linux の場合）パフォーマンスを向上させるために使用します。 プラットフォームに適したライブラリを次の場所からコピーします。 `thirdparty/cryptoj/platform` を `PATH` 環境変数 ( または `LD_LIBRARY_PATH` （Linux の場合）。

>[!NOTE]
>
>64 ビット版の [!DNL jsafe] ライブラリは、オペレーティングシステムと JDK の両方が 64 ビットをサポートしている場合にのみ使用し、それ以外の場合は 32 ビットバージョンを使用します。

## SSL 設定 {#ssl-configuration}

リモート HTTPS キー配信には SSL が必要です。 SSL 接続は、アプリケーションサーバー（Tomcat で SSL を設定）で処理するか、別のサーバー（ロードバランサー、SSL アクセラレーター、Apache）で処理できます。 リモート HTTPS キー配信には SSL 接続が必要です。 サーバーには、信頼された CA が発行した SSL 証明書が必要です。

SSL を設定するには、様々なオプションがあります。 Apache および Tomcat でクライアント認証を使用して SSL を設定する場合の例を以下に示します。

次の例に、Apache SSL の設定を示します。

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

次の例は、Tomcat SSL の設定を示しています。 証明書およびキーファイルを生成するには：

```
Generate key:  
 openssl genrsa -des3 -out server.key 1024 
Generate CSR: 
 openssl req -new -key server.key -out server.csr 
Generate Certificate: 
 openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.cer
```

共通名の入力を求められたら、サーバーの完全修飾ドメイン名 (FQDN) を使用します。

コピー [!DNL server.cer]、および [!DNL server.key] を Tomcat ディレクトリに追加します。 で次のコネクタを指定します。 [!DNL conf/server.xml]:

```
<Connector port="8443" protocol="HTTP/1.1" SSLEnabled="true" 
 maxThreads="150" scheme="https" secure="true" 
 sslProtocol="TLS" 
 SSLCertificateFile="${catalina.base}/server.cer" 
 SSLCertificateKeyFile="${catalina.base}/server.key" 
 SSLPassword="password-for-key-file" 
 SSLVerifyClient="require"/>
```

## Java システムプロパティ {#java-system-properties}

次の 2 つの Java システムプロパティを設定して、Primetime DRM キーサーバーの設定ファイルとログファイルの場所を変更できます。

* `KeyServer.ConfigRoot`  — このディレクトリには、Primetime DRM キーサーバーのすべての設定ファイルが含まれます。 これらのファイルの内容について詳しくは、 [キーサーバーの設定ファイル](#key-server-configuration-files). 設定しない場合、デフォルトはです。 [!DNL CATALINA_BASE/keyserver].

* `KeyServer.LogRoot` - iOSキーサーバーアプリケーションのログを格納するログディレクトリです。 設定しない場合、デフォルトは `KeyServer.ConfigRoot`

* `XboxKeyServer.LogRoot`  — これは、Xbox キーサーバーのアプリケーションログを含むログディレクトリです。 設定しない場合、デフォルトは `KeyServer.ConfigRoot`.

を使用している場合、 [!DNL catalina.bat] または [!DNL catalina.sh] Tomcat を起動するには、 `JAVA_OPTS` 環境変数。 ここで設定した Java オプションは、Tomcat の起動時に使用されます。 例えば、次のように設定します。

```
JAVA_OPTS=-DKeyServer.ConfigRoot=”absolute-path-to-config-folder” 
  -DKeyServer.LogRoot=”absolute-path-to-log-folder”
```

## Primetime DRM 資格情報 {#primetime-drm-credentials}

Primetime DRM iOSおよび Xbox 360 クライアントからのキー要求を処理するには、Primetime DRM キーサーバーにAdobeから発行された一連の資格情報を設定する必要があります。 これらの資格情報は、PKCS#12 ( [!DNL .pfx]) ファイルまたは HSM 上に書き込むことができます。

The [!DNL .pfx] ファイルはどこでも配置できますが、設定を簡単にするために、Adobeでは [!DNL .pfx] テナントの設定ディレクトリ内のファイル。 詳しくは、 [キーサーバーの設定ファイル](#key-server-configuration-files).

### HSM 設定 {#section_13A19E3E32934C5FA00AEF621F369877}

HSM を使用してサーバーの資格情報を保存する場合は、秘密鍵と証明書を HSM に読み込み、 *pkcs11.cfg* 設定ファイル。 このファイルは、 *KeyServer.ConfigRoot* ディレクトリ。 詳しくは、 `<Primetime DRM Key Server>/configs` サンプルの PKCS 11 構成ファイル用のディレクトリ。 の形式について詳しくは、 [!DNL pkcs11.cfg]（ Sun PKCS11 プロバイダのドキュメントを参照）。

HSM および Sun PKCS11 の設定ファイルが正しく設定されていることを確認するには、次のコマンドを、 [!DNL pkcs11.cfg] ファイルが見つかりました ( [!DNL keytool] は、Java JRE および JDK と共にインストールされます )。

```
keytool -keystore NONE -storetype PKCS11 -providerClass sun.security.pkcs11.SunPKCS11 
  -providerArg pkcs11.cfg -list
```

リストに自分の資格情報が表示された場合、HSM は正しく設定され、キーサーバーがその資格情報にアクセスできるようになります。

## キーサーバーの設定ファイル {#key-server-configuration-files}

Primetime DRM キーサーバーには、次の 2 種類の設定ファイルが必要です。

* グローバル設定ファイル [!DNL flashaccess-keyserver-global.xml]
* 各テナントのテナント設定ファイル [!DNL flashaccess-keyserver-tenant.xml]

設定ファイルに変更を加えた場合、変更を有効にするには、サーバを再起動する必要があります。

設定ファイル内のクリアテキストでパスワードを使用できないようにするには、グローバルおよびテナントの設定ファイルで指定されているすべてのパスワードを暗号化する必要があります。 パスワードの暗号化の詳細については、 [*パスワードスクランブラ* in *保護されたストリーミング用の Primetime DRM サーバーの使用*](../protected-streaming/understanding-deployment/drm-for-protected-streaming-utilities/password-scrambler.md).

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

The [!DNL flashaccess-keyserver-global.xml] 設定ファイルには、キーサーバーのすべてのテナントに適用される設定が含まれています。 このファイルは、 `KeyServer.ConfigRoot`. 詳しくは、 [!DNL configs] ディレクトリを参照してください。 グローバル設定ファイルには、次の内容が含まれます。

* ログ — ログレベルとログファイルのロール頻度を指定します。
* HSM パスワード — サーバーの資格情報を保存するために HSM が使用されている場合にのみ必要です。

次の場所にあるグローバル設定ファイル例のコメントを参照してください。 `<Primetime DRM Key Server>/configs` を参照してください。

## テナント設定ファイル {#tenant-configuration-files}

The [!DNL flashaccess-ioskeyserver-tenant.xml] および [!DNL flashaccess-xboxkeyserver-tenant.xml] 設定ファイルには、Primetime DRM キーサーバーの特定のテナントに適用される設定が含まれています。 各テナントには、次の場所にあるこれらの設定ファイルの独自のインスタンスがあります。 [!DNL <KeyServer.ConfigRoot>/faxsks/tenants/tenantname]. 詳しくは、 [!DNL configs/faxsks/tenants/sampletenant] サンプルのテナント設定ファイル用のディレクトリ。

テナント設定ファイル内のすべてのファイルパスは、絶対パスまたはテナントの設定ディレクトリを基準とした相対パス ( [!DNL <KeyServer.ConfigRoot>/faxsks/tenants/tenantname]) をクリックします。

すべてのテナント設定ファイルには次が含まれます。

* Key Server Credentials -Adobeが発行する 1 つ以上のキーサーバー資格情報（証明書と秘密鍵）を指定します。 パスとして [!DNL .pfx] ファイルとパスワード、または HSM に保存されている秘密鍵証明書のエイリアス。 ここでは、ファイルパス、キーエイリアス、またはその両方として、このような資格情報を複数指定できます。

The **iOS** テナント設定ファイルには次が含まれます。

* キー配信ウィンドウ — （オプション）キー配信リクエストのタイムスタンプの有効期間（秒単位）を指定します。 デフォルト値は 500 秒です。

The **Xbox 360** テナント設定ファイルには次が含まれます。

* XSTS 秘密鍵証明書 — XSTS トークンの復号化に使用するアプリケーション開発者の秘密鍵証明書を指定します。
* XSTS Signing Certificate - XSTS トークンでの署名の検証に使用する証明書を指定します。
* Packager許可リスト — キーサーバーによって信頼される Packager 証明書。 リストに Packager 証明書が含まれていない場合、すべての Packager 証明書が信頼されます。

## ログファイル {#log-files}

Primetime DRM キーサーバーアプリケーション ( [!DNL flashaccess-ioskeyserver_*.log] および [!DNL flashaccess-xboxkeyserver_*.log]) は、 `KeyServer.LogRoot`.

ログファイルは、クライアントの種類によって区別されます。 クライアントタイプごとに 2 つのログがあります。

* An *アクセスログ*  — リクエストと応答のみを監視します。
* A *コンテキストログ*  — 詳細なエラーメッセージとスタックトレースを含みます。

## キーサーバーの起動 {#starting-the-key-server}

キーサーバーを起動するには、Tomcat を起動します。
