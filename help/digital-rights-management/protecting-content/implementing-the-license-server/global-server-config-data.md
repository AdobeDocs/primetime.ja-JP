---
seo-title: グローバルサーバ設定データ
title: グローバルサーバ設定データ
uuid: a1557b3e-9a08-4623-a62d-8ebc308eae15
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# グローバルサーバ設定データ{#global-server-configuration-data}

ライセンスサーバーで使用される設定に加えて、は、ライ `HandlerConfiguration` センスの適用方法を制御するためにクライアントに送信できる設定情報を保存します。 これは、クラスを作成して呼び出す `ServerConfigData` ことで行われま `HandlerConfiguration.setServerConfigData()`す。 これらの設定は、このライセンスサーバーが発行したライセンスにのみ適用されます。

クロックのウィンドバック許容値は、クライアントがライセンスを強制する方法を制御するためにライセンスサーバーが設定できる1つのプロパティです。 デフォルトでは、ユーザーはライセンスを無効にすることなく、コンピューターのクロックを4時間戻すことができます。 ライセンスサーバーのオペレータが別の設定を使用する場合、新しい値をクラスに設定でき `ServerConfigData` ます。 これらの設定の値を変更する場合は、を呼び出してバージョン番号を増やしてくださ `setVersion()`い。 新しい値は、クライアント上のバージョンが現在のバージョンより古い場合にのみクライアントに送信さ `ServerConfigData` れます。
