---
description: ConfigProviderクラスを使用して最初にDVRストリームに入るときのデフォルトの動作の代わりに、いつDVRストリームに入るかのカスタム開始ポイントを選択できます。
title: DVRのカスタム開始ポイントの選択
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---


# DVR {#choosing-a-custom-starting-point-for-dvr}のカスタム開始ポイントの選択

ConfigProviderクラスを使用して最初にDVRストリームに入るときのデフォルトの動作の代わりに、いつDVRストリームに入るかのカスタム開始ポイントを選択できます。

[ConfigProvider](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html)クラスを使用して開始時間を設定するには：

1. [isCustomPositionPrefEnabled()](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html#isCustomPositionPrefEnabled())を有効にします。
1. [retrieveStartTimePref()](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html#iretrieveStartTimePref())に開始時刻を設定します。
1. カスタム開始の位置が有効になっていることを確認します。
