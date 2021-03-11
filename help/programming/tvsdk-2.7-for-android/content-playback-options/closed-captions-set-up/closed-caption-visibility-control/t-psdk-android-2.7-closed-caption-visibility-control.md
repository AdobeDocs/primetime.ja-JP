---
description: クローズドキャプションの表示を制御できます。 表示を有効にすると、現在選択されているトラックが表示されます。 現在のトラックを変更しても、表示設定は変わりません。
title: クローズドキャプションの表示を制御する
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 1%

---


# 概要{#control-closed-caption-visibility-overview}

クローズドキャプションの表示を制御できます。 表示を有効にすると、現在選択されているトラックが表示されます。 現在のトラックを変更しても、表示設定は変わりません。

>[!TIP]
>
>プレイヤーがシークモードに入ったときにクローズドキャプションテキストが表示された場合、シーク完了後にテキストが表示されることはなくなりました。 代わりに、数秒後に、TVSDKはビデオ内の終了シーク位置の後に次のクローズドキャプションテキストを表示します。
>
>クローズドキャプションの表示値は`MediaPlayer.Visibility`で定義されています。
>
>
```java
>enum Visibility {  
>       VISIBLE,  
>       INVISIBLE 
>}
>```

1. `MediaPlayer`がPREPAREDステータスになるまで待ちます。

   詳しくは、ui-state-prepared-wait-forを参照してください。
1. クローズドキャプションの現在の表示設定を取得するには、`MediaPlayer`のgetterメソッドを使用します。このメソッドは、表示値を返します。

   ```java
   MediaPlayer.Visibility getCCVisibility() throws MediaPlayerException;
   ```

1. クローズドキャプションの表示/非表示を変更するには、setterメソッドを使用して、`MediaPlayer.Visibility`から表示値を渡します。

   例：

   ```java
   mediaPlayer.setCCVisibility(MediaPlayer.Visibility visibility);
   ```

