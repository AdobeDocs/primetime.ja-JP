---
description: TVSDK Primetime Referenceは、TVSDKおよびAVEフレームワークに関して構築されたAndroidアプリケーションです。
seo-description: TVSDK Primetime Referenceは、TVSDKおよびAVEフレームワークに関して構築されたAndroidアプリケーションです。
seo-title: Primetimeリファレンスの実装の構築
title: Primetimeリファレンスの実装の構築
uuid: ab12660a-1563-49a4-82d9-1ab13f8a92be
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Primetimeリファレンスの実装の構築 {#build-the-primetime-reference-implementation}

TVSDK Primetime Referenceは、TVSDKおよびAVEフレームワークに関して構築されたAndroidアプリケーションです。

EclipseでPrimetime Referenceプロジェクトを設定して構築するには：

1. TVSDK Androidのzipファイルをダウンロードし、記憶しておく場所のディレクトリに解凍します。
1. Eclipseを起動します。
1. /を選 **[!UICONTROL File]** 択しま **[!UICONTROL Import]**&#x200B;す。
1. /を選 **[!UICONTROL Android]** 択しま **[!UICONTROL Existing Android Code Into Workspace]**&#x200B;す。
1. クリック **[!UICONTROL Next]**.
1. このボタン **[!UICONTROL Browse]** を使用して、TVSDK Android zipフ **[!UICONTROL Root Directory]** ァイルの展開先とな [!DNL samples/PrimetimeReference/src] るディレクトリをフィールドに入力します。
1. 読み込む次のプロジェクトを選択します。 **[!UICONTROL appcompat]**、 **[!UICONTROL PrimetimeReference]**
1. クリック **[!UICONTROL Finish]**.
1. /を選 **[!UICONTROL Project]** 択して、 **[!UICONTROL Build Project]** プロジェクトを構築します。

   この手順は、プロジェクトが自動的に構築されるように設定されている場合は必要ありません。
1. テストプロジェクトをワークスペースに含める場合は、テストプロジェクトをPrimetimeReferenceプロジェクトに関連付けます。
   1. 手順3を繰り返します。 ～ 6
   1. 読み込む次のプロジェクトを選択します。 `PrimetimeReference\tests`.
   1. クリック **[!UICONTROL Finish]**.

      テストプロジェクトはCatalogActivityプロジェクトに依存しているので、テストプロジェクトをCatalogActivityプロジェクトに関連付ける必要があります。
   1. 右クリックし、を **[!UICONTROL tests]** 選択しま **[!UICONTROL Properties]**&#x200B;す。
   1. 「Java Build Path」 **[!UICONTROL Projects]** の下のタブを選択します。
   1. クリック **[!UICONTROL Add...]**
   1. 「CatalogActivity」を選択します。
   1. をクリック **[!UICONTROL OK]** して、プロジェクトを追加します。
   1. をクリック **[!UICONTROL OK]** して、プロパティページを終了します。
   1. /を選 **[!UICONTROL Project]** 択して、 **[!UICONTROL Build Project]** プロジェクトを構築します。

      この手順は、プロジェクトが自動的に構築されるように設定されている場合は必要ありません。
