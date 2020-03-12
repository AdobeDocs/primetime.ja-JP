---
description: クローズドキャプションの表示を制御できます。 表示が有効になっている場合は、現在選択されているトラックが表示されます。 現在のトラックを変更しても、表示設定は変わりません。
seo-description: クローズドキャプションの表示を制御できます。 表示が有効になっている場合は、現在選択されているトラックが表示されます。 現在のトラックを変更しても、表示設定は変わりません。
seo-title: クローズドキャプションの表示を制御する
title: クローズドキャプションの表示を制御する
uuid: b9d48d70-2554-4948-8654-fa45093c3782
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# 概要 {#control-closed-caption-visibility-overview}

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



1. がPREPAREDステータ `MediaPlayer` ス以上になるまで待ちます。

   詳しくは、ui-state-prepared-wait-forを参照してください。
1. クローズドキャプションの現在の表示設定を取得するには、のgetterメソッドを使用します。こ `MediaPlayer`のメソッドは、表示値を返します。

   ```java
   MediaPlayer.Visibility getCCVisibility() throws MediaPlayerException;
   ```

1. クローズドキャプションの表示/非表示を変更するには、setterメソッドを使用し、から表示値を渡しま `MediaPlayer.Visibility`す。

   例：

   ```java
   mediaPlayer.setCCVisibility(MediaPlayer.Visibility visibility);
   ```

