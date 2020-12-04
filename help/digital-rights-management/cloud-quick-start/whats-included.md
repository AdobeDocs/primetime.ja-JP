---
description: Adobeは、独自のPrimetime DRMライセンスサーバーの開発と保守を希望しないAdobe PrimetimeDRMのお客様に対して、Cloud DRMサービスを提供します。 このサービスを利用することで、DRMライセンスの発行に関連する運用と開発の複雑さを軽減できます。 Primetime Cloud DRMは、PrimetimeブラウザーTVSDK対応のビデオアプリケーション（iOS、Android、デスクトップ、Xbox360など）を実行できるすべてのデバイスにDRMライセンスを発行できます。 このDRMサービスは、24時間365日稼働状態で、Adobeがホストし、保守します。
seo-description: Adobeは、独自のPrimetime DRMライセンスサーバーの開発と保守を希望しないAdobe PrimetimeDRMのお客様に対して、Cloud DRMサービスを提供します。 このサービスを利用することで、DRMライセンスの発行に関連する運用と開発の複雑さを軽減できます。 Primetime Cloud DRMは、PrimetimeブラウザーTVSDK対応のビデオアプリケーション（iOS、Android、デスクトップ、Xbox360など）を実行できるすべてのデバイスにDRMライセンスを発行できます。 このDRMサービスは、24時間365日稼働状態で、Adobeがホストし、保守します。
seo-title: 背景
title: 背景
uuid: 11a5b9ea-ebd2-47e0-b078-af2a3e1f7bf6
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---


# 背景{#background}

Adobeは、独自のPrimetime DRMライセンスサーバーの開発と保守を希望しないAdobe PrimetimeDRMのお客様に対して、Cloud DRMサービスを提供します。 このサービスを利用することで、DRMライセンスの発行に関連する運用と開発の複雑さを軽減できます。 Primetime Cloud DRMは、PrimetimeブラウザーTVSDK対応のビデオアプリケーション（iOS、Android、デスクトップ、Xbox360など）を実行できるすべてのデバイスにDRMライセンスを発行できます。 このDRMサービスは、24時間365日稼働状態で、Adobeがホストし、保守します。

>[!NOTE]
>
>Adobe PrimetimeDRMは、以前はAdobeアクセスと呼ばれていましたが、それ以前はFlash Accessと呼ばれていました。

## Primetime Cloud DRMに含まれるもの{#section_788D0DD5F6DB41678FD87CFBD21B25FD}

* カスタム認証/エンタイトルメントモジュールと、コンテンツのカスタム認証を関与させる方法に関する手順を説明します。 詳細なドキュメントについては、[!DNL Custom Authentication Entitlement]ディレクトリを参照してください。
* Cloud DRM固有のライセンスサーバー証明書([!DNL .pem/.cer/.der])

* Cloud DRM固有のライセンスサーバートランスポート証明書([!DNL .pem/.cer/.der])

* Primetime Java Offline Packager
* パッケージ化のためのサンプルDRMポリシー

   * **policy_24hr** - 24時間ディスク上のキャッシュをライセンスします。24時間後に、コンテンツを表示するために新しいライセンスを取得する必要があります。 このキットに含まれる他のポリシーもすべて、24時間のライセンスキャッシュを持ちます。
   * **policy_ios_remotekeyserver** - iOSデバイスでは、DRMライセンスはCloud DRMから取得されます。さらに、クライアントはCloud DRMからすべてのAES復号キーを取得します。 正常終了したiOSデバイスでは再生が許可されません。

   * **policy_ios_localkeyserver** - iOSデバイスでは、DRMライセンスはCloud DRMから取得されます。さらに、クライアントは、Cloud DRMではなく、ローカルのHTTPサーバーからすべてのHLS AES復号キーを取得します。 正常終了したiOSデバイスでは再生が許可されません。

   * **policy_adobePass**  — クライアントは、(以前のAdobe Passと呼ばれていた)最初の認証が必要です。認証が必要でないと、ライセンスが拒否されます。

* Adobeポリシーマネージャーツールを使用した追加のDRMポリシーの作成
* パッケージ化に使用するビデオコンテンツのサンプル

