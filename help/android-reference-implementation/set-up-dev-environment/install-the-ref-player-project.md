---
description: TVSDK Primetime Reference は、 TVSDK および AVE フレームワークに基づいて構築された Android アプリケーションです。
title: Primetime リファレンス実装の構築
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 0%

---

# Primetime リファレンス実装の構築 {#build-the-primetime-reference-implementation}

TVSDK Primetime Reference は、 TVSDK および AVE フレームワークに基づいて構築された Android アプリケーションです。

Eclipse で Primetime Reference プロジェクトを設定して構築するには、次の手順を実行します。

1. TVSDK Android zip ファイルをダウンロードし、覚えておく場所のディレクトリに解凍します。
1. Eclipse を起動します。
1. 選択 **[!UICONTROL File]** > **[!UICONTROL Import]**.
1. 選択 **[!UICONTROL Android]** > **[!UICONTROL Existing Android Code Into Workspace]**.
1. クリック **[!UICONTROL Next]**.
1. 以下を使用します。 **[!UICONTROL Browse]** ボタンを使用して **[!UICONTROL Root Directory]** の下のディレクトリを含むフィールド [!DNL samples/PrimetimeReference/src] TVSDK Android zip ファイルを展開します。
1. 読み込むプロジェクトを次の中から選択します。 **[!UICONTROL appcompat]**, **[!UICONTROL PrimetimeReference]**.
1. クリック **[!UICONTROL Finish]**.
1. 選択  **[!UICONTROL Project]** > **[!UICONTROL Build Project]** をクリックして、プロジェクトを構築します。

   プロジェクトが自動的にビルドするように設定されている場合、この手順は必要ありません。
1. テストプロジェクトをワークスペースに含める場合は、テストプロジェクトを PrimetimeReference プロジェクトに関連付けます。
   1. 手順 3 を繰り返します。 6.
   1. 読み込むプロジェクトを次の中から選択します。 `PrimetimeReference\tests`.
   1. クリック **[!UICONTROL Finish]**.

      テストプロジェクトは CatalogActivity プロジェクトに依存するので、テストプロジェクトを CatalogActivity プロジェクトに関連付ける必要があります。
   1. 右クリック **[!UICONTROL tests]** を選択します。 **[!UICONTROL Properties]**.
   1. を選択します。 **[!UICONTROL Projects]** 」タブをクリックします。
   1. クリック **[!UICONTROL Add...]**
   1. 「CatalogActivity」を選択します。
   1. クリック **[!UICONTROL OK]** をクリックして、プロジェクトを追加します。
   1. クリック **[!UICONTROL OK]** をクリックして、プロパティページを終了します。
   1. 選択  **[!UICONTROL Project]** > **[!UICONTROL Build Project]** をクリックして、プロジェクトを構築します。

      プロジェクトが自動的にビルドするように設定されている場合、この手順は必要ありません。
