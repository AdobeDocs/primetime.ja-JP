---
seo-title: 証明書の展開の概要
title: 証明書の展開の概要
uuid: e6413f9f-69a5-4881-bb13-47a80cf32a48
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---


# 概要{#deploy-certificates-overview}

証明書をAdobe PrimetimeDRMプロパティファイルに追加するには、PKCS#7ファイルを秘密鍵を使用してPFXファイルに変換し、PEMファイルまたはDERファイルを生成します。

* 秘密鍵証明書（証明書および秘密鍵）が必要な場合、Primetime DRMコマンドラインツールおよびAdobeHTTP Dynamic StreamingパッケージャーにはPFXファイルが必要です。 SDK、リファレンス実装、およびPrimetime DRM Server for Protected Streamingは、PFXファイルを受け入れることができ、HSMに保存された秘密鍵証明書も使用できます。
* 証明書のみが必要な場合、ほとんどのPrimetime DRMコンポーネントは、PEMファイル、DERファイル、またはHSM上の証明書を使用できます。 AdobeHTTP Dynamic Streamingパッケージャーは、証明書にDERファイルのみを受け付けます。