---
description: ライセンスの取得中にカスタム認証ロジックを呼び出して、要求元のクライアントにライセンスを発行する必要があるかどうかを判断できます。
title: カスタム認証拡張
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---


# カスタム認証拡張{#custom-authorization-extensions}

ライセンスの取得中にカスタム認証ロジックを呼び出して、要求元のクライアントにライセンスを発行する必要があるかどうかを判断できます。

独自の顧客認証拡張機能を実装する場合は、まずsamplesディレクトリにある[!DNL SampleAuthorizer.java]サンプルコードを調べる必要があります。 このサンプルのコンパイル版は[!DNL flashaccess-license-server-ext-sample.jar]にあります。

独自の拡張機能を構築する場合は、`com.adobe.flashaccess.server.license.extension.auth.IAuthorizer`インターフェイスを実装し、[!DNL flashaccess-license-server-exts.jar]と[!DNL commons-logging.jar]がビルドパスにあることを確認する必要があります（`IMessageFacade`で特定のフィールドを使用する場合は、[!DNL adobe-flashaccess-sdk.jar]もビルドパスに含める必要があります）。

拡張機能をデプロイする場合は、jarファイルまたはクラスファイルを&#x200B;*LicenseServer.ConfigRoot* [!DNL /flashaccessserver/libs]にコピーする必要があります。

jarファイルまたはクラスファイルを更新する場合は、更新されたバージョンを使用する前に、サーバーを再起動する必要があります。 また、承認者クラス名をテナント構成ファイルに追加する必要があります。
