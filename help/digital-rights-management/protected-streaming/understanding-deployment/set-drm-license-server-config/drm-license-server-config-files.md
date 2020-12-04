---
seo-title: ライセンスサーバー構成ファイル
title: ライセンスサーバー構成ファイル
uuid: 7c7e0f76-2ced-45af-9542-99e06ec31cda
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 0%

---


# ライセンスサーバ構成ファイル{#license-server-configuration-files}

保護ストリーミング用のAdobe PrimetimeDRMサーバーには、次の種類の設定ファイルが必要です。

* グローバル構成ファイル([!DNL flashaccess-global.xml])
* 各テナントのテナント構成ファイル([!DNL flashaccess-tenant.xml])

設定ファイルの編集が完了したら、Adobeでは、Primetime DRM Server for Protected Streamingに付属のユーティリティを使用して、ファイルが正しい形式であることを確認することを推奨します。

*設定バリデーター*&#x200B;を参照してください。

設定ファイル内のパスワードをクリアテキストで表示しないようにするには、Adobeが提供したScramblerツールを使用して、グローバル設定ファイルとテナント設定ファイルで指定したすべてのパスワードを暗号化する必要があります。

パスワードを暗号化する方法の詳細については、*パスワードスクランブラ*&#x200B;を参照してください。
