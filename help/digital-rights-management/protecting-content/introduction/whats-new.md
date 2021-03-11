---
description: Adobe PrimetimeDRMは、高価値の視聴覚コンテンツを実現する高度なDigital Rights Management(DRM)およびコンテンツ保護ソリューションです。 Java APIの作成をサポートするアプリケーションでは、Primetime DRM SDKを使用してDRMポリシーを指定し、それらのポリシーをコンテンツに適用し、そのコンテンツを暗号化できます。
title: Adobe PrimetimeDRMの新機能
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---


# Adobe PrimetimeDRM{#what-is-new-in-adobe-primetime-drm}の新機能

Adobe PrimetimeDRMは、高価値の視聴覚コンテンツを実現する高度なDigital Rights Management(DRM)およびコンテンツ保護ソリューションです。 Java APIの作成をサポートするアプリケーションでは、Primetime DRM SDKを使用してDRMポリシーを指定し、それらのポリシーをコンテンツに適用し、そのコンテンツを暗号化できます。

>[!NOTE]
>
>Primetime DRMは、以前はAdobeアクセスと呼ばれていましたが、これ以前はFlash Accessと呼ばれていました。

コンテンツ保護プロセスの概要を次に示します。

1. DRM Java APIを使用して、DRMポリシーのプロパティと暗号化パラメーターを設定します。
1. 任意のコンテンツの使用上の役割を説明するDRMポリシーを作成します。

   DRMポリシーはいくつでも作成できます。 ほとんどのユーザーは、少数のポリシーを作成し、多数のファイルに適用します。
1. メディアファイルをパッケージ化します。

   *`Packaging a file`* は、ファイルを暗号化し、DRMポリシーをファイルに適用することを意味します。
1. ライセンスサーバーを実装して、ユーザーにライセンスを発行します。

これらの手順が完了すると、暗号化されたコンテンツの展開準備が整います。 展開後、クライアントはライセンスサーバーにライセンスを要求し、要求を受けるとコンテンツを再生できます。

Primetime DRM SDKは、これらのタスクを完了するJava APIを提供します。 SDKには、ライセンスサーバーとコマンドラインツールのリファレンス実装が含まれており、どちらもDRM SDK Java APIに基づいています。

以下に説明する機能は、このリリースの新機能です。

## 新機能{#section_F6BA874CEAE24610920BC3A4C6D20EBA}

* **ハードストップ —** 再生ウィンドウの最後で再生を停止するか、続行するかを指定できます。
* **解像度に依存する出力コントロール —** ピクセル解像度に基づいて出力制約を指定できます。
* **ライセンスサーバー応答の匿名化 — Primetime DRMライセンスサーバープロトコル** のプライバシーを強化するために、サポートクライアントに対するライセンスサーバー応答の場合は、トランスポート証明書のシリアル番号がゼロになります。

