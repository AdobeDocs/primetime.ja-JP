---
seo-title: 前提条件ソフトウェアのダウンロードと設定
title: 前提条件ソフトウェアのダウンロードと設定
description: インストールは簡単です。 システムにJDKが既にインストールされている場合は、この手順をスキップできますが、JDK、Eclipse IDE、OSに互換性が必要であることに注意してください。
seo-description: インストールは簡単です。 システムにJDKが既にインストールされている場合は、この手順をスキップできますが、JDK、Eclipse IDE、OSに互換性が必要であることに注意してください。
uuid: ca29144f-8088-4c8d-93cf-aa59007da034
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# 前提条件ソフトウェアのダウンロードと設定 {#download-and-configure-prerequisite-software}

1. https://www.oracle.com/technetwork/java/javase/downloads/からJDKをダウンロード [します](https://www.oracle.com/technetwork/java/javase/downloads/)。

   インストールは簡単です。 システムにJDKが既にインストールされている場合は、この手順をスキップできますが、JDK、Eclipse IDE、OSに互換性が必要であることに注意してください。
1. https://www.eclipse.org/downloadsからEclipse IDE for Java Developersをダウンロードし [ます](https://www.eclipse.org/downloads)。

   パッケージの解凍後、Eclipseを直接実行できます。 インストーラーがありません。
1. https://developer.android.com/sdk/index.htmlからAndroid SDK ADT Bundleをダウンロードし [ます](https://developer.android.com/sdk/index.html)。

   このバンドルにはEclipseが含まれます。 システムに既にEclipseがインストールされている場合は、このセクションから、使用しているプラットフォーム用のSDKツールをダウンロードで [!UICONTROL Use An Existing IDE] きます。

   アンパックし、記憶しておく場所にインストールします。 後の手順で参照する必要があります。
1. Android SDKを設定します。
   1. ターミナル（Mac OS Xの場合）またはコマンドプロンプト（Windowsの場合）を開きます。
   1. Android SDKをダウンロードまたは展開したディレクトリに移動します。
   1. toolsフォルダーに移動します。このフォルダーには、という名前のファイルが含まれていま [!DNL android]す。
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

         このプロセスにはしばらく時間がかかります。

1. Eclipseを設定します。
   1. Eclipseを起動します。

      Windowsで、Eclipseが起動せず、Eclipseで必要なJavaファイルが見つからないと報告された問題が発生した場合は、次の手順を実行してください。

      * ファイル `-vm C:\[path to your JDK bin]\javaw.exe` にを追加 [!DNL eclipse.ini] します。
   1. /を選 **[!UICONTROL Help]** 択しま **[!UICONTROL Install New Software]** す。
   1. クリック **[!UICONTROL Add...]**.
   1. 名前を `Android` 入力します。
   1. リンク `https://dl-ssl.google.com/android/eclipse/` にと入力 **[!UICONTROL Work with]** します。
   1. クリック **[!UICONTROL OK]**.

      次のようなダイアログが表示されます。

      ![](assets/available_software.jpg)

   1. 表示されるパッケージ（Developer ToolsおよびNDK Pluginsに含まれるパッケージ）を選択し、をクリックしま **[!UICONTROL Next]**&#x200B;す。

      これにより、Android開発ツール(ADT)がダウンロードされます。
   1. ダウンロードが完了したら、Eclipseを再起動します。
   Android SDKがインストールされました。 1.Android SDKを見つけてリソースとして使用できるようにEclipseを設定します。
   1. Eclipseを開きます。
   1. / **[!UICONTROL Window]** Windows **[!UICONTROL Preferences]** を選択します。 **[!UICONTROL ADT]** / **[!UICONTROL Preferences]** Mac OS Xの場合
   1. タブを選択 **[!UICONTROL Android]** します。
   1. Android SDKの場所を参照します。
   1. クリック **[!UICONTROL Apply]**.

      ![ステップの結果](assets/ss2.jpg)


