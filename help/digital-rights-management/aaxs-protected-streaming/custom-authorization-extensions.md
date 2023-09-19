---
title: カスタム認証拡張機能
description: カスタム認証ロジックは、ライセンスの取得中に呼び出して、要求元のクライアントに対してライセンスを発行するかどうかを決定できます。
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# カスタム認証拡張機能 {#custom-authorization-extensions}

カスタム認証ロジックは、ライセンスの取得中に呼び出して、要求元のクライアントに対してライセンスを発行するかどうかを決定できます。

独自の顧客認証拡張機能を実装するには、まず [!DNL SampleAuthorizer.java] サンプルコードは samples ディレクトリにあります（このサンプルのコンパイル版は flashaccess-license-server-ext-sample.jar にあります）。

独自の拡張機能を構築するには、 `com.adobe.flashaccess.server.license.extension.auth.IAuthorizer` インターフェイスを使用し、 `flashaccess-license-server-exts.jar` および `commons-logging.jar` はビルドパス上にあります `adobe-flashaccess-sdk.jar` また、 `IMessageFacade`) をクリックします。 拡張機能をデプロイするには、jar またはクラスファイルを次の場所にコピーします。 *LicenseServer.ConfigRoot* `/flashaccessserver/libs`. jar またはクラスファイルを更新する必要がある場合は、更新されたバージョンを使用する前にサーバーを再起動する必要があります。 また、オーサライザークラス名をテナント設定ファイルに追加する必要があります。
