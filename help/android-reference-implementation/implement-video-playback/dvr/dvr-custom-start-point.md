---
description: ConfigProviderクラスを使用して最初にDVRストリームを入力するというデフォルトの動作の代わりに、いつDVRストリームに入るかのカスタム開始ポイントを選択できます。
seo-description: ConfigProviderクラスを使用して最初にDVRストリームを入力するというデフォルトの動作の代わりに、いつDVRストリームに入るかのカスタム開始ポイントを選択できます。
seo-title: DVRのカスタムスタートポイントの選択
title: DVRのカスタムスタートポイントの選択
uuid: a7e13865-2b86-4234-ac4c-9a5320b293db
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# DVRのカスタムスタートポイントの選択 {#choosing-a-custom-starting-point-for-dvr}

ConfigProviderクラスを使用して最初にDVRストリームを入力するというデフォルトの動作の代わりに、いつDVRストリームに入るかのカスタム開始ポイントを選択できます。

ConfigProviderクラスを使用して開始時間を設定す [るには](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html) :

1. isCustomPositionPrefEnabled() [を有効にします](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html#isCustomPositionPrefEnabled())。
1. 開始時間をretrieveStartTimePref() [で設定します](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html#iretrieveStartTimePref())。
1. カスタムの開始位置が有効になっていることを確認します。
