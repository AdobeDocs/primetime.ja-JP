---
seo-title: BEESサーバーでのSSLの設定
title: BEESサーバーでのSSLの設定
uuid: 041a106e-8b21-4018-815d-b7ea48c3de03
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5
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
