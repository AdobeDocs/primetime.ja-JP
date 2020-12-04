---
description: クローズドキャプションの表示を制御できます。 表示がオンの場合、現在選択されているトラックが表示されます。
seo-description: クローズドキャプションの表示を制御できます。 表示がオンの場合、現在選択されているトラックが表示されます。
seo-title: クローズドキャプションの表示を制御する
title: クローズドキャプションの表示を制御する
uuid: b161a729-73f3-4019-a95e-013b42779842
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '143'
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

