---
description: 広告、名前空間および追跡用のメタデータを提供するクラスです。
title: Metadataクラス
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---


# Metadataクラス{#metadata-classes}

広告、名前空間および追跡用のメタデータを提供するクラスです。

パッケージ：[com.adobe.mediacore.metadata](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/package-summary.html)

| 名前 | 説明 |
|---|---|
| [AdvertisingMetadata](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/AdvertisingMetadata.html) | 特定のメディア項目の広告を解決するために設定する必要があるプロパティを提供するクラス。 プレイヤーが広告を正しく解決できるように、必要なすべてのプロパティを設定する必要があります。 |
| AuditudeMetadata | 廃止。 AuditudeSettingsを使用します。 |
| [AuditudeSettings](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/AuditudeSettings.html) | 特にPhrase用にJava `AdvertisingMetadata`を拡張するクラス。 特定のメディア項目のフレーズ広告を解決するために設定するプロパティを提供します。 プレイヤーが広告を正しく解決できるように、ゾーンID、メディアID、広告サーバーURLなど、必要なすべてのプロパティを設定する必要があります。 |
| [メタデータ](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/Metadata.html) | プレイヤーと追加オブジェクトに使用できるすべてのメタデータを設定する汎用インターフェイスを定義します。 |
| [MetadataNode](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/MetadataNode.html) | 任意のキーと値のペアを格納する、データ構造に似た汎用クラス。 |
| [TimedMetadata](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/TimedMetadata.html) | メディアストリームに挿入される時間指定メタデータの生の表現のクラス。 |