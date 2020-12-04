---
seo-title: DRMErrorEventハンドラーの作成
title: DRMErrorEventハンドラーの作成
uuid: dde660fc-6899-47d4-97d4-46acda2db262
translation-type: tm+mt
source-git-commit: 5749142d42f7d7b36c96592955d1f71f6a7956fc
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

