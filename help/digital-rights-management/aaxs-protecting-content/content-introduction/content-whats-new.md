---
description: 'Adobe® Access™は、高価値のオーディオビジュアルコンテンツを実現する高度なデジタル著作権管理およびコンテンツ保護ソリューションです。 Java APIを使用して作成したツールを使用して、ポリシーを作成し、オーディオおよびビデオコンテンツを含むファイルにポリシーを適用し、それらのファイルを暗号化できます。 これらのタスクを実行するための高レベルの手順は次のとおりです。 '
seo-description: 'Adobe® Access™は、高価値のオーディオビジュアルコンテンツを実現する高度なデジタル著作権管理およびコンテンツ保護ソリューションです。 Java APIを使用して作成したツールを使用して、ポリシーを作成し、オーディオおよびビデオコンテンツを含むファイルにポリシーを適用し、それらのファイルを暗号化できます。 これらのタスクを実行するための高レベルの手順は次のとおりです。 '
seo-title: 概要
title: 概要
uuid: 874c175b-8207-49fa-aad4-204ccbee9c2c
translation-type: tm+mt
source-git-commit: 58bb3bedc5b0ac63afd96eb6101d9ad779e6deed
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---


# 概要 {#overview}

Adobe® Access™は、高価値のオーディオビジュアルコンテンツを実現する高度なデジタル著作権管理およびコンテンツ保護ソリューションです。 Java APIを使用して作成したツールを使用して、ポリシーを作成し、オーディオおよびビデオコンテンツを含むファイルにポリシーを適用し、それらのファイルを暗号化できます。 これらのタスクを実行するための高レベルの手順を次に示します。

1. Java APIを使用して、ポリシーのプロパティと暗号化パラメーターを設定します。
1. コンテンツの使用上の役割を説明するポリシーを作成します。 (ポリシーの [操作を参照](../../aaxs-protecting-content/content-working-with-policies/content-working-with-policies-overview.md))。

   ポリシーはいくつでも作成できます。 ほとんどのユーザーは、少数のポリシーを作成し、多数のファイルに適用します。

1. メディアファイルをパッケージ化します。

   このコンテキストでは、ファイルを *パッケージ化すると* 、ファイルが暗号化され、ポリシーが適用されます。 (メディアファイルの [パッケージ化を参照](../../aaxs-protecting-content/content-packaging-media-files/content-packaging-media-files-overview.md))。

1. ライセンスサーバーを実装して、ユーザーにライセンスを発行します。

これで、暗号化されたコンテンツの展開準備が整い、クライアントはサーバーからライセンスを要求できます。

SDKは、これらのタスクを達成するJava APIを提供し、ライセンスサーバーの参照実装、およびJava APIに基づくコマンドラインツールを含みます。 詳しくは、『Adobe Access Reference Implementations *の使用*』を参照してください。

## Adobe Access 5.2の新機能 {#section_06220EDE36B54DCB9CA7963B76DA8167}

* **外部CEK**: CEKを暗号化してコンテンツのメタデータにバンドルする代わりに、Content Key Management System(CKMS)をDRMライセンスサービングおよびコンテンツパッケージングワークフローに統合する機能。 「 [Adobe Access DRM External CEKの概要](../../aaxs-drm-xkey-mgmt/aaxs-drm-using-external-cek-overview.md)」を参照してください。

* **ライセンス（バウチャー）返却**: クライアントがクライアントに発行したライセンスを返却（または削除）する機能。
* **Xboxキーサーバー**: XboxとXbox 360に送信されるコンテンツを保護する機能。 （Adobe Primetimeクライアントが必要です）。

## カスタム使用ルール {#custom-usage-rules}

カスタム使用ルールを指定します。 カスタムデータは、License Serverが発行するライセンスに含めることができます。 このデータの解釈/処理は、クライアントアプリケーションとライセンスサーバーの実装に完全に依存します。

使用例： 使用ルールの拡張機能を有効にします。そのため、他のビジネスルールをポリシーおよび/またはコンテンツのライセンスの一部として安全に伝達できます。 セキュリティ上の理由から、これらの使用ルールはカスタムクライアントアプリケーションコードで適用されるので、この許可リストは、AIRアプリケーションまたはFlash Player SWFアプリケーションオプションと組み合わせて使用する必要があります。 詳しくは、「 [ランタイムとアプリケーションの制限](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-runtime-application-restrictions/content-allowlist-air.md)」を参照してください。
