---
description: 機能マネージャーからディスパッチされたイベントをアプリケーションで処理する必要がある場合は、PlayerFragment.javaファイルにマネージャーを登録する必要があります。
title: イベントの処理
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 4%

---


# イベント{#handling-events}の処理

機能マネージャーからディスパッチされたイベントをアプリケーションで処理する必要がある場合は、PlayerFragment.javaファイルにマネージャーを登録する必要があります。

例：

```
private final AdsManager.AdsManagerEventListener adsManagerEventListener =  
  new AdsManager.AdsManagerEventListener() { 
 
    // add the ads functionality... 
 
} 
 
//Register the listener 
adsManager.addEventListener(adsManagerEventListener);
```
