---
description: Adobe Primetime DRM は、高価値の視聴コンテンツを実現する高度なDigital Rights Management(DRM) およびコンテンツ保護ソリューションです。 Java API の作成をサポートするアプリケーションでは、Primetime DRM SDK を使用して DRM ポリシーを指定し、それらのポリシーをコンテンツに適用し、そのコンテンツを暗号化することができます。
title: Adobe Primetime DRM の新機能
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# Adobe Primetime DRM の新機能{#what-is-new-in-adobe-primetime-drm}

Adobe Primetime DRM は、高価値の視聴コンテンツを実現する高度なDigital Rights Management(DRM) およびコンテンツ保護ソリューションです。 Java API の作成をサポートするアプリケーションでは、Primetime DRM SDK を使用して DRM ポリシーを指定し、それらのポリシーをコンテンツに適用し、そのコンテンツを暗号化することができます。

>[!NOTE]
>
>Primetime DRM は、以前はAdobeアクセスと呼ばれていましたが、それ以前はFlash Accessでした。

コンテンツ保護プロセスの概要を次に示します。

1. DRM Java API を使用して、DRM ポリシーのプロパティと暗号化パラメーターを設定します。
1. コンテンツの使用上の役割を記述した DRM ポリシーを作成します。

   任意の数の DRM ポリシーを作成できます。 ほとんどのユーザーは、少数のポリシーを作成し、多数のファイルに適用します。
1. メディアファイルをパッケージ化します。

   *`Packaging a file`* は、ファイルを暗号化し、そのファイルに DRM ポリシーを適用することを意味します。
1. ライセンスをユーザーに発行するには、ライセンスサーバーを実装します。

これらの手順が完了すると、暗号化されたコンテンツのデプロイメント準備が整います。 デプロイメント後、クライアントはライセンスサーバーにライセンスを要求し、受け取ったらコンテンツを再生できます。

Primetime DRM SDK は、これらのタスクを完了するための Java API を提供します。 SDK には、ライセンスサーバーとコマンドラインツールの参照実装が含まれています。両方とも、DRM SDK Java API に基づいています。

以下に説明する機能は、このリリースの新機能です。

## 新機能 {#section_F6BA874CEAE24610920BC3A4C6D20EBA}

* **ハードストップ —** 再生を停止するか、再生ウィンドウの最後に続くかを指定できます。
* **解像度に依存する出力制御 —** ピクセル解像度に基づいて出力制約を指定できます。
* **ライセンスサーバ応答の匿名化 —** Primetime DRM ライセンスサーバープロトコルでプライバシーを強化するために、サポートクライアントに対するライセンスサーバー応答用に、トランスポート証明書のシリアル番号がゼロになります。
