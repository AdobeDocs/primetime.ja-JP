---
title: ライセンスチェーニング
description: ライセンスチェーニング
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---

# ライセンスチェーニング{#license-chaining}

ライセンスの生成に使用するポリシーがライセンスチェーニングをサポートする場合は、サーバーが Leaf ライセンス、Root ライセンス、またはその両方を発行するかどうかを決定する必要があります。 ポリシーがサポートするライセンスチェーンの種類を判断するには、 `Policy.getLicenseChainType()`またはを呼び出す `Policy.getRootLicenseId()` ポリシーにルートライセンスがあるかどうかを確認します。 Adobeアクセス 2.0 ライセンスチェーニングでは、通常、ユーザーが特定のマシンのライセンスを初めて要求したときに、サーバがリーフライセンスを発行し、その後、ルートライセンスを発行します。 指定したポリシーのリーフライセンスがマシンに既に存在するかどうかを確認するには、を呼び出します。 `LicenseRequestMessage.clientHasLeafForPolicy()`.
