---
description: ライセンスの取得中にカスタム認証ロジックを呼び出して、要求元のクライアントにライセンスを発行する必要があるかどうかを判断できます。
seo-description: ライセンスの取得中にカスタム認証ロジックを呼び出して、要求元のクライアントにライセンスを発行する必要があるかどうかを判断できます。
seo-title: カスタム認証拡張
title: カスタム認証拡張
uuid: 588b05e5-3402-4586-bbd4-58b7e9a58ee4
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# カスタム認証拡張{#custom-authorization-extensions}

ライセンスの取得中にカスタム認証ロジックを呼び出して、要求元のクライアントにライセンスを発行する必要があるかどうかを判断できます。

独自の顧客認証拡張を実装する場合は、まずsamplesディレクトリにあるサンプルコ [!DNL SampleAuthorizer.java] ードを確認する必要があります。 このサンプルのコンパイルバージョンは、にありま [!DNL flashaccess-license-server-ext-sample.jar]す。

独自の拡張機能を構築する場合は、インターフェイスを実装し、とがビルドパスに含まれていることを確認する必要があります(で特定のフィールドを使用する場合は、ビルドパ `com.adobe.flashaccess.server.license.extension.auth.IAuthorizer` スにも含まれている必要があり [!DNL flashaccess-license-server-exts.jar][!DNL commons-logging.jar][!DNL adobe-flashaccess-sdk.jar]`IMessageFacade`ます)。

拡張機能をデプロイする場合は、jarまたはクラスファイルを *LicenseServer.ConfigRootにコピーする必要があります*[!DNL /flashaccessserver/libs]。

jarファイルまたはクラスファイルを更新する場合は、更新したバージョンを使用する前に、サーバーを再起動する必要があります。 また、承認者のクラス名をテナント構成ファイルに追加する必要があります。
