---
title: ローカルに生成されたCRLを使用する
description: ローカルに生成されたCRLを使用する
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---


# ローカルに生成されたCRLを使用{#consume-locally-generated-crls}

ローカルに生成された証明書失効リスト(CRL)およびポリシー更新リストを使用するには、AdobeアクセスAPIを使用して署名を検証します。 APIは、リストが改ざんされていないこと、および正しいLicense Serverによって署名されていることを確認します。

* RevocationListをAPIに提供する前に、`RevocationList.verifySignature`を呼び出して署名を確認してください。

   詳しくは、『*AdobeアクセスAPIリファレンス*』の`RevocationListFactory`を参照してください。

* `PolicyUpdateList.verifySignature`を呼び出して署名を確認してから、APIに`PolicyUpdateList`を提供します。

   詳しくは、『*AdobeアクセスAPIリファレンス*』の`PolicyUpdateList`を参照してください。

