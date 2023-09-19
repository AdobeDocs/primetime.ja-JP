---
title: 前提条件のソフトウェアをダウンロードして構成
description: インストールプロセスは簡単です。 既に JDK をシステムにインストールしている場合は、この手順をスキップできますが、JDK、Eclipse IDE、OS に互換性が必要です。
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# 前提条件のソフトウェアをダウンロードして構成 {#download-and-configure-prerequisite-software}

1. からの JDK のダウンロード [https://www.oracle.com/technetwork/java/javase/downloads/](https://www.oracle.com/technetwork/java/javase/downloads/).

   インストールプロセスは簡単です。 既に JDK をシステムにインストールしている場合は、この手順をスキップできますが、JDK、Eclipse IDE、OS に互換性が必要です。
1. Eclipse IDE for Java Developers のダウンロード先： [https://www.eclipse.org/downloads](https://www.eclipse.org/downloads).

   パッケージを解凍した後、Eclipse を直接実行できます。 インストーラーがありません。
1. Android SDK ADT Bundle のダウンロード先： [https://developer.android.com/sdk/index.html](https://developer.android.com/sdk/index.html).

   このバンドルには Eclipse が含まれます。 既にシステムに Eclipse がインストールされている場合は、使用しているプラットフォーム用の SDK ツールを、 [!UICONTROL Use An Existing IDE] 」セクションに入力します。

   記憶する場所に展開してインストールします。 後の手順でこれを参照する必要があります。
1. Android SDK を設定します。
   1. ターミナル (Mac OS X の場合 ) またはコマンドプロンプト（Windows の場合）を開きます。
   1. Android SDK をダウンロードまたは展開したディレクトリに移動します。
   1. という名前のファイルを含むツールフォルダに移動します。 [!DNL android].
   1. 次のコマンドを実行します。

      * Mac OS X/Unix の場合：

        ```
        chmod +x android 
        android update sdk --no-ui
        ```

      * Windows の場合：

        ```
        android update sdk --no-ui
        ```

        この処理には時間がかかります。

1. Eclipse を設定します。
   1. Eclipse を起動します。

      Windows で、Eclipse が起動せず、報告された問題が Eclipse が必要な Java ファイルを見つけられない場合は、次の操作を試します。

      * 追加 `-vm C:\[path to your JDK bin]\javaw.exe` を [!DNL eclipse.ini] ファイル。
   1. 選択  **[!UICONTROL Help]** > **[!UICONTROL Install New Software]** .
   1. クリック **[!UICONTROL Add...]**.
   1. 入力 `Android` の名前。
   1. 入力 `https://dl-ssl.google.com/android/eclipse/` （の） **[!UICONTROL Work with]** リンク。
   1. クリック **[!UICONTROL OK]**.

      次のようなダイアログが表示されます。

      ![](assets/available_software.jpg)

   1. 生成されたパッケージ（開発者ツールと NDK プラグインのパッケージ）を選択し、 **[!UICONTROL Next]**.

      Android 開発ツール (ADT) がダウンロードされます。
   1. ダウンロードが完了したら、Eclipse を再起動します。

   これで、Android SDK がインストールされました。 1. Eclipse を設定して、Android SDK を検索し、リソースとして使用できるようにします。
   1. Eclipse を開きます。
   1. 選択  **[!UICONTROL Window]** > **[!UICONTROL Preferences]** （Windows の場合）  **[!UICONTROL ADT]** > **[!UICONTROL Preferences]** (Mac OS X 上 )
   1. を選択します。 **[!UICONTROL Android]** タブをクリックします。
   1. Android SDK の場所を参照します。
   1. クリック **[!UICONTROL Apply]**.

      ![手順の結果](assets/ss2.jpg)
