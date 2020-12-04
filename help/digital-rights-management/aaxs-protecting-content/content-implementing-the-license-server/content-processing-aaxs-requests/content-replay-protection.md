---
seo-title: 再生保護
title: 再生保護
uuid: 75f2be65-b2fc-428a-b853-34a4b30960ce
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 0%

---


# リプレイ保護{#replay-protection}

再生保護のため、`RequestMessageBase.getMessageId()`を呼び出して、メッセージIDが最近表示されたかどうかを確認することをお勧めします。 その場合、攻撃者は要求を再生しようとしている可能性がありますが、これは拒否されるはずです。 再生試行を検出するために、サーバーは最近表示されたメッセージIDのリストを格納し、キャッシュされたリストに対して各着信要求を確認できます。 メッセージ識別子の保存時間を制限するには、`HandlerConfiguration.setTimestampTolerance()`を呼び出します。 このプロパティを設定すると、SDKは、指定された秒数を超えるタイムスタンプを持つ要求を拒否します。
