---
description: 機能マネージャーは、TVSDKライブラリのラッパーとして機能します。
seo-description: 機能マネージャーは、TVSDKライブラリのラッパーとして機能します。
seo-title: リファレンス実装構造
title: リファレンス実装構造
uuid: ae347a97-1500-476a-9fc8-c99e6b2ab8de
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# リファレンス実装構造 {#reference-implementation-structure}

機能マネージャーは、TVSDKライブラリのラッパーとして機能します。

Javaでは、クラスは階層構造になっています。 例えば、のUI関連のコードと、すべてのフィーチャマ `com.adobe.primetime.reference.ui` ネージャの下にあるすべてのコードが `com.adobe.primetime.reference.manager`、

Primetimeリファレンスの実装には、次のパッケージが含まれています。

| パッケージ | 説明 |
|--- |--- |
| [com.adobe.primetime.reference](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/PrimetimeReference.html) | このクラスは、android.app.Applicationを拡張します。 |
| [com.adobe.primetime.reference.advertising](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/advertising/package-summary.html) | カスタム広告のコードが含まれます。 |
| [com.adobe.primetime.reference.config](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/package-summary.html) | フィーチャマネージャの設定に必要なインターフェイスコードが含まれます。 |
| [com.adobe.primetime.reference.drm](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/drm/package-summary.html) | DRMのヘルパークラスを含みます。 |
| [com.adobe.primetime.reference.feeds](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/feeds/package-summary.html) | インターフェイス、プラットフォーム、および参照情報のアダプタと項目アダプタ。 また、FeedAdapterFactory、ContentRenditionInfoおよびXMLParserHelperコードも含まれます。 |
| [com.adobe.primetime.reference.logging](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/logging/package-summary.html) | ローカルおよびリモートでログを記録するクラスを提供します。 |
| [com.adobe.primetime.reference.manager](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/package-summary.html) | ここでは、フィーチャマネージャとManagerFactoryを見つけることができます。 オプション機能の有効/無効を切り替えることができる場合は、次の2つの機能マネージャがあります。 <ul><li>機能の名前を示す機能マネージャー（例：CCManager）。 この機能マネージャはオフになっており、デフォルトのオフの動作を提供します。</li><li>機能マネージャ名にOnが追加された機能マネージャ（CCManagerOnなど）。 この機能マネージャは、有効な機能のサンプルコードを提供します。</li></ul> |
| [com.adobe.primetime.reference.ui.catalog](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/catalog/package-summary.html) | カタログのUIコードが含まれます。 |
| [com.adobe.primetime.reference.ui.log](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/log/package-summary.html) | ログのUIコードが含まれます。 |
| [com.adobe.primetime.reference.ui.player](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/player/package-summary.html) | プレイヤーのUIコードが含まれます。 |
| [com.adobe.primetime.reference.ui.settings](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/settings/package-summary.html) | 設定のUIコードが含まれます。 |
| [com.adobe.primetime.reference.utils](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/utils/package-summary.html) | 一般的なユーティリティクラスが含まれます。 |
| [com.adobe.primetime.reference.utils.http](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/utils/http/package-summary.html) | ユーティリテ `HTTP-specific` ィクラスが含まれます。 |
