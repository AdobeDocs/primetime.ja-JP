---
title: BEES サーバーでの SSL の設定
description: BEES サーバーでの SSL の設定
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 0%

---

# BEES サーバーでの SSL の設定 {#configure-ssl-on-your-bees-server}

1. このソフトウェアを提供したAdobeの連絡先に、サーバーの SSL 証明書を提供します。

   証明書は、信頼された証明書として Primetime Cloud DRM トラストストアに追加されます。
1. SSL 接続のクライアント認証を有効にするには（このバージョンでは無効）:
   1. 次を追加： `[!DNL clouddrm-transport.cer]` および `[!DNL AdobeFlashAccessIntermediateCA.cer]` クライアント認証に使用される Trust Store への証明書。
   1. SSL 設定でクライアント認証を有効にします。
