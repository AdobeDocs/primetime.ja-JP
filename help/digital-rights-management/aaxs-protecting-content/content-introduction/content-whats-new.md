---
description: 'Adobe® Access™は、高価値のオーディオビジュアルコンテンツを実現する高度なデジタル著作権管理およびコンテンツ保護ソリューションです。 Java APIを使用して作成したツールを使用して、ポリシーを作成し、オーディオおよびビデオコンテンツを含むファイルにポリシーを適用し、それらのファイルを暗号化できます。 これらのタスクを実行するための高レベルの手順は次のとおりです。 '
title: 概要
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---


# 概要{#overview}

Adobe® Access™は、高価値のオーディオビジュアルコンテンツを実現する高度なデジタル著作権管理およびコンテンツ保護ソリューションです。 Java APIを使用して作成したツールを使用して、ポリシーを作成し、オーディオおよびビデオコンテンツを含むファイルにポリシーを適用し、それらのファイルを暗号化できます。 これらのタスクを実行するための高レベルの手順を次に示します。

1. Java APIを使用して、ポリシーのプロパティと暗号化パラメーターを設定します。
1. コンテンツの使用上の役割を説明するポリシーを作成します。 （[ポリシーの操作](../../aaxs-protecting-content/content-working-with-policies/content-working-with-policies-overview.md)を参照）。

   ポリシーはいくつでも作成できます。 ほとんどのユーザーは、少数のポリシーを作成し、多数のファイルに適用します。

1. メディアファイルをパッケージ化します。

   このコンテキストでは、*ファイル*&#x200B;をパッケージ化すると、ファイルを暗号化し、それにポリシーを適用します。 （[メディアファイルのパッケージ化](../../aaxs-protecting-content/content-packaging-media-files/content-packaging-media-files-overview.md)を参照）。

1. ライセンスサーバーを実装して、ユーザーにライセンスを発行します。

これで、暗号化されたコンテンツの展開準備が整い、クライアントはサーバーからライセンスを要求できます。

SDKは、これらのタスクを達成するJava APIを提供し、ライセンスサーバーの参照実装、およびJava APIに基づくコマンドラインツールを含みます。 詳しくは、*Adobeアクセスリファレンス実装の使用*&#x200B;を参照してください。

## Adobeアクセス5.2の新機能{#section_06220EDE36B54DCB9CA7963B76DA8167}

* **外部CEK**:CEKを暗号化してコンテンツのメタデータにバンドルする代わりに、Content Key Management System(CKMS)をDRMライセンスサービングおよびコンテンツパッケージングワークフローに統合する機能。「[AdobeアクセスDRM外部CEKの概要](../../aaxs-drm-xkey-mgmt/aaxs-drm-using-external-cek-overview.md)」を参照してください。

* **ライセンス（バウチャー）返却**:クライアントがクライアントに発行したライセンスを返却（または削除）する機能。
* **Xboxキーサーバー**:XboxとXbox 360に送信されるコンテンツを保護する機能。(Adobe Primetimeのお客様が必要です。)

## カスタム使用ルール{#custom-usage-rules}

カスタム使用ルールを指定します。 カスタムデータは、License Serverが発行するライセンスに含めることができます。 このデータの解釈/処理は、クライアントアプリケーションとライセンスサーバーの実装に完全に依存します。

使用例：使用ルールの拡張機能を有効にします。そのため、他のビジネスルールをポリシーおよび/またはコンテンツのライセンスの一部として安全に伝達できます。 セキュリティ上の理由から、これらの使用ルールはカスタムクライアントアプリケーションコードで適用されるので、このオプションは、AIRアプリケーションまたはFlash PlayerSWF許可リストオプションと組み合わせて使用する必要があります。 詳しくは、[ランタイムとアプリケーションの制限](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-runtime-application-restrictions/content-allowlist-air.md)を参照してください。
