---
title: 拡張ライセンスチェーニング
description: 拡張ライセンスチェーニング
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---

# 拡張ライセンスチェーニング {#enhanced-license-chaining}

Adobeアクセス 3.0 で拡張されたライセンスチェーニングを使用する場合、ユーザーが特定のマシンのライセンスを初めてリクエストする際に、リーフとルートの両方を発行することをお勧めします。 ユーザーが既に Root ライセンスを持っている場合、サーバはリーフ ( `LicenseRequestMessage.clientHasEnhancedRootForPolicy()` をクリックして、クライアントに既に 3.0 拡張ルートがあるかどうかを判断します。 以降のライセンス要求では、クライアントはすでにリーフとルートを持っていることを示すので、サーバは新しいルートライセンスを発行する必要があります。 拡張ライセンスチェーニングを使用する場合、 `setRootKeyRetrievalInfo()` は、ポリシーのルート暗号化キーを復号化するために必要な資格情報を提供するために呼び出す必要があります。

>[!NOTE]
>
>ポリシーが 3.0 拡張ライセンスチェーンをサポートしているが、クライアントがAdobeアクセス 2.0 の場合、サーバーは 2.0 オリジナルのチェーンされたライセンスを発行します。 クライアントのバージョンを確認するには、 LicenseRequestMessage.getClientVersion() を使用します。
