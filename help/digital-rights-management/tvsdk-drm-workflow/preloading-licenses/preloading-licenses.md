---
seo-title: オフライン再生用のプリロードライセンスの概要
title: オフライン再生用のプリロードライセンスの概要
uuid: 71e5169b-7f70-4723-9f9b-fdff822c5876
translation-type: tm+mt
source-git-commit: 9bbcb228d3367fbf53de811bf2941ca653ce3b0e
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 0%

---


# オフライン再生用のプリロードライセンス{#pre-loading-licenses-for-offline-playback}

Primetime DRMで保護されたコンテンツを再生するのに必要なライセンスを事前に読み込むことができます。 事前に読み込まれたライセンスを使用すると、ユーザーは、アクティブなインターネット接続があるかどうかに関係なく、コンテンツを表示できます。

事前読み込みプロセス自体&#x200B;*は、*&#x200B;インターネット接続を必要とします。 事前に`DRMManager.loadVoucher()`を使用して、ライセンスを事前に読み込むことができます。 後で、クライアントが希望のコンテンツを再生したい場合、DRMシステムは事前に準備され、保護されたコンテンツを直ちに再生できます。
