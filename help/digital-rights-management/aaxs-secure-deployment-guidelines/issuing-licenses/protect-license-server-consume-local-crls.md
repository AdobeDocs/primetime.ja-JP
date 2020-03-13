---
seo-title: ローカルに生成されたCRLを使用する
title: ローカルに生成されたCRLを使用する
uuid: 5a4519b8-6dbd-4921-9048-6c9f67aae18d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# ローカルに生成されたCRLを使用する{#consume-locally-generated-crls}

ローカルに生成された証明書失効リスト(CRL)とポリシー更新リストを使用するには、Adobe Access APIを使用して署名を検証します。 APIは、リストが改ざんされていないこと、および正しいLicense Serverによって署名されていることを確認します。

* RevocationListをAPI `RevocationList.verifySignature` に提供する前に、署名を確認する呼び出し。

   詳しくは、『 `RevocationListFactory` Adobe Access APIリファレンス』の *を参照*&#x200B;してください。

* APIを提 `PolicyUpdateList.verifySignature`供する前に、署名を確認するた `PolicyUpdateList` めの呼び出し。

   詳しくは、『 `PolicyUpdateList` Adobe Access APIリファレンス』の *を参照*&#x200B;してください。

