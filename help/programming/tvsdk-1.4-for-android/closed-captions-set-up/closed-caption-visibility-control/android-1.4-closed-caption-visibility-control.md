---
description: クローズドキャプションの表示を制御できます。 表示がオンの場合は、現在選択されているトラックが表示されます。 現在のトラックを変更した場合、表示設定は変わりません。
title: クローズドキャプションの表示を制御する
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---

# 概要 {#control-closed-caption-visibility}

クローズドキャプションの表示を制御できます。 表示がオンの場合は、現在選択されているトラックが表示されます。 現在のトラックを変更した場合、表示設定は変わりません。

>[!TIP]
>
>プレーヤーがシークモードに入ったときにクローズドキャプションテキストが表示される場合、シークが完了した後にテキストが表示されなくなります。 代わりに、数秒後に、 TVSDK はビデオ内のシーク終了位置の後に、次のクローズドキャプションテキストを表示します。

>[!NOTE]
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

1. MediaPlayer の状態が PREPARED 以上になるのを待ちます ( [有効な状態になるのを待つ](../../../tvsdk-1.4-for-android/ui-configure/android-1.4-ui-state-prepared-wait-for.md)) をクリックします。
1. クローズドキャプションの現在の表示設定を取得するには、MediaPlayer の getter メソッドを使用します。このメソッドは、表示値を返します。

   ```java
   Visibility getCCVisibility() throws IllegalStateException;
   ```

1. クローズドキャプションの表示を変更するには、setter メソッドを使用して、表示値を `MediaPlayer.Visibility`.

   例：

   ```java
   mediaPlayer.setCCVisibility(Visibility.VISIBLE);
   ```
