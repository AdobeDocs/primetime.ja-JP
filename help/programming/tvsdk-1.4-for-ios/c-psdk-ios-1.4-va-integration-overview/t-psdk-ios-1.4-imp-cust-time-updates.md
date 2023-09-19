---
description: 一部の Analytics 実装では、クライアントアプリケーションが、TVSDK の localTime 値で報告される位置とは異なる再生ヘッドの位置を提供する必要が生じる場合があります。 例えば、リニアストリームの再生中に、各プログラムの再生ヘッドを開始時間に対して相対的に提供できます。
title: カスタム時間更新の実装
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# カスタム時間更新の実装{#implement-custom-time-updates}

一部の Analytics 実装では、クライアントアプリケーションが、TVSDK の localTime 値で報告される位置とは異なる再生ヘッドの位置を提供する必要が生じる場合があります。 例えば、リニアストリームの再生中に、各プログラムの再生ヘッドを開始時間に対して相対的に提供できます。

>[!TIP]
>
>デフォルト位置とは異なる再生ヘッドの位置を指定する場合にのみ、このメソッドをオーバーライドします。

1. デフォルトの再生ヘッドの位置を上書きするには：

   ```
   vaTrackingMetadata.currentTimeUpdateBlock = ^CMTime () { 
       NSInteger random = arc4random() % 500;  
       return CMTimeMakeWithSeconds(random, 1); 
   };
   ```

   >[!IMPORTANT]
   >
   >このコードサンプルでは、500 はサンプル値のみです。 カスタム再生ヘッドの位置に別の値を使用する必要があります。
