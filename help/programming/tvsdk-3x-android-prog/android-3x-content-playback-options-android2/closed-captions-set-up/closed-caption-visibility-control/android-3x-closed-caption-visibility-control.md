---
description: クローズドキャプションの表示を制御できます。 表示が有効になっている場合は、現在選択されているトラックが表示されます。 現在のトラックを変更した場合、表示設定は変わりません。
title: クローズドキャプションの表示を制御する
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 0%

---

# クローズドキャプションの表示を制御する {#control-closed-caption-visibility}

クローズドキャプションの表示を制御できます。 表示が有効になっている場合は、現在選択されているトラックが表示されます。 現在のトラックを変更した場合、表示設定は変わりません。

>[!TIP]
>
>プレーヤーがシークモードに入ったときにクローズドキャプションテキストが表示される場合、シークが完了した後にテキストが表示されなくなります。 代わりに、数秒後に、 TVSDK はビデオ内のシーク終了位置の後に、次のクローズドキャプションテキストを表示します。
>
>クローズドキャプションの表示値は、 `MediaPlayer.Visibility`.
>
>```java
>enum Visibility {  
>       VISIBLE,  
>       INVISIBLE 
>}
>```
>

1. 待機： `MediaPlayer` 少なくとも PREPARED ステータスになっている。 詳しくは、 [有効なステータスを待つ](../../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/ui-configure/android-3x-ui-state-prepared-wait-for.md).

1. クローズドキャプションの現在の表示設定を取得するには、 `MediaPlayer`：表示値を返します。

   ```java
   MediaPlayer.Visibility getCCVisibility() throws MediaPlayerException;
   ```

1. クローズドキャプションの表示を変更するには、setter メソッドを使用して、表示値を `MediaPlayer.Visibility`.

   例：

   ```java
   mediaPlayer.setCCVisibility(MediaPlayer.Visibility visibility);
   ```
