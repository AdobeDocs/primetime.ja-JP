---
description: ConfigProvider クラスを使用して最初に DVR ストリームに入るデフォルトの動作ではなく、DVR ストリームに入るタイミングのカスタム開始点を選択できます。
title: DVR のカスタム開始点の選択
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---

# DVR のカスタム開始点の選択 {#choosing-a-custom-starting-point-for-dvr}

ConfigProvider クラスを使用して最初に DVR ストリームに入るデフォルトの動作ではなく、DVR ストリームに入るタイミングのカスタム開始点を選択できます。

開始時間を [ConfigProvider](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html) クラス：

1. 有効にする [isCustomPositionPrefEnabled()](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html#isCustomPositionPrefEnabled()).
1. 開始時間を [retrieveStartTimePref()](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html#iretrieveStartTimePref()).
1. カスタムの開始位置が有効になっていることを確認します。
