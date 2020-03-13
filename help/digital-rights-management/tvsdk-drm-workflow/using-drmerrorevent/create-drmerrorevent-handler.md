---
seo-title: DRMErrorEventハンドラーの作成
title: DRMErrorEventハンドラーの作成
uuid: dde660fc-6899-47d4-97d4-46acda2db262
translation-type: tm+mt
source-git-commit: 5749142d42f7d7b36c96592955d1f71f6a7956fc

---


# DRMErrorEventハンドラーの作成{#create-a-drmerrorevent-handler}

保護されたコンテンツの再生中にエラーが発生した場合にPrimetimeからディスパッチされたエラーイベントを処理するイベントハンドラーを作成します。

通常、アプリケーションでエラーが発生した場合は、任意の数のクリーンアップタスクが実行されます。 次に、エラーをユーザに通知し、問題を解決するためのオプションを提供します。

```
private function drmErrorEventHandler(event:DRMErrorEvent):void {  
    trace(event.toString());  
} 
```

