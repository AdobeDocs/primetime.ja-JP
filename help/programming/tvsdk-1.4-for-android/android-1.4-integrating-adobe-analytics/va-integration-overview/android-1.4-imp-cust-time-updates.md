---
description: 一部の解析実装では、クライアントアプリケーションは、TVSDKのlocalTime値でレポートされる位置とは異なる再生ヘッド位置を提供したい場合があります。 例えば、リニアストリーム再生中に、各プログラムの再生ヘッドを開始時間に対して相対的に提供できます。
title: カスタム時間更新の実装
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---


# カスタム時刻更新の実装{#implement-custom-time-updates}

一部の解析実装では、クライアントアプリケーションは、TVSDKのlocalTime値でレポートされる位置とは異なる再生ヘッド位置を提供したい場合があります。 例えば、リニアストリーム再生中に、各プログラムの再生ヘッドを開始時間に対して相対的に提供できます。

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
>このコードスニペットの値はサンプルのみです。 カスタム再生ヘッドの位置に異なる値を使用する必要があります。