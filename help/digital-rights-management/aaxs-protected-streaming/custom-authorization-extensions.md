---
title: カスタム認証拡張
description: ライセンスの取得中にカスタム認証ロジックを呼び出して、要求元のクライアントにライセンスを発行するかどうかを決定できます。
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---


# カスタム認証拡張{#custom-authorization-extensions}

ライセンスの取得中にカスタム認証ロジックを呼び出して、要求元のクライアントにライセンスを発行するかどうかを決定できます。

独自の顧客認証拡張機能を実装するには、まずsamplesディレクトリにある[!DNL SampleAuthorizer.java]サンプルコードを調べます（このサンプルのコンパイルバージョンは、flashaccess-license-server-ext-sample.jarにあります）。

独自の拡張機能を構築するには、`com.adobe.flashaccess.server.license.extension.auth.IAuthorizer`インターフェイスを実装し、`IMessageFacade`で特定のフィールドを利用する場合は、`flashaccess-license-server-exts.jar`と`commons-logging.jar`がビルドパス`adobe-flashaccess-sdk.jar`にある必要があることを確認します。 拡張機能をデプロイするには、jarファイルまたはクラスファイルを&#x200B;*LicenseServer.ConfigRoot* `/flashaccessserver/libs`にコピーします。 jarファイルまたはクラスファイルを更新する必要がある場合は、更新したバージョンを使用する前にサーバーを再起動する必要があります。 また、承認者クラス名をテナント構成ファイルに追加する必要があります。
