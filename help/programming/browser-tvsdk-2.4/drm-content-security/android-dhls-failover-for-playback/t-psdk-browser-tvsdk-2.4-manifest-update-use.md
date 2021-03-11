---
description: この機能をオンにして、関連イベントを確認できます。
title: ライブマスターマニフェストの更新の使用
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '56'
ht-degree: 0%

---


# ライブマスターマニフェストの更新{#use-live-master-manifest-update}を使用

この機能をオンにして、関連イベントを確認できます。

1. ライブマスターマニフェストの更新を有効にするには、`NetworkConfiguration.masterUpdateInterval`プロパティを設定して更新頻度（分単位）を設定します。
1. オプションで、`MediaPlayerItemEvent.MASTER_UPDATED`イベントをリッスンして、成功したマニフェストの更新を追跡します。
