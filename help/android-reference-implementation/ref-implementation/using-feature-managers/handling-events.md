---
description: 機能マネージャーからディスパッチされるイベントを処理する必要がある場合は、PlayerFragment.java ファイルにマネージャーを登録する必要があります。
title: イベントの処理
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 0%

---

# イベントの処理 {#handling-events}

機能マネージャーからディスパッチされるイベントを処理する必要がある場合は、PlayerFragment.java ファイルにマネージャーを登録する必要があります。

例：

```
private final AdsManager.AdsManagerEventListener adsManagerEventListener =  
  new AdsManager.AdsManagerEventListener() { 
 
    // add the ads functionality... 
 
} 
 
//Register the listener 
adsManager.addEventListener(adsManagerEventListener);
```
