---
description: Adobe Primetime Ad Decisioning インターフェイスを使用して、VOD およびライブ/リニアコンテンツに広告を挿入できます。
title: 広告要件
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 0%

---

# 広告要件{#advertising-requirements}

Adobe Primetime Ad Decisioning インターフェイスを使用して、VOD およびライブ/リニアコンテンツに広告を挿入できます。

<!--<a id="section_4889E0ED7A4241D98E61AD6C846B84B6"></a>-->

Primetime ad decisioning は TVSDK と連携して、広告オポチュニティの識別、広告の解決、ビデオストリームへの解決済み広告の挿入をおこないます。
ビデオコンテンツに広告を組み込むには、広告とメインのビデオコンテンツが次の要件を満たしていることを確認します。

* 広告コンテンツの HLS バージョンをメインコンテンツの HLS バージョンより高くすることはできません。
* 広告は、メインコンテンツが多重化されているかどうかに関係なく、多重化する必要はありません（制限なし）。
