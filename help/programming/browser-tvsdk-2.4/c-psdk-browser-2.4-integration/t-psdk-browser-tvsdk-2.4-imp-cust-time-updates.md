---
description: 一部の解析の実装では、クライアントアプリケーションは、Browser TVSDK localTime値でレポートされる位置とは異なる再生ヘッドの位置を提供する必要があります。
seo-description: 一部の解析の実装では、クライアントアプリケーションは、Browser TVSDK localTime値でレポートされる位置とは異なる再生ヘッドの位置を提供する必要があります。
seo-title: カスタム時間の更新の実装
title: カスタム時間の更新の実装
uuid: 26a0592c-a47b-4d65-b984-5e51533dcddc
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# カスタム時間の更新の実装{#implement-custom-time-updates}

一部の解析の実装では、クライアントアプリケーションは、Browser TVSDK localTime値でレポートされる位置とは異なる再生ヘッドの位置を提供する必要があります。

例えば、リニアストリーム再生中に、各プログラムの再生ヘッドを開始時間を基準にして提供できます。

>[!TIP]
>
>デフォルトの位置以外の再生ヘッドの位置を指定する場合にのみ、このメソッドを上書きします。

デフォルトの再生ヘッドの位置を上書きするには：

```js
vaMetadata.currentTimeUpdateBlock = function() { 
       return playerPositionInSeconds; 
}; 
```

>[!IMPORTANT]
>
>このコードスニペットの値はサンプルのみです。 カスタム再生ヘッドの位置には、異なる値を使用する必要があります。

