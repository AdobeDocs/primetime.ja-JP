---
seo-title: BEESサーバーでのSSLの設定
title: BEESサーバーでのSSLの設定
uuid: 041a106e-8b21-4018-815d-b7ea48c3de03
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5

---


# BEESサーバーでのSSLの設定 {#configure-ssl-on-your-bees-server}

1. このソフトウェアを提供したアドビの担当者に、サーバーSSL証明書を提供します。

   証明書は、信頼できる証明書としてPrimetime Cloud DRM Trust Storeに追加されます。
1. SSL接続のクライアント認証を有効にするには（このバージョンでは無効）:
   1. クライアント `[!DNL clouddrm-transport.cer]` 認証に使 `[!DNL AdobeFlashAccessIntermediateCA.cer]` 用するTrust Storeに証明書と証明書を追加します。
   1. SSL設定でクライアント認証を有効にします。
