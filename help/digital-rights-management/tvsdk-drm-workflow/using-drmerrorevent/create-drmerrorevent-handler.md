---
title: DRMErrorEventハンドラーの作成
description: DRMErrorEventハンドラーの作成
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '63'
ht-degree: 0%

---


# DRMErrorEventハンドラー{#create-a-drmerrorevent-handler}を作成します

保護されたコンテンツの再生を試みているときにエラーが発生した場合にPrimetimeからディスパッチされるエラーイベントを処理するイベントハンドラーを作成します。

通常、アプリケーションはエラーを検出すると、任意の数のクリーンアップタスクを実行します。 その後、エラーをユーザに通知し、問題を解決するためのオプションを提供します。

```
private function drmErrorEventHandler(event:DRMErrorEvent):void {  
    trace(event.toString());  
} 
```

