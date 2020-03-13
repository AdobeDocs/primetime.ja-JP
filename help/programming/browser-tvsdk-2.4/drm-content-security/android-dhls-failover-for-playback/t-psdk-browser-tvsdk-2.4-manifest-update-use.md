---
description: この機能をオンにして、関連イベントを確認できます。
seo-description: この機能をオンにして、関連イベントを確認できます。
seo-title: ライブマスターマニフェストの更新の使用
title: ライブマスターマニフェストの更新の使用
uuid: 4ec665ab-b7ce-4a45-a251-13a07eb4d789
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# ライブマスターマニフェストの更新の使用{#use-live-master-manifest-update}

この機能をオンにして、関連イベントを確認できます。

1. ライブマスターマニフェストの更新を有効にするには、プロパティを設定して更新頻度（分単位）を設定 `NetworkConfiguration.masterUpdateInterval` します。
1. オプションで、イベントをリッスンして、成功したマニフェストの更新を追 `MediaPlayerItemEvent.MASTER_UPDATED` 跡します。
