---
description: 機能マネージャーは、TVSDK ライブラリのラッパーとして機能します。
title: 参照実装構造
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# 参照実装構造 {#reference-implementation-structure}

機能マネージャーは、TVSDK ライブラリのラッパーとして機能します。

Java では、クラスは階層内で構造化されます。 例えば、以下のすべての UI 関連コード。 `com.adobe.primetime.reference.ui` すべての機能マネージャが以下の場所にあります。 `com.adobe.primetime.reference.manager`.

Primetime リファレンス実装には、次のパッケージが含まれています。

| パッケージ | 説明 |
|--- |--- |
| [com.adobe.primetime.reference](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/PrimetimeReference.html) | このクラスは、android.app.Application を拡張したものです。 |
| [com.adobe.primetime.reference.advertising](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/advertising/package-summary.html) | カスタム広告のコードが含まれます。 |
| [com.adobe.primetime.reference.config](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/package-summary.html) | 機能マネージャの設定に必要なインターフェイスコードが含まれます。 |
| [com.adobe.primetime.reference.drm](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/drm/package-summary.html) | DRM のヘルパークラスが含まれます。 |
| [com.adobe.primetime.reference.feeds](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/feeds/package-summary.html) | インターフェイス、プラットフォーム、および参照情報のアダプタと項目アダプタ。 また、FeedAdapterFactory、ContentRenditionInfo、XMLParserHelper コードも含まれます。 |
| [com.adobe.primetime.reference.logging](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/logging/package-summary.html) | ローカルおよびリモートでログを記録するクラスを提供します。 |
| [com.adobe.primetime.reference.manager](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/package-summary.html) | ここでは、ManagerFactory と同様に、機能マネージャを検索できます。 有効または無効にできるオプション機能には、次の 2 つの機能マネージャがあります。 <ul><li>機能の名前を示す 1 つの機能マネージャ（CCManager など）。 この機能マネージャはオフになり、既定のオフ動作を提供します。</li><li>機能マネージャ名に「On」が付いた機能マネージャ（例： CCManagerOn）。 この機能マネージャには、有効な機能のサンプルコードが用意されています。</li></ul> |
| [com.adobe.primetime.reference.ui.catalog](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/catalog/package-summary.html) | カタログの UI コードが含まれます。 |
| [com.adobe.primetime.reference.ui.log](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/log/package-summary.html) | ログの UI コードが含まれます。 |
| [com.adobe.primetime.reference.ui.player](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/player/package-summary.html) | プレーヤーの UI コードが含まれます。 |
| [com.adobe.primetime.reference.ui.settings](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/settings/package-summary.html) | 設定の UI コードが含まれます。 |
| [com.adobe.primetime.reference.utils](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/utils/package-summary.html) | 一般的なユーティリティクラスが含まれます。 |
| [com.adobe.primetime.reference.utils.http](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/utils/http/package-summary.html) | 次を含む `HTTP-specific` ユーティリティクラス。 |
