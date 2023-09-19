---
title: 帯域外ライセンスの概要
description: 帯域外ライセンスの概要
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---

# 帯域外ライセンス {#out-of-band-licenses}

また、ライセンスをディスクに保存し、 `storeVoucher()` メソッド。

Primetime で暗号化されたビデオを再生するには、それぞれのランタイムがそのビデオのライセンスを取得する必要があります。 ライセンスには、ビデオの復号キーが含まれ、顧客がデプロイした Primetime DRM ライセンスサーバーによって生成されます。

通常、ランタイムは、ビデオの DRM メタデータ ( `DRMContentData` クラス ) です。 アプリケーションは、このライセンスリクエストをトリガーするには、 `DRMManager.loadVoucher()` メソッド。

`DRMManager.storeVoucher()` を使用すると、アプリケーションは帯域外で取得したライセンスを送信できます。 その後、ランタイムは、ライセンスリクエストプロセスをスキップし、転送されたライセンスを使用して、暗号化されたビデオを再生できます。 ライセンスは、帯域外で取得する前に、Primetime DRM ライセンスサーバーで生成する必要があります。 ただし、Primetime DRM ライセンスサーバーではなく、任意の HTTP サーバー上にライセンスをホストするオプションが用意されています。

`DRMManager.storeVoucher()` は、複数のデバイス間でのライセンス共有をサポートするためにも使用されます。 Primetime DRM 3.0 以降、この機能は「デバイスドメインサポート」と呼ばれます。 この使用例がデプロイメントでサポートされている場合は、 `DRMManager.addToDeviceGroup()` メソッド。 特定のコンテンツに対して有効なドメインバインドライセンスを持つマシンがある場合、アプリケーションは、 `DRMVoucher.toByteArray()` メソッドと、他のコンピューターでは、 `DRMManager.storeVoucher()` メソッド。

## デバイスの登録について {#about-device-registration}

作成時には、すべての Primetime DRM ライセンスをエンドエンティティにバインドする必要があります。 バインディングは、特定のエンティティに対して、ライセンスの消費を許可する暗号化プロセスです。 これは、任意のデバイスで使用できる「フローティングライセンス」を防ぐために必要です。 Primetime DRM で「事前生成」ライセンスを使用する場合、これは、事前生成されたこれらのライセンスの「ターゲット」を事前に知っておく必要があることを意味します。 Primetime DRM では、これを「デバイスの登録」と呼びます。

## デバイスの登録 {#register-a-device}

次のタスクを実行したとします。

* Primetime DRM Server SDK が設定されている。
* 事前に生成されたライセンスを発行するための HTTP サーバーが設定されている。
* 保護されたコンテンツを表示する Primetime アプリケーションを作成しました。

 デバイス登録フェーズでは、次の操作をおこないます。

1. ランダムに生成された ID が作成されます。
1. アプリケーションがを呼び出します。 `DRMManager.authenticate()` メソッド。 アプリケーションでは、認証リクエストにランダムに生成された ID を含める必要があります。 例えば、ユーザー名フィールドに ID を含めます。
1. 手順 2 で説明した操作により、Primetime DRM がお客様のサーバーに認証リクエストを送信します。 この要求には、デバイス証明書が含まれます。
   1. サーバーは、要求からデバイス証明書と生成された ID を抽出し、保存します。
   1. 顧客サブシステムは、このデバイス証明書のライセンスを事前に生成して保存し、生成された ID に関連付ける方法でアクセス権を付与します。.
1. サーバーは、「成功」メッセージを使用してリクエストに応答します。
1. 生成された ID はアプリケーションによって保存されます。

デバイスの登録後、アプリケーションは、前のスキームでデバイス ID を使用した場合と同じ方法で、生成された ID を使用します。
1. 生成された ID が見つかります。
1. 生成された ID が見つかった場合、アプリケーションは生成された ID を使用して、事前に生成されたライセンスをダウンロードします。 アプリケーションは、を使用して使用するために、Primetime DRM クライアントにライセンスを送信します。 `DRMManager.storeVoucher()` メソッド。.
1. 生成された ID が見つからない場合、アプリケーションはデバイス登録手順を実行します。

## DRM の工場出荷時リセット {#drm-factory-reset}

デバイスのユーザーが DRM ファクトリリセットオプションを呼び出すと、デバイス証明書は消去されます。 保護されたコンテンツの再生を続行するには、アプリケーションがデバイス登録手順を再度実行する必要があります。 古いデバイス ID に対してライセンスが暗号化されているので、アプリケーションが古い事前生成ライセンスを送信した場合、Primetime DRM クライアントはそのライセンスを拒否します。

* FlashAPI: [DRMManager.resetDRMVouchers()](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/drm/DRMManager.html#resetDRMVouchers()) - （回復不能な特定の DRM エラーコードに対する応答でのみ呼び出すことができます。）
* iOS API: [DRMManager resetDRM](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a0dd6c9662428583196e0419d3ea69446)
* Android API: [DRMManager.resetDRM()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#resetDRM(com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMOperationCompleteCallback))
