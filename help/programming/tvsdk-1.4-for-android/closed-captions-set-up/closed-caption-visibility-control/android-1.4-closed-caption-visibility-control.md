---
description: クローズドキャプションの表示を制御できます。 表示がオンの場合、現在選択されているトラックが表示されます。 現在のトラックを変更しても、表示設定は変わりません。
seo-description: クローズドキャプションの表示を制御できます。 表示がオンの場合、現在選択されているトラックが表示されます。 現在のトラックを変更しても、表示設定は変わりません。
seo-title: クローズドキャプションの表示を制御する
title: クローズドキャプションの表示を制御する
uuid: 42913347-8158-474e-aa3c-ba4d38baba12
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# 概要 {#control-closed-caption-visibility}

クローズドキャプションの表示を制御できます。 表示がオンの場合、現在選択されているトラックが表示されます。 現在のトラックを変更しても、表示設定は変わりません。

>[!TIP]
>
>プレイヤーがシークモードに入ったときにクローズドキャプションテキストが表示された場合、シークの完了後にテキストが表示されることはなくなりました。 代わりに、数秒後に、TVSDKはビデオ内の終了シーク位置の後の次のクローズドキャプションテキストを表示します。

>[!NOTE]
>
>クローズドキャプションの表示値は、で定義されま `MediaPlayer.Visibility`す。>
>
```java>
>enum Visibility { 
>       VISIBLE,  
>       INVISIBLE 
>}
>```>



1. MediaPlayerが少なくともPREPARED状態になるまで待ちます(有効な状態にな [るまで待つを参照](../../../tvsdk-1.4-for-android/ui-configure/android-1.4-ui-state-prepared-wait-for.md))。
1. クローズドキャプションの現在の表示設定を取得するには、MediaPlayerのgetterメソッドを使用します。このメソッドは表示値を返します。

   ```java
   Visibility getCCVisibility() throws IllegalStateException;
   ```

1. クローズドキャプションの表示/非表示を変更するには、setterメソッドを使用し、から表示値を渡しま `MediaPlayer.Visibility`す。

   例：

   ```java
   mediaPlayer.setCCVisibility(Visibility.VISIBLE);
   ```

