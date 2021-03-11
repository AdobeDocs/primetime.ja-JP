---
title: DRMStatusEventハンドラーの作成
description: DRMStatusEventハンドラーの作成
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 0%

---


# DRMStatusEventハンドラーの作成{#create-a-drmstatusevent-handler}

次の例では、イベントを生成したPrimetimeオブジェクトのDRMコンテンツのステータス情報を出力するイベントハンドラーを作成します。

保護さ追加れたコンテンツを指すPrimetimeオブジェクトのイベントハンドラー：

```
function drmStatusEventHandler(event:DRMStatusEvent):void { trace(event); } 
```

