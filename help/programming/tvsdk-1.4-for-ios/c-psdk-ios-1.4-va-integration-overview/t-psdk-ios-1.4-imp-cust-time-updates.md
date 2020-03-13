---
description: 一部の解析の実装では、TVSDKのlocalTime値によってレポートされる位置とは異なる再生ヘッドの位置をクライアントアプリケーションが提供する必要がある場合があります。 例えば、リニアストリーム再生中に、各プログラムの再生ヘッドを開始時間を基準にして提供できます。
seo-description: 一部の解析の実装では、TVSDKのlocalTime値によってレポートされる位置とは異なる再生ヘッドの位置をクライアントアプリケーションが提供する必要がある場合があります。 例えば、リニアストリーム再生中に、各プログラムの再生ヘッドを開始時間を基準にして提供できます。
seo-title: カスタム時間の更新の実装
title: カスタム時間の更新の実装
uuid: 303303eb-c371-4766-a1ee-806ba75b4e01
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# カスタム時間の更新の実装{#implement-custom-time-updates}

一部の解析の実装では、TVSDKのlocalTime値によってレポートされる位置とは異なる再生ヘッドの位置をクライアントアプリケーションが提供する必要がある場合があります。 例えば、リニアストリーム再生中に、各プログラムの再生ヘッドを開始時間を基準にして提供できます。

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
   >このコードサンプルでは、500はサンプル値のみです。 カスタム再生ヘッドの位置に別の値を使用する必要があります。

