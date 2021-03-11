---
title: ライセンスチェーン
description: ライセンスチェーン
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---


# ライセンスチェーン{#license-chaining}

ライセンスの生成に使用されるポリシーがライセンスのチェーンをサポートしている場合、サーバーはリーフライセンス、ルートライセンス、またはその両方を発行するかどうかを決定する必要があります。 ポリシーがサポートするライセンスの種類を確認するには、`Policy.getLicenseChainType()`を使用するか、`Policy.getRootLicenseId()`を呼び出して、ポリシーにルートライセンスがあるかどうかを確認します。 Adobeアクセス2.0ライセンスチェーンでは、通常、サーバーは、特定のマシンのライセンスとルートライセンスを最初に要求したときにリーフライセンスを発行します。 指定したポリシーに対するリーフライセンスが既にマシンに存在するかどうかを確認するには、`LicenseRequestMessage.clientHasLeafForPolicy()`を呼び出します。
