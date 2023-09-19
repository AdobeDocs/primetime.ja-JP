---
description: ConfigProvider クラスは、メディアプレーヤーの設定を取得します。 機能マネージャーが設定情報を読み取れるように、設定インターフェイスを実装する必要があります。
title: ConfigProvider
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---

# ConfigProvider {#configprovider}

ConfigProvider クラスは、メディアプレーヤーの設定を取得します。 機能マネージャーが設定情報を読み取れるように、設定インターフェイスを実装する必要があります。

次を使用します。 [ConfigProvider](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html) 実装するクラス `ICCConfig`, `IAAConfig`, `IPlaybackConfig`, `IAdConfig`、および `IQosConfig` コンフィギュレーションインターフェイスを使用して、機能マネージャが設定を読み取れるようにします。 例えば、 `ICCConfig` は、 `CCManager` 設定。 設定ファイルは、JSON 設定ファイルから設定パラメーターを受け取ります。

The `ConfigProvider.java` file は、設定インターフェイスをAdobeが実装した例です。 次の設定を読み取ります。 `SharedPreferences`：設定が格納されます。 設定は、組織に適した任意の方法で保存できます。 config 実装は、設定ソースのラッパーを提供します。
