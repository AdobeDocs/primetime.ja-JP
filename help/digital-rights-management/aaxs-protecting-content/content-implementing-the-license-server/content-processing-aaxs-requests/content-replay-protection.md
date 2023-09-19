---
title: リプレイの保護
description: リプレイの保護
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 0%

---

# リプレイの保護{#replay-protection}

再生の保護のために、 `RequestMessageBase.getMessageId()`. その場合、攻撃者は要求を再生しようとする可能性がありますが、これは拒否されるべきです。 再生の試行を検出するために、サーバーは最近表示されたメッセージ ID のリストを保存し、キャッシュされたリストに対して各受信要求を確認できます。 メッセージ識別子を保存する必要がある時間を制限するには、を呼び出します。 `HandlerConfiguration.setTimestampTolerance()`. このプロパティを設定すると、SDK は、指定された秒数を超えるサーバー時間のタイムスタンプを持つ要求を拒否します。
