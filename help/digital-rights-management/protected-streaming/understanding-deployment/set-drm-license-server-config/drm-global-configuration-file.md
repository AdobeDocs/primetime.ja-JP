---
description: flashaccess-global.xml設定ファイルには、ライセンスサーバーのすべてのテナントに適用される設定が含まれています。
seo-description: flashaccess-global.xml設定ファイルには、ライセンスサーバーのすべてのテナントに適用される設定が含まれています。
seo-title: グローバル設定ファイル
title: グローバル設定ファイル
uuid: 294d6cff-be07-4b4b-8aa6-943044a1c56f
translation-type: tm+mt
source-git-commit: d2b8cb67c54fadb8e0e7d2bdc15e393fdce8550e
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---


# グローバル設定ファイル{#global-configuration-file}

flashaccess-global.xml設定ファイルには、ライセンスサーバーのすべてのテナントに適用される設定が含まれています。

設定ファイルは、ディレクトリに配置する必要があり [!DNL LicenseServer.ConfigRoot] ます。

グローバル設定ファイルの例については、 [!DNL configs] ディレクトリを参照してください。

グローバル設定ファイルには、次のものが含まれます。

* 「キャッシュ」 — メモリ内の設定ファイルのキャッシュを制御します。

   キャッシュ設定について詳しくは、 *設定ファイルの更新* を参照してください。
* 「ログ」 — ログ・レベルと、ログ・ファイルをロールする頻度を指定します。
* 「HSMパスワード」 — サーバー秘密鍵証明書の保存にHSMが使用される場合にのみ必要です。

詳しくは、Primetime DRM\ `<DVD>`Adobe PrimetimeDRMサーバー（保護されたストリーミング用）\configsにあるグローバル設定ファイルの例のコメントを参照してください。
