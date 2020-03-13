---
seo-title: ライセンスサーバー設定ファイル
title: ライセンスサーバー設定ファイル
uuid: 7c7e0f76-2ced-45af-9542-99e06ec31cda
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# ライセンスサーバー設定ファイル{#license-server-configuration-files}

Adobe Primetime DRM Server for Protected Streamingには、次の種類の設定ファイルが必要です。

* グローバル設定ファイル( [!DNL flashaccess-global.xml])
* 各テナントのテナント構成ファイル( [!DNL flashaccess-tenant.xml])

設定ファイルの編集が完了したら、Primetime DRM Server for Protected Streamingに付属のユーティリティを使用して、ファイルが正しい形式であることを確認することをお勧めします。

設定バリデ *ーターを参照*。

設定ファイル内のパスワードをクリアテキストで使用しないようにする場合は、アドビが提供するScramblerツールを使用して、グローバル設定ファイルとテナント設定ファイルで指定したすべてのパスワードを暗号化する必要があります。

パスワード *の暗号化方法について詳しくは* 、Password Scramblerを参照してください。
