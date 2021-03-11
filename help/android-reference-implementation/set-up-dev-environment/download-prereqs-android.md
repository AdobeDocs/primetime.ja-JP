---
title: 前提条件となるソフトウェアのダウンロードと設定
description: インストールプロセスは簡単です。 システムにJDKが既にインストールされている場合は、この手順をスキップできますが、JDK、Eclipse IDE、OSに互換性が必要であることに注意してください。
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---


# 前提条件のソフトウェア{#download-and-configure-prerequisite-software}をダウンロードして構成する

1. [https://www.oracle.com/technetwork/java/javase/downloads/](https://www.oracle.com/technetwork/java/javase/downloads/)からJDKをダウンロードします。

   インストールプロセスは簡単です。 システムにJDKが既にインストールされている場合は、この手順をスキップできますが、JDK、Eclipse IDE、OSに互換性が必要であることに注意してください。
1. [https://www.eclipse.org/downloads](https://www.eclipse.org/downloads)からEclipse IDE for Java Developersをダウンロードします。

   パッケージを解凍した後、Eclipseを直接実行できます。 インストーラーがありません。
1. [https://developer.android.com/sdk/index.html](https://developer.android.com/sdk/index.html)からAndroid SDK ADT Bundleをダウンロードします。

   このバンドルにはEclipseが含まれます。 既にEclipseがシステムにインストールされている場合は、[!UICONTROL Use An Existing IDE]セクションから、お使いのプラットフォーム用のSDKツールをダウンロードできます。

   アンパックして、記憶する場所にインストールします。 後の手順で参照する必要があります。
1. Android SDKを設定します。
   1. ターミナル（Mac OS Xの場合）またはコマンドプロンプト（Windowsの場合）を開きます。
   1. Android SDKをダウンロードまたは展開したディレクトリに移動します。
   1. [!DNL android]という名前のファイルが含まれているtoolsフォルダーに移動します。
   1. 次のコマンドを実行します。

      * Mac OS X/Unixの場合：

         ```
         chmod +x android 
         android update sdk --no-ui
         ```

      * Windowsの場合：

         ```
         android update sdk --no-ui
         ```

         この処理には時間がかかります。

1. Eclipseを設定します。
   1. 開始Eclipse。

      Windowsで、Eclipseが開始せず、Eclipseが必要なJavaファイルを見つけられないと報告される問題が発生した場合は、次の手順を実行してください。

      * `-vm C:\[path to your JDK bin]\javaw.exe`を[!DNL eclipse.ini]ファイルに追加します。
   1. **[!UICONTROL Help]**/**[!UICONTROL Install New Software]**&#x200B;を選択します。
   1. クリック **[!UICONTROL Add...]**.
   1. 名前に`Android`と入力します。
   1. **[!UICONTROL Work with]**&#x200B;リンクの`https://dl-ssl.google.com/android/eclipse/`と入力します。
   1. クリック **[!UICONTROL OK]**.

      次のようなダイアログが表示されます。

      ![](assets/available_software.jpg)

   1. 表示されるパッケージ（Developer ToolsとNDKプラグインのパッケージ）を選択し、**[!UICONTROL Next]**&#x200B;をクリックします。

      これにより、Android開発ツール(ADT)がダウンロードされます。
   1. ダウンロードが完了したら、Eclipseを再起動します。

   Android SDKがインストールされました。 1. Eclipseを設定して、Android SDKを検索し、それをリソースとして使用できるようにします。
   1. Eclipseを開きます。
   1. Windowsでは&#x200B;**[!UICONTROL Window]** > **[!UICONTROL Preferences]**&#x200B;を選択します。 Mac OS Xでは&#x200B;**[!UICONTROL ADT]** > **[!UICONTROL Preferences]**。
   1. 「**[!UICONTROL Android]**」タブを選択します。
   1. Android SDKの場所を参照します。
   1. クリック **[!UICONTROL Apply]**.

      ![ステップの結果](assets/ss2.jpg)


