---
description: ConfigProviderクラスは、メディアプレイヤーの設定を取得します。 機能マネージャーが設定情報を読み取れるように、設定インターフェイスを実装する必要があります。
seo-description: ConfigProviderクラスは、メディアプレイヤーの設定を取得します。 機能マネージャーが設定情報を読み取れるように、設定インターフェイスを実装する必要があります。
seo-title: ConfigProvider
title: ConfigProvider
uuid: 2467a617-6413-4b5d-9710-894cdc751b26
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# ConfigProvider {#configprovider}

ConfigProviderクラスは、メディアプレイヤーの設定を取得します。 機能マネージャーが設定情報を読み取れるように、設定インターフェイスを実装する必要があります。

ConfigProviderクラスを使用して、 [、、、](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html) 、 `ICCConfig`およ `IAAConfig`び設 `IPlaybackConfig``IAdConfig``IQosConfig` 定インターフェイスを実装し、フィーチャマネージャが設定を読み取れるようにします。 例えば、は設定のイ `ICCConfig` ンターフェイス `CCManager` です。 設定ファイルは、JSON設定ファイルから設定パラメーターを受け取ります。

このフ `ConfigProvider.java` ァイルは、アドビの設定インターフェイスの実装例です。 設定はから読み取られ、 `SharedPreferences`設定が保存されます。 組織で機能するあらゆる方法で設定を保存できます。 config実装は、設定ソースのラッパーを提供します。