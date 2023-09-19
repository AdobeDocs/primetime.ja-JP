---
title: ローカルに生成された CRL を使用
description: ローカルに生成された CRL を使用
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---

# ローカルに生成された CRL を使用{#consume-locally-generated-crls}

ローカルに生成された証明書失効リスト (CRL) とポリシー更新リストを使用するには、Adobeアクセス API を使用して署名を検証します。 API は、リストが改ざんされていないこと、および正しいライセンスサーバーによって署名されていることを確認します。

* 通話 `RevocationList.verifySignature` を使用して、API に RevocationList を提供する前に署名を確認します。

  詳しくは、 `RevocationListFactory` （内） *Adobeアクセス API リファレンス*.

* 通話 `PolicyUpdateList.verifySignature`署名を確認してから `PolicyUpdateList` を任意の API に追加します。

  詳しくは、 `PolicyUpdateList` （内） *Adobeアクセス API リファレンス*.
