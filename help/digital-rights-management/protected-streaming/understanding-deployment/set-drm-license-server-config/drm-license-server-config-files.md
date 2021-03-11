---
title: ライセンスサーバー構成ファイル
description: ライセンスサーバー構成ファイル
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
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
