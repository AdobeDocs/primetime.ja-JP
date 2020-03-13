---
seo-title: 証明書のデプロイの概要
title: 証明書のデプロイの概要
uuid: e6413f9f-69a5-4881-bb13-47a80cf32a48
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5

---


# 概要 {#deploy-certificates-overview}

証明書をAdobe Primetime DRMプロパティファイルに追加するには、秘密鍵を使用してPKCS#7ファイルをPFXファイルに変換し、PEMファイルまたはDERファイルを生成します。

* 秘密鍵証明書（証明書と秘密鍵）が必要な場合、Primetime DRMコマンドラインツールとAdobe HTTP Dynamic Streaming PackagerにはPFXファイルが必要です。 SDK、参照実装およびPrimetime DRM Server for Protected Streamingは、PFXファイルを受け入れ、HSMに保存された秘密鍵証明書を使用することもできます。
* 証明書のみが必要な場合、ほとんどのPrimetime DRMコンポーネントは、PEMファイル、DERファイル、またはHSM上の証明書を使用できます。 Adobe HTTP Dynamic Streaming Packagerは、証明書にDERファイルのみを受け付けます。