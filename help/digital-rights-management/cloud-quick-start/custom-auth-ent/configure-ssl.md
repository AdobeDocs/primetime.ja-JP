---
title: BEESサーバーでのSSLの設定
description: BEESサーバーでのSSLの設定
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 0%

---


# BEESサーバーでSSLを設定{#configure-ssl-on-your-bees-server}

1. このソフトウェアを提供したAdobeの担当者に、サーバーSSL証明書を提供してください。

   証明書は、信頼できる証明書としてPrimetime Cloud DRM Trust Storeに追加されます。
1. SSL接続のクライアント認証を有効にするには（このバージョンでは無効）:
   1. ク追加ライアント認証に使用するTrust Storeへの`[!DNL clouddrm-transport.cer]`証明書と`[!DNL AdobeFlashAccessIntermediateCA.cer]`証明書。
   1. SSL設定でクライアント認証を有効にします。
