---
description: 'Adobe® Access™は、高価値のオーディオビジュアルコンテンツを実現する高度なデジタル著作権管理およびコンテンツ保護ソリューションです。 Java APIを使用して作成したツールを使用して、ポリシーを作成し、オーディオおよびビデオコンテンツを含むファイルにポリシーを適用し、それらのファイルを暗号化できます。 これらのタスクを実行するための高度な手順は、次のとおりです。 '
seo-description: 'Adobe® Access™は、高価値のオーディオビジュアルコンテンツを実現する高度なデジタル著作権管理およびコンテンツ保護ソリューションです。 Java APIを使用して作成したツールを使用して、ポリシーを作成し、オーディオおよびビデオコンテンツを含むファイルにポリシーを適用し、それらのファイルを暗号化できます。 これらのタスクを実行するための高度な手順は、次のとおりです。 '
seo-title: 概要
title: 概要
uuid: 874c175b-8207-49fa-aad4-204ccbee9c2c
translation-type: tm+mt
source-git-commit: 53654b740b03c6a79394d30704a41186d4655237

---


# 概要 {#overview}

Adobe® Access™は、高価値のオーディオビジュアルコンテンツを実現する高度なデジタル著作権管理およびコンテンツ保護ソリューションです。 Java APIを使用して作成したツールを使用して、ポリシーを作成し、オーディオおよびビデオコンテンツを含むファイルにポリシーを適用し、それらのファイルを暗号化できます。 これらのタスクを実行するための高度な手順は、次のとおりです。

1. Java APIを使用して、ポリシーのプロパティと暗号化パラメーターを設定します。
1. コンテンツの使用上の役割を説明するポリシーを作成します。 (ポリシー [の操作を参照](../../aaxs-protecting-content/content-working-with-policies/content-working-with-policies-overview.md))。

   ポリシーはいくつでも作成できます。 ほとんどのユーザーは、少数のポリシーを作成し、多数のファイルに適用します。

1. メディアファイルのパッケージ化

   この場合、ファイルのパッ *ケージ化とは* 、ファイルを暗号化し、ポリシーを適用することを意味します。 (メディアフ [ァイルのパッケージ化](../../aaxs-protecting-content/content-packaging-media-files/content-packaging-media-files-overview.md)を参照)。

1. ライセンスサーバーを実装して、ユーザーにライセンスを発行します。

これで、暗号化されたコンテンツを展開する準備が整い、クライアントはサーバーにライセンスを要求できます。

SDKは、これらのタスクを実行するJava APIを提供し、ライセンスサーバーの参照実装、およびJava APIに基づくコマンドラインツールを含みます。 詳しくは、『Adobe Access Reference Implementations *の使用』を参照してください*。

## Adobe Access 5.2の新機能 {#section_06220EDE36B54DCB9CA7963B76DA8167}

* **外部CEK**:CKMS(Content Key Management System)を、CEKを暗号化してコンテンツのメタデータにバンドルする代わりに、DRMライセンスサービングおよびコンテンツパッケージ化ワークフローに統合する機能。 詳しくは、 [Adobe Access DRM External CEKの概要を参照してください](../../aaxs-drm-xkey-mgmt/aaxs-drm-using-external-cek-overview.md)。

* **ライセンス（バウチャー）返却**:クライアントがクライアントに発行されたライセンスを返す（または削除する）機能。
* **Xboxキーサーバ**:XboxおよびXbox 360に送信されるコンテンツを保護する機能。 （Adobe Primetimeクライアントが必要です）。

## カスタム使用ルール {#custom-usage-rules}

カスタムの使用ルールを指定します。 カスタムデータは、License Serverが発行するライセンスに含めることができます。 このデータの解釈/処理は、クライアントアプリケーションとライセンスサーバの実装に完全に依存します。

使用例：ポリシーやコンテンツのライセンスの一部として他のビジネスルールを安全に伝達できるようにすることで、使用ルールの拡張を有効にします。 セキュリティ上の理由から、これらの使用ルールはカスタムクライアントアプリケーションコードで適用されるので、このオプションはAIRアプリケーションまたはFlash Player SWFホワイトリストオプションと組み合わせて使用する必要があります。 詳しくは、「ランタイムとアプリケ[ーションの制限](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-runtime-application-restrictions/content-whitelist-air.md)」を参照してください。