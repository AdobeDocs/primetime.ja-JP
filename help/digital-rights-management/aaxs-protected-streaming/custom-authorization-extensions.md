---
seo-title: カスタム認証拡張
title: カスタム認証拡張
description: ライセンスの取得中にカスタム認証ロジックを呼び出して、要求元のクライアントにライセンスを発行する必要があるかどうかを判断できます。
seo-description: ライセンスの取得中にカスタム認証ロジックを呼び出して、要求元のクライアントにライセンスを発行する必要があるかどうかを判断できます。
uuid: fb40db6f-30aa-46e3-9eeb-faff3cfedab1
translation-type: tm+mt
source-git-commit: fe9493d610bc6fb97d30351c707b73cda92c67a0

---


# カスタム認証拡張 {#custom-authorization-extensions}

ライセンスの取得中にカスタム認証ロジックを呼び出して、要求元のクライアントにライセンスを発行する必要があるかどうかを判断できます。

独自の顧客認証拡張を実装するには、まずsamplesディレクトリにあるサンプルコードを確認します(このサンプルのコンパイルバージョンは、 [!DNL SampleAuthorizer.java] flashaccess-license-server-ext-sample.jarにあります)。

独自の拡張機能を構築するには、インターフェイスを実装 `com.adobe.flashaccess.server.license.extension.auth.IAuthorizer` し、で特定のフィールドを使用する場合は、インターフェイスがビルドパス上にあり、ビルドパス上にあ `flashaccess-license-server-exts.jar` ることを確認する必要があり `commons-logging.jar``adobe-flashaccess-sdk.jar``IMessageFacade`ます)。 拡張機能をデプロイするには、jarまたはクラスファイルを *LicenseServer.ConfigRootにコピーします*`/flashaccessserver/libs`。 jarまたはクラスファイルを更新する必要がある場合は、更新したバージョンを使用する前にサーバーを再起動する必要があります。 また、承認者のクラス名をテナント構成ファイルに追加する必要があります。
