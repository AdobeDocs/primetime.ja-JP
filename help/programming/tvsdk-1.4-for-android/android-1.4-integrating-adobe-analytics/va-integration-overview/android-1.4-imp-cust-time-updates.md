---
description: 一部の解析の実装では、TVSDK localTime値でレポートされる位置とは異なる再生ヘッドの位置をクライアントアプリケーションで提供する必要があります。 例えば、リニアストリーム再生中に、各プログラムの再生ヘッドを開始時間を基準にして提供できます。
seo-description: 一部の解析の実装では、TVSDK localTime値でレポートされる位置とは異なる再生ヘッドの位置をクライアントアプリケーションで提供する必要があります。 例えば、リニアストリーム再生中に、各プログラムの再生ヘッドを開始時間を基準にして提供できます。
seo-title: カスタム時間の更新の実装
title: カスタム時間の更新の実装
uuid: 7f5d46e5-eab6-4bdc-b015-ae27ddb609ce
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# カスタム時間の更新の実装 {#implement-custom-time-updates}

一部の解析の実装では、TVSDK localTime値でレポートされる位置とは異なる再生ヘッドの位置をクライアントアプリケーションで提供する必要があります。 例えば、リニアストリーム再生中に、各プログラムの再生ヘッドを開始時間を基準にして提供できます。

>[!TIP]
>
>デフォルトの位置以外の再生ヘッドの位置を指定する場合にのみ、このメソッドを上書きします。

デフォルトの再生ヘッドの位置を上書きするには：

```java
vaMetadata.setCurrentTimeUpdateBlock(new VideoAnalyticsMetadata.CurrentTimeUpdateBlock() { 
    @Override 
    public long call() { 
        long range = 500L; 
        Random r = new Random() 
        return (long)(r.nextDouble()*range); 
    } 
});
```

>[!IMPORTANT]
>
>このコードスニペットの値はサンプルのみです。 カスタム再生ヘッドの位置には、異なる値を使用する必要があります。