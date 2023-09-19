---
title: 拡張ライセンスチェーニング
description: 拡張ライセンスチェーニング
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---

# 拡張ライセンスチェーニング {#enhanced-license-chaining}

ライセンスチェーニングをサポートするライセンスを生成するために DRM ポリシーを使用する場合、サーバーは Leaf ライセンス、Root ライセンス、またはその両方を発行するかどうかを決定する必要があります。 DRM ポリシーがサポートするライセンスの種類を決定する場合は、 `Policy.getLicenseChainType()`またはを呼び出す `Policy.getRootLicenseId()` をクリックして、DRM ポリシーにルートライセンスがあるかどうかを確認します。 Adobe Primetime DRM 2.0 ライセンスチェーンでは、通常、ユーザーが特定のマシンのライセンスとその後のルートライセンスを初めて要求したときに、サーバーがリーフライセンスを発行します。 指定したポリシーのリーフライセンスがマシンに既に存在するかどうかを判断するには、を呼び出す必要があります。 `LicenseRequestMessage.clientHasLeafForPolicy()`.

Adobe Primetime DRM 3.0 の拡張ライセンスチェーニングでは、ユーザーが特定のマシンのライセンスを初めてリクエストする際に、リーフとルートの両方を発行することをお勧めします。 ユーザーが既に Root ライセンスを持っている場合、サーバはリーフ ( `LicenseRequestMessage.clientHasEnhancedRootForPolicy()` をクリックして、クライアントに既に 3.0 拡張ルートがあるかどうかを判断します。 その後のライセンス要求では、クライアントはすでにリーフとルートを持っていることを示すので、サーバは新しいルートライセンスを発行する必要があります。 拡張ライセンスチェーニングを使用する場合、 `setRootKeyRetrievalInfo()` は、DRM ポリシーのルート暗号化キーを復号化するために必要な資格情報を提供するために呼び出す必要があります。

>[!NOTE]
>
>ポリシーが 3.0 拡張ライセンスチェーンをサポートしているが、クライアントが Primetime DRM 2.0 の場合、サーバーは 2.0 オリジナルのチェーンされたライセンスを発行します。 クライアントのバージョンを確認するには、 `LicenseRequestMessage.getClientVersion()`.
