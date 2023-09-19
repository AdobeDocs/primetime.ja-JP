---
title: オフライン再生用のライセンスのプリロードの概要
description: オフライン再生用のライセンスのプリロードの概要
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 0%

---

# オフライン再生用のライセンスのプリロード {#pre-loading-licenses-for-offline-playback}

Primetime DRM で保護されたコンテンツの再生に必要なライセンスをプリロードできます。 事前に読み込まれたライセンスを使用すると、ユーザーはアクティブなインターネット接続を持っているかどうかに関わらずコンテンツを表示できます。

プリロードプロセス自体 *は、* には、インターネット接続が必要です。 以下を使用できます。 `DRMManager.loadVoucher()` 事前にライセンスをプリロードする。 その後、クライアントが目的のコンテンツを再生したい場合、DRM システムは事前に準備され、保護されたコンテンツを直ちに再生できます。
