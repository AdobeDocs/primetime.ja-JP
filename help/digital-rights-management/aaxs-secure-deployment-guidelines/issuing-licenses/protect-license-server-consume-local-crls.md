---
seo-title: ローカルに生成されたCRLを使用する
title: ローカルに生成されたCRLを使用する
uuid: 5a4519b8-6dbd-4921-9048-6c9f67aae18d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
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

