---
description: 機能マネージャーからディスパッチされたイベントをアプリケーションで処理する必要がある場合は、PlayerFragment.javaファイルにマネージャーを登録する必要があります。
seo-description: 機能マネージャーからディスパッチされたイベントをアプリケーションで処理する必要がある場合は、PlayerFragment.javaファイルにマネージャーを登録する必要があります。
seo-title: イベントの処理
title: イベントの処理
uuid: 13639f02-0dcc-4a0a-8524-515da5478006
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# イベントの処理 {#handling-events}

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
