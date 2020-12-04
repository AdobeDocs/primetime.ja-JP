---
description: 特定の解析実装では、クライアントアプリケーションは、TVSDKのlocalTime値でレポートされるのとは異なる再生ヘッド位置を提供したい場合があります。 例えば、LINEARストリーム再生中に、各プログラムの再生ヘッドを、開始時間を基準にして提供できます。
seo-description: 特定の解析実装では、クライアントアプリケーションは、TVSDKのlocalTime値でレポートされるのとは異なる再生ヘッド位置を提供したい場合があります。 例えば、LINEARストリーム再生中に、各プログラムの再生ヘッドを、開始時間を基準にして提供できます。
seo-title: カスタム時間更新の実装
title: カスタム時間更新の実装
uuid: 2b46eca9-3815-4c44-ab5e-21678c35f410
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '181'
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

