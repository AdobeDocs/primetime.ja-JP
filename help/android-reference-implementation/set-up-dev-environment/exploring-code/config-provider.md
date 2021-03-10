---
description: ConfigProviderクラスは、メディアプレイヤーの設定を取得します。 機能マネージャーが設定情報を読み取れるように、設定インターフェイスを実装する必要があります。
title: ConfigProvider
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---


# ConfigProvider {#configprovider}

ConfigProviderクラスは、メディアプレイヤーの設定を取得します。 機能マネージャーが設定情報を読み取れるように、設定インターフェイスを実装する必要があります。

[ConfigProvider](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html)クラスを使用して`ICCConfig`、`IAAConfig`、`IPlaybackConfig`、`IAdConfig`、`IQosConfig`の各設定インターフェイスを実装し、機能マネージャが設定を読み取れるようにします。 例えば、`ICCConfig`は`CCManager`設定のインターフェイスです。 設定ファイルは、JSON設定ファイルから設定パラメーターを受け取ります。

`ConfigProvider.java`ファイルは、Adobeが設定インターフェイスを実装した例です。 `SharedPreferences`から設定を読み取り、そこに設定が保存されます。 組織で機能するあらゆる方法で設定を保存できます。 config実装は、設定ソースのラッパーを提供します。