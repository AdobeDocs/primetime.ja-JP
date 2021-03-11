---
description: 特定の解析実装では、クライアントアプリケーションは、TVSDKのlocalTime値でレポートされるのとは異なる再生ヘッド位置を提供したい場合があります。 例えば、LINEARストリーム再生中に、各プログラムの再生ヘッドを、開始時間を基準にして提供できます。
title: カスタム時間更新の実装
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---


# カスタム時刻更新の実装{#implement-custom-time-updates}

特定の解析実装では、クライアントアプリケーションは、TVSDKのlocalTime値でレポートされるのとは異なる再生ヘッド位置を提供したい場合があります。 例えば、LINEARストリーム再生中に、各プログラムの再生ヘッドを、開始時間を基準にして提供できます。

>[!TIP]
>
>デフォルトの位置とは異なる再生ヘッドの位置を指定する場合にのみ、このメソッドを上書きします。

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
   >このコードスニペットの値はサンプルのみです。 カスタム再生ヘッドの位置に異なる値を使用する必要があります。

