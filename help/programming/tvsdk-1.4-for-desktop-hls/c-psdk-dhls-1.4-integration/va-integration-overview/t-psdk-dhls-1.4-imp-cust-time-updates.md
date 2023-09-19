---
description: 特定の Analytics 実装では、クライアントアプリケーションは、 TVSDK localTime 値で報告されるものとは異なる再生ヘッドの位置を提供する必要がある場合があります。 例えば、LINEAR ストリームの再生中に、各プログラムの再生ヘッドを開始時間に対して相対的に指定できます。
title: カスタム時間更新の実装
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---

# カスタム時間更新の実装{#implement-custom-time-updates}

特定の Analytics 実装では、クライアントアプリケーションは、 TVSDK localTime 値で報告されるものとは異なる再生ヘッドの位置を提供する必要がある場合があります。 例えば、LINEAR ストリームの再生中に、各プログラムの再生ヘッドを開始時間に対して相対的に指定できます。

>[!TIP]
>
>デフォルトの位置とは異なる再生ヘッドの位置を指定する場合にのみ、このメソッドをオーバーライドします。

1. デフォルトの再生ヘッドの位置を上書きするには：

   ```
   vaMetadata.currentTimeUpdateBlock = function():Number { 
      if (currentTime == 0) { 
          currentTime = getTimer(); 
      } 
      return ((getTimer() - currentTime) / 1000 + 1000); 
   }
   ```

   >[!IMPORTANT]
   >
   >このコードスニペットの値は、サンプルのみです。 カスタム再生ヘッドの位置に異なる値を使用する必要があります。
