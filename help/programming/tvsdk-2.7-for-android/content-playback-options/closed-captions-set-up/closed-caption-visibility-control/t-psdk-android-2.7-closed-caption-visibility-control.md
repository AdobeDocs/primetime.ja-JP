---
description: クローズドキャプションの表示を制御できます。 表示を有効にすると、現在選択されているトラックが表示されます。 現在のトラックを変更しても、表示設定は変わりません。
seo-description: クローズドキャプションの表示を制御できます。 表示を有効にすると、現在選択されているトラックが表示されます。 現在のトラックを変更しても、表示設定は変わりません。
seo-title: クローズドキャプションの表示を制御する
title: クローズドキャプションの表示を制御する
uuid: b9d48d70-2554-4948-8654-fa45093c3782
translation-type: tm+mt
source-git-commit: 5df9a8b98baaf1cd1803581d2b60c7ed4261a0e8
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---


# 概要 {#control-closed-caption-visibility-overview}

クローズドキャプションの表示を制御できます。 表示を有効にすると、現在選択されているトラックが表示されます。 現在のトラックを変更しても、表示設定は変わりません。

>[!TIP]
>
>プレイヤーがシークモードに入ったときにクローズドキャプションテキストが表示された場合、シーク完了後にテキストが表示されることはなくなりました。 代わりに、数秒後に、TVSDKはビデオ内の終了シーク位置の後に次のクローズドキャプションテキストを表示します。
>
>クローズドキャプションの表示値は、で定義し `MediaPlayer.Visibility`ます。
>
>
```java
>enum Visibility {  
>       VISIBLE,  
>       INVISIBLE 
>}
>```

1. PREPAREDステータス `MediaPlayer` 以上になるまで待ちます。

   詳しくは、ui-state-prepared-wait-forを参照してください。
1. クローズドキャプションの現在の表示設定を取得するには、のgetterメソッドを使用します。このメソッドは、表示値 `MediaPlayer`を返します。

   ```java
   MediaPlayer.Visibility getCCVisibility() throws MediaPlayerException;
   ```

1. クローズドキャプションの表示/非表示を変更するには、setterメソッドを使用して、表示値をから渡し `MediaPlayer.Visibility`ます。

   例：

   ```java
   mediaPlayer.setCCVisibility(MediaPlayer.Visibility visibility);
   ```

