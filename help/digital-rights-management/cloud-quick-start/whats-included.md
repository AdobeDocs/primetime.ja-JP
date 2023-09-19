---
description: Adobeは、独自の Primetime DRM ライセンスサーバーの開発と維持を希望しないAdobe Primetime DRM のお客様に Cloud DRM サービスを提供します。 このサービスを利用することで、DRM ライセンスの発行に関する運用と開発の複雑さを軽減できます。 Primetime Cloud DRM は、iOS、Android、デスクトップ、Xbox360 など、Primetime ブラウザー TVSDK 対応のビデオアプリケーションを実行できるすべてのデバイスに DRM ライセンスを発行できます。 この DRM サービスは、24/7稼動時間でAdobeによってホストおよび維持されます。
title: 背景
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# 背景 {#background}

Adobeは、独自の Primetime DRM ライセンスサーバーの開発と維持を希望しないAdobe Primetime DRM のお客様に Cloud DRM サービスを提供します。 このサービスを利用することで、DRM ライセンスの発行に関する運用と開発の複雑さを軽減できます。 Primetime Cloud DRM は、iOS、Android、デスクトップ、Xbox360 など、Primetime ブラウザー TVSDK 対応のビデオアプリケーションを実行できるすべてのデバイスに DRM ライセンスを発行できます。 この DRM サービスは、24/7稼動時間でAdobeによってホストおよび維持されます。

>[!NOTE]
>
>Adobe Primetime DRM は、以前はAdobeアクセスと呼ばれていましたが、それ以前はFlash Accessでした。

## Primetime Cloud DRM に含まれるもの {#section_788D0DD5F6DB41678FD87CFBD21B25FD}

* カスタム認証/資格付与モジュールおよびコンテンツのカスタム認証をおこなう方法に関する説明です。 詳しくは、 [!DNL Custom Authentication Entitlement] ディレクトリ。
* Cloud DRM 固有のライセンスサーバー証明書 ( [!DNL .pem/.cer/.der])

* Cloud DRM 固有のライセンスサーバートランスポート証明書 ( [!DNL .pem/.cer/.der])

* Primetime Java Offline Packager
* パッケージ化用のサンプル DRM ポリシー

   * **policy_24hr**  — ディスク上のキャッシュを 24 時間ライセンスします。 24 時間後に、コンテンツを表示するには新しいライセンスを取得する必要があります。 このキットの他のすべてのポリシーには、24 時間のライセンスキャッシュも含まれます。
   * **policy_ios_remotekeyserver** - iOSデバイスでは、DRM ライセンスは Cloud DRM から取得されます。 さらに、クライアントは Cloud DRM からすべての AES 復号化キーを取得します。 正常終了のiOSデバイスでは再生が許可されていません。

   * **policy_ios_localkeyserver** - iOSデバイスでは、DRM ライセンスは Cloud DRM から取得されます。 さらに、クライアントは、Cloud DRM ではなく、ローカル HTTP サーバーからすべての HLS AES 復号鍵を取得します。 正常終了のiOSデバイスでは再生が許可されていません。

   * **policy_adobePass**  — クライアントは、最初に ( 旧称Adobe Pass) で認証する必要があります。認証しないと、ライセンスが拒否されます。

* Adobeポリシーマネージャーツールを使用して追加の DRM ポリシーを作成する
* パッケージ化に使用するサンプルビデオコンテンツ
