---
description: 一部の解析実装では、クライアントアプリケーションは、TVSDKのlocalTime値でレポートされる位置とは異なる再生ヘッド位置を提供したい場合があります。 例えば、リニアストリーム再生中に、各プログラムの再生ヘッドを開始時間に対して相対的に提供できます。
title: カスタム時間更新の実装
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---


# カスタム時刻更新の実装{#implement-custom-time-updates}

一部の解析実装では、クライアントアプリケーションは、TVSDKのlocalTime値でレポートされる位置とは異なる再生ヘッド位置を提供したい場合があります。 例えば、リニアストリーム再生中に、各プログラムの再生ヘッドを開始時間に対して相対的に提供できます。

>[!TIP]
>
>デフォルトの位置とは異なる再生ヘッドの位置を指定する場合にのみ、このメソッドを上書きします。

1. デフォルトの再生ヘッドの位置を上書きするには：

   ```
   vaTrackingMetadata.currentTimeUpdateBlock = ^CMTime () { 
       NSInteger random = arc4random() % 500;  
       return CMTimeMakeWithSeconds(random, 1); 
   };
   ```

   >[!IMPORTANT]
   >
   >このコードのサンプルでは、500はサンプル値にすぎません。 カスタム再生ヘッドの位置に別の値を使用する必要があります。

