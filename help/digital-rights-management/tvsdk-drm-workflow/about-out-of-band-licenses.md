---
title: 帯域外ライセンスの概要
description: 帯域外ライセンスの概要
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---


# 帯域外ライセンス{#out-of-band-licenses}

`storeVoucher()`メソッドを使用してディスクとメモリにライセンスを格納することで、（Primetime DRMライセンスサーバーに接続せずに）ライセンスを帯域外で取得することもできます。

暗号化されたビデオをPrimetimeで再生するには、それぞれのランタイムがそのビデオのライセンスを取得する必要があります。 ライセンスにはビデオの復号化キーが含まれ、顧客がデプロイしたPrimetime DRMライセンスサーバーによって生成されます。

通常、ランタイムは、ビデオのDRMメタデータ（`DRMContentData`クラス）に示されているPrimetime DRMライセンスサーバーにライセンス要求を送信することで、このライセンスを取得します。 アプリケーションは、`DRMManager.loadVoucher()`メソッドを呼び出すことで、このライセンス要求をトリガーできます。

`DRMManager.storeVoucher()` アプリケーションが帯域外で取得したライセンスを送信できるようにします。その後、ランタイムはライセンス要求プロセスをスキップし、転送されたライセンスを使用して暗号化されたビデオを再生できます。 ライセンスを帯域外で取得するには、Primetime DRMライセンスサーバーでライセンスを生成する必要があります。 ただし、Primetime DRMライセンスサーバーではなく、任意のHTTPサーバーでライセンスをホストするオプションがあります。

`DRMManager.storeVoucher()` は、複数のデバイス間でのライセンスの共有をサポートするためにも使用されます。Primetime DRM 3.0以降、この機能は「デバイスドメインのサポート」と呼ばれます。 展開がこの使用例をサポートしている場合は、`DRMManager.addToDeviceGroup()`メソッドを使用して複数のマシンをデバイスグループに登録できます。 特定のコンテンツに対して有効なドメインバインドライセンスを持つマシンがある場合、アプリケーションは`DRMVoucher.toByteArray()`メソッドを使用してシリアライズ済みのライセンスを抽出し、他のマシンでは`DRMManager.storeVoucher()`メソッドを使用してライセンスを読み込むことができます。

## デバイス登録について{#about-device-registration}

すべてのPrimetime DRMライセンスは、作成時にエンドエンティティにバインドする必要があります。 バインディングは、特定のエンティティにライセンスを消費する機能のみを許可する暗号化プロセスです。 これは、任意のデバイスで使用できる「フローティングライセンス」を防ぐために必要です。 Primetime DRMから「事前生成」ライセンスへの移行については、これは、事前生成されたライセンスの「ターゲット」が事前に認識されている必要があることを意味します。 Primetime DRMは、これを「デバイス登録」と呼びます。

## デバイスの登録{#register-a-device}

次のタスクを実行したと仮定します。

* Primetime DRM Server SDKを設定しました。
* 事前に生成されたライセンスを発行するためのHTTPサーバーが設定されている。
* 保護されたコンテンツを表示するためのPrimetimeアプリケーションを作成しました。

 デバイス登録フェーズには、次の操作が含まれます。

1. ランダムに生成されたIDがアプリケーションによって作成されます。
1. アプリケーションが`DRMManager.authenticate()`メソッドを呼び出します。 アプリケーションでは、ランダムに生成されたIDを認証リクエストに含める必要があります。 例えば、「username」フィールドにIDを含めます。
1. 手順2で説明した操作によって、Primetime DRMが顧客のサーバーに認証リクエストを送信します。 この要求には、デバイス証明書が含まれます。
   1. サーバは、要求からデバイス証明書と生成されたIDを抽出し、保存する。
   1. お客様のサブシステムは、このデバイス証明書のライセンスを事前に生成し、保存し、生成されたIDに関連付ける方法でそれらへのアクセスを許可します。.
1. サーバーは、「成功」メッセージを使用してリクエストに応答します。
1. 生成されたIDはアプリケーションによって保存されます。

デバイスの登録後、アプリケーションは、前のスキームで使用したのと同じ方法で、生成されたIDを使用します。
1. 生成されたIDの検索が試行されます。
1. 生成されたIDが見つかった場合、アプリケーションは、生成済みのライセンスをダウンロードする際に、生成されたIDを使用します。 アプリケーションは、`DRMManager.storeVoucher()`メソッドを使用して使用するためにPrimetime DRMクライアントにライセンスを送信します。.
1. 生成されたIDが見つからない場合、アプリケーションはデバイス登録手順を実行します。

## DRMファクトリのリセット{#drm-factory-reset}

デバイスのユーザーがDRMファクトリリセットオプションを呼び出すと、デバイス証明書は削除されます。 保護されたコンテンツの再生を続行するには、アプリケーションはデバイス登録手順を再度実行する必要があります。 古い生成済みのライセンスがアプリケーションから送信された場合、Primetime DRMクライアントは、古いデバイスID用にライセンスが暗号化されているので、そのライセンスを拒否します。

* FlashAPI:[DRMManager.resetDRMVouchers()](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/drm/DRMManager.html#resetDRMVouchers()) - （回復不可能な特定のDRMエラーコードに対してのみ呼び出すことができます）
* iOS API:[DRMManager resetDRM](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a0dd6c9662428583196e0419d3ea69446)
* Android API:[DRMManager.resetDRM()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#resetDRM(com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMOperationCompleteCallback))