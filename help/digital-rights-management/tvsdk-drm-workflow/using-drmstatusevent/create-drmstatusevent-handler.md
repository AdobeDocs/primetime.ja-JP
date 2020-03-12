---
seo-title: DRMStatusEventハンドラーの作成
title: DRMStatusEventハンドラーの作成
uuid: 64f539d9-344c-4372-88b8-c8d098af9dd8
translation-type: tm+mt
source-git-commit: 5749142d42f7d7b36c96592955d1f71f6a7956fc

---


# DRMStatusEventハンドラーの作成{#create-a-drmstatusevent-handler}

次の例では、イベントの発生元のPrimetimeオブジェクトのDRMコンテンツのステータス情報を出力するイベントハンドラーを作成します。

保護されたコンテンツを指すイベントハンドラーをPrimetimeオブジェクトに追加します。

```
function drmStatusEventHandler(event:DRMStatusEvent):void { trace(event); } 
```

