---
description: TVSDK Primetime Referenceは、TVSDKとAVEフレームワークに関して構築されたAndroidアプリケーションです。
title: Primetimeリファレンスの実装の構築
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 1%

---


# Primetimeリファレンス実装の構築{#build-the-primetime-reference-implementation}

TVSDK Primetime Referenceは、TVSDKとAVEフレームワークに関して構築されたAndroidアプリケーションです。

EclipseでPrimetime Referenceプロジェクトを設定して構築するには：

1. TVSDK Androidのzipファイルをダウンロードし、記憶しておくべき場所のディレクトリに解凍します。
1. Eclipseを起動します。
1. **[!UICONTROL File]**/**[!UICONTROL Import]**&#x200B;を選択します。
1. **[!UICONTROL Android]**/**[!UICONTROL Existing Android Code Into Workspace]**&#x200B;を選択します。
1. クリック **[!UICONTROL Next]**.
1. **[!UICONTROL Browse]**&#x200B;ボタンを使用して、**[!UICONTROL Root Directory]**&#x200B;フィールドにTVSDK Android zipファイルを展開した[!DNL samples/PrimetimeReference/src]下のディレクトリを設定します。
1. 読み込むプロジェクトを次から選択します。**[!UICONTROL appcompat]**、**[!UICONTROL PrimetimeReference]**。
1. クリック **[!UICONTROL Finish]**.
1. **[!UICONTROL Project]** > **[!UICONTROL Build Project]**&#x200B;を選択して、プロジェクトをビルドします。

   プロジェクトが自動的に構築されるように設定されている場合は、この手順は必要ありません。
1. テストプロジェクトをWorkspaceに含める場合は、テストプロジェクトをPrimetimeReferenceプロジェクトに関連付けます。
   1. 手順3を繰り返します。 ～ 6。
   1. 読み込むプロジェクトを次の中から選択します。`PrimetimeReference\tests`.
   1. クリック **[!UICONTROL Finish]**.

      テストプロジェクトはCatalogActivityプロジェクトに依存しているので、テストプロジェクトをCatalogActivityプロジェクトに関連付ける必要があります。
   1. **[!UICONTROL tests]**&#x200B;を右クリックし、**[!UICONTROL Properties]**&#x200B;を選択します。
   1. 「Java Build Path」の「**[!UICONTROL Projects]**」タブを選択します。
   1. クリック **[!UICONTROL Add...]**
   1. 「CatalogActivity」を選択します。
   1. **[!UICONTROL OK]**&#x200B;をクリックして、プロジェクトを追加します。
   1. **[!UICONTROL OK]**&#x200B;をクリックしてプロパティページを終了します。
   1. **[!UICONTROL Project]** > **[!UICONTROL Build Project]**&#x200B;を選択して、プロジェクトをビルドします。

      プロジェクトが自動的に構築されるように設定されている場合は、この手順は必要ありません。
