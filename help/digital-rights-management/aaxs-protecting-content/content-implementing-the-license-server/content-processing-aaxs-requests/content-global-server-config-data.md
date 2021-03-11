---
title: グローバルサーバー設定データ
description: グローバルサーバー設定データ
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---


# グローバル・サーバ構成データ{#global-server-configuration-data}

ライセンスサーバーが使用する構成に加えて、`HandlerConfiguration`には、ライセンスの適用方法を制御するためにクライアントに送信できる構成情報が格納されます。 これは、`ServerConfigData`クラスを作成し、`HandlerConfiguration.setServerConfigData()`を呼び出すことで行われます（これらの設定は、このライセンスサーバーが発行したライセンスにのみ適用されます）。 クロックウィンドバック許容値は、ライセンスサーバーがクライアントによるライセンスの強制方法を制御するために設定できる1つのプロパティです。 デフォルトでは、ユーザーはライセンスを無効にすることなく、コンピューターのクロックを4時間戻すことができます。 ライセンスサーバーの演算子が別の設定を使用したい場合は、新しい値を`ServerConfigData`クラスに設定できます。 これらの設定の値を変更する場合は、必ず`setVersion()`を呼び出してバージョン番号を増やしてください。 新しい値は、クライアント上のバージョンが現在の`ServerConfigData`バージョンよりも小さい場合にのみクライアントに送信されます。
