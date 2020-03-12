---
seo-title: 再生保護
title: 再生保護
uuid: 75f2be65-b2fc-428a-b853-34a4b30960ce
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# 再生保護{#replay-protection}

再生の保護のために、呼び出しによってメッセージIDが最近表示されたかどうかを確認することをお勧めしま `RequestMessageBase.getMessageId()`す。 その場合、攻撃者が要求を再実行しようとしている可能性がありますが、これは拒否される必要があります。 再生試行を検出するために、サーバーは最近表示されたメッセージIDのリストを格納し、受信要求をキャッシュされたリストと比較して確認できます。 メッセージ識別子の保存時間を制限するには、を呼び出しま `HandlerConfiguration.setTimestampTolerance()`す。 このプロパティが設定されている場合、SDKは、指定された秒数を超えるタイムスタンプを持つ要求を拒否します。
