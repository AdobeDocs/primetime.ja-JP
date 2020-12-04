---
seo-title: グローバルサーバー設定データ
title: グローバルサーバー設定データ
uuid: a1557b3e-9a08-4623-a62d-8ebc308eae15
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---


# グローバル・サーバ構成データ{#global-server-configuration-data}

ライセンスサーバーが使用する構成に加えて、`HandlerConfiguration`には、ライセンスの適用方法を制御するためにクライアントに送信できる構成情報が格納されます。 これは、`ServerConfigData`クラスを作成し、`HandlerConfiguration.setServerConfigData()`を呼び出すことで行います。 これらの設定は、このライセンスサーバーが発行したライセンスにのみ適用されます。

クロックウィンドバック許容値は、ライセンスサーバーがクライアントによるライセンスの強制方法を制御するために設定できる1つのプロパティです。 デフォルトでは、ユーザーはライセンスを無効にすることなく、コンピューターのクロックを4時間戻すことができます。 ライセンスサーバーの演算子が別の設定を使用したい場合は、新しい値を`ServerConfigData`クラスに設定できます。 これらの設定の値を変更する場合は、必ず`setVersion()`を呼び出してバージョン番号を増やしてください。 新しい値は、クライアント上のバージョンが現在の`ServerConfigData`バージョンより古い場合にのみクライアントに送信されます。
