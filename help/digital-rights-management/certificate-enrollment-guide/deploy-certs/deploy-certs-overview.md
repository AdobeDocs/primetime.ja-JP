---
title: 証明書のデプロイの概要
description: 証明書のデプロイの概要
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# 概要 {#deploy-certificates-overview}

証明書をAdobe Primetime DRM プロパティファイルに追加するには、PKCS#7 ファイルを秘密鍵で PFX ファイルに変換し、PEM ファイルまたは DER ファイルを生成します。

* 証明書（証明書と秘密鍵）が必要な場合、Primetime DRM コマンドラインツールおよびAdobeHTTP Dynamic Streamingパッケージャーには PFX ファイルが必要です。 SDK、リファレンス実装、および保護されたストリーミング用 Primetime DRM サーバーは、PFX ファイルを受け取ることができ、HSM に保存された秘密鍵証明書を使用することもできます。
* 証明書のみが必要な場合、ほとんどの Primetime DRM コンポーネントでは、PEM ファイル、DER ファイル、または HSM 上の証明書を使用できます。 AdobeHTTP Dynamic Streamingパッケージャは、証明書の DER ファイルのみを受け付けます。
