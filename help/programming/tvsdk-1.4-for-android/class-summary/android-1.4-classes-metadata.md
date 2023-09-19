---
description: 広告、名前空間および追跡用のメタデータを提供するクラスです。
title: Metadata クラス
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# Metadata クラス{#metadata-classes}

広告、名前空間および追跡用のメタデータを提供するクラスです。

パッケージ： [com.adobe.mediacore.metadata](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/package-summary.html)

| 名前 | 説明 |
|---|---|
| [AdvertisingMetadata](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/AdvertisingMetadata.html) | 特定のメディア項目の広告を解決するために設定する必要があるプロパティを提供するクラス。 プレーヤーが広告を正常に解決できるように、必要なすべてのプロパティを設定する必要があります。 |
| AuditudeMetadata | 廃止されました。 AuditudeSettings を使用します。 |
| [AuditudeSettings](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/AuditudeSettings.html) | Java を拡張するクラス `AdvertisingMetadata` 特にフレーズ用です。 特定のメディア項目のフレーズ広告を解決するために設定されるプロパティを提供します。 プレーヤーが広告を正しく解決できるように、ゾーン ID、メディア ID、広告サーバー URL など、必要なすべてのプロパティを設定する必要があります。 |
| [メタデータ](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/Metadata.html) | プレーヤーおよび追加オブジェクトで使用可能なすべてのメタデータを設定する汎用インターフェイスを定義します。 |
| [MetadataNode](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/MetadataNode.html) | 任意のキーと値のペアを保存するための汎用のデータ構造に似たクラス。 |
| [TimedMetadata](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/TimedMetadata.html) | メディアストリームに挿入された時間指定メタデータの生の表現用のクラス。 |
