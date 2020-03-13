---
seo-title: ライセンスのチェーン
title: ライセンスのチェーン
uuid: dcc12663-ef9e-4c73-b837-66fcec39358b
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# ライセンスのチェーン{#license-chaining}

ライセンスの生成に使用されるポリシーがライセンスのチェーンをサポートしている場合、サーバーはリーフライセンス、ルートライセンス、またはその両方を発行するかどうかを決定する必要があります。 ポリシーがサポートするライセンスチェーンの種類を判断するには、を使用するか、 `Policy.getLicenseChainType()`またはを呼び出して、ポリシー `Policy.getRootLicenseId()` にルートライセンスがあるかどうかを判断します。 Adobe Access 2.0のライセンスチェーンでは、通常、ユーザーが特定のマシンのライセンスとその後のルートライセンスを初めて要求したときに、サーバーはリーフライセンスを発行します。 指定したポリシーのリーフライセンスがコンピューターに既に存在するかどうかを確認するには、を呼び出しま `LicenseRequestMessage.clientHasLeafForPolicy()`す。
