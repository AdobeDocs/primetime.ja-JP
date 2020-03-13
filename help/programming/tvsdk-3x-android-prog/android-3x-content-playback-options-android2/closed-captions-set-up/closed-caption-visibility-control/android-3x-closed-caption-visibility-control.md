---
description: クローズドキャプションの表示を制御できます。 表示が有効になっている場合は、現在選択されているトラックが表示されます。 現在のトラックを変更しても、表示設定は変わりません。
seo-description: クローズドキャプションの表示を制御できます。 表示が有効になっている場合は、現在選択されているトラックが表示されます。 現在のトラックを変更しても、表示設定は変わりません。
seo-title: クローズドキャプションの表示を制御する
title: クローズドキャプションの表示を制御する
uuid: f142e60d-5581-4d1c-9d4d-a4a58ac1b67b
translation-type: tm+mt
source-git-commit: ed910a60440ae7c0d19d9be56c80c8bdbc62bcf1

---


# クローズドキャプションの表示を制御する {#control-closed-caption-visibility}

クローズドキャプションの表示を制御できます。 表示が有効になっている場合は、現在選択されているトラックが表示されます。 現在のトラックを変更しても、表示設定は変わりません。

>[!TIP]
>
>プレイヤーがシークモードに入ったときにクローズドキャプションテキストが表示される場合、シークの完了後にテキストが表示されることはなくなりました。 代わりに、数秒後に、TVSDKはビデオ内の終了シーク位置の後の次のクローズドキャプションテキストを表示します。
>
>クローズドキャプションの表示値は、で定義されま `MediaPlayer.Visibility`す。>
>
```java>
>enum Visibility {  
>       VISIBLE,  
>       INVISIBLE 
>}
>```>



1. がPREPAREDステータ `MediaPlayer` ス以上になるまで待ちます。 詳しくは、「有効なステータスを [待機する」を参照してください](../../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/ui-configure/android-3x-ui-state-prepared-wait-for.md)。

1. クローズドキャプションの現在の表示設定を取得するには、のgetterメソッドを使用します。こ `MediaPlayer`のメソッドは、表示値を返します。

   ```java
   MediaPlayer.Visibility getCCVisibility() throws MediaPlayerException;
   ```

1. クローズドキャプションの表示/非表示を変更するには、setterメソッドを使用し、から表示値を渡しま `MediaPlayer.Visibility`す。

   例：

   ```java
   mediaPlayer.setCCVisibility(MediaPlayer.Visibility visibility);
   ```
