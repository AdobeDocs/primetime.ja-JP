---
description: クローズドキャプションの表示を制御できます。 表示がオンの場合、現在選択されているトラックが表示されます。
title: クローズドキャプションの表示を制御する
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---


# クローズドキャプションの表示/非表示を制御{#control-closed-caption-visibility}

クローズドキャプションの表示を制御できます。 表示がオンの場合、現在選択されているトラックが表示されます。

>[!TIP]
>
>現在のトラックを変更しても、表示設定は変わりません。

プレイヤーがシークモードに入ったときにクローズドキャプションテキストが表示されている場合、シーク完了後にテキストは表示されなくなります。 代わりに、数秒後に、Browser TVSDKは、ビデオ内の終了シーク位置の後に、次のクローズドキャプションテキストを表示します。

>[!TIP]
>
>クローズドキャプションの表示値は、`MediaPlayer.VISIBLE`と`MediaPlayer.INVISIBLE`で制御します。

1. クローズドキャプションの現在の表示設定にアクセスするには、`MediaPlayer.ccVisibility`プロパティを使用します。

