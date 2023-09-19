---
description: ライセンスの取得中にカスタム認証ロジックを呼び出して、要求元のクライアントにライセンスを発行するかどうかを決定できます。
title: カスタム認証拡張機能
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---

# カスタム認証拡張機能{#custom-authorization-extensions}

ライセンスの取得中にカスタム認証ロジックを呼び出して、要求元のクライアントにライセンスを発行するかどうかを決定できます。

独自の顧客認証拡張機能を実装する場合は、まず [!DNL SampleAuthorizer.java] samples ディレクトリにあるサンプルコード。 このサンプルのコンパイル版は、 [!DNL flashaccess-license-server-ext-sample.jar].

独自の拡張機能を構築する場合は、 `com.adobe.flashaccess.server.license.extension.auth.IAuthorizer` インターフェイスを使用し、 [!DNL flashaccess-license-server-exts.jar] および [!DNL commons-logging.jar] はビルドパス ( [!DNL adobe-flashaccess-sdk.jar] また、 `IMessageFacade`) をクリックします。

拡張機能をデプロイする場合は、jar またはクラスファイルを次の場所にコピーする必要があります。 *LicenseServer.ConfigRoot* [!DNL /flashaccessserver/libs].

jar ファイルまたはクラスファイルを更新する場合は、更新されたバージョンを使用する前に、サーバーを再起動する必要があります。 また、オーサライザークラス名をテナント設定ファイルに追加する必要があります。
