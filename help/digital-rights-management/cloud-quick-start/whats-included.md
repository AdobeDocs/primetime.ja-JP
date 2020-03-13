---
description: アドビは、Adobe Primetime DRMのお客様に対して、独自のPrimetime DRMライセンスサーバーの開発と維持を希望しないCloud DRMサービスを提供しています。 このサービスを利用することで、DRMライセンスの発行に関する運用と開発の複雑さを軽減できます。 Primetime Cloud DRMは、Primetime Browser TVSDK対応のビデオアプリケーション（iOS、Android、デスクトップ、Xbox360など）を実行できるすべてのデバイスに対してDRMライセンスを発行できます。 このDRMサービスは、24時間365日稼働状態でアドビによってホストされ、管理されます。
seo-description: アドビは、Adobe Primetime DRMのお客様に対して、独自のPrimetime DRMライセンスサーバーの開発と維持を希望しないCloud DRMサービスを提供しています。 このサービスを利用することで、DRMライセンスの発行に関する運用と開発の複雑さを軽減できます。 Primetime Cloud DRMは、Primetime Browser TVSDK対応のビデオアプリケーション（iOS、Android、デスクトップ、Xbox360など）を実行できるすべてのデバイスに対してDRMライセンスを発行できます。 このDRMサービスは、24時間365日稼働状態でアドビによってホストされ、管理されます。
seo-title: 背景
title: 背景
uuid: 11a5b9ea-ebd2-47e0-b078-af2a3e1f7bf6
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# 背景 {#background}

アドビは、Adobe Primetime DRMのお客様に対して、独自のPrimetime DRMライセンスサーバーの開発と維持を希望しないCloud DRMサービスを提供しています。 このサービスを利用することで、DRMライセンスの発行に関する運用と開発の複雑さを軽減できます。 Primetime Cloud DRMは、Primetime Browser TVSDK対応のビデオアプリケーション（iOS、Android、デスクトップ、Xbox360など）を実行できるすべてのデバイスに対してDRMライセンスを発行できます。 このDRMサービスは、24時間365日稼働状態でアドビによってホストされ、管理されます。

>[!NOTE]
>
>Adobe Primetime DRMは、以前はAdobe Accessと呼ばれていましたが、それ以前はFlash Accessでした。

## Primetime Cloud DRMに含まれるもの {#section_788D0DD5F6DB41678FD87CFBD21B25FD}

* カスタム認証/エンタイトルメントモジュールと、コンテンツのカスタム認証を行う方法に関する説明です。 詳細なドキュメントについては、ディレクトリを参照してく [!DNL Custom Authentication Entitlement] ださい。
* Cloud DRM固有のライセンスサーバー証明書( [!DNL .pem/.cer/.der])

* Cloud DRM固有のライセンスサーバートランスポート証明書( [!DNL .pem/.cer/.der])

* Primetime Java Offline Packager
* パッケージ化のDRMポリシーの例

   * **policy_24hr** - 24時間、ディスク上のライセンスキャッシュ。 24時間後に、コンテンツを表示するには新しいライセンスを取得する必要があります。 このキットの他のポリシーもすべて、24時間のライセンスキャッシュを使用します。
   * **policy_ios_remotekeyserver** - iOSデバイスでは、DRMライセンスはCloud DRMから取得されます。 さらに、クライアントはCloud DRMからすべてのAES復号キーを取得します。 正常終了したiOSデバイスでの再生は許可されません。

   * **policy_ios_localkeyserver** - iOSデバイスでは、DRMライセンスはCloud DRMから取得されます。 さらに、クライアントは、Cloud DRMではなく、ローカルHTTPサーバーからすべてのHLS AES復号キーを取得します。 正常終了したiOSデバイスでの再生は許可されません。

   * **policy_adobePass** — クライアントは最初に認証が必要（旧称Adobe Pass）です。認証が必要でない場合、ライセンスが拒否されます。

* 追加のDRMポリシーを作成するAdobe Policy Managerツール
* パッケージ化に使用するビデオコンテンツのサンプル

