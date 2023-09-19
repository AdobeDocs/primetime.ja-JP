---
title: グローバルサーバー設定データ
description: グローバルサーバー設定データ
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---

# グローバルサーバー設定データ{#global-server-configuration-data}

ライセンスサーバが使用する設定に加えて、 `HandlerConfiguration` は、ライセンスの適用方法を制御するためにクライアントに送信できる構成情報を格納します。 これは、 `ServerConfigData` クラスと呼び出し `HandlerConfiguration.setServerConfigData()` （これらの設定は、このライセンスサーバーが発行したライセンスにのみ適用されます）。 クロック・ウィンドバックの許容値は、ライセンス・サーバによって設定され、クライアントがライセンスを強制する方法を制御する 1 つのプロパティです。 デフォルトでは、ユーザーはライセンスを無効にすることなく、4 時間前にマシンクロックを設定できます。 ライセンスサーバーのオペレーターが別の設定を使用する場合は、新しい値を `ServerConfigData` クラス。 これらの設定の値を変更する場合は、必ず `setVersion()`. 新しい値は、クライアント上のバージョンが現在のバージョンより小さい場合にのみクライアントに送信されます `ServerConfigData` バージョン。
