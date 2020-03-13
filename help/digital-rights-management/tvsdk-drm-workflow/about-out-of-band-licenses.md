---
seo-title: 帯域外ライセンスの概要
title: 帯域外ライセンスの概要
uuid: 82e4529a-ee1b-4c0c-8885-e0e68319d1a0
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# 帯域外ライセンス {#out-of-band-licenses}

また、この方法を使用して、ライセンスをディスク上およびメモリ内に格納することで、（Primetime DRMライセンスサーバーに接続せずに）帯域外でライセンスを取得することもで `storeVoucher()` きます。

Primetimeで暗号化されたビデオを再生するには、対応するランタイムがそのビデオのライセンスを取得する必要があります。 ライセンスにはビデオの復号化キーが含まれ、顧客がデプロイしたPrimetime DRMライセンスサーバーによって生成されます。

ランタイムは、通常、ビデオのDRMメタデータ（クラス）に示されているPrimetime DRMライセンスサーバーにライセンス要求を送信することで、このライセンスを `DRMContentData` 取得します。 アプリケーションは、メソッドを呼び出すことで、このライセンス要求をトリガ `DRMManager.loadVoucher()` ーできます。

`DRMManager.storeVoucher()` アプリケーションが、帯域外で取得したライセンスを送信できるようにします。 その後、ランタイムはライセンス要求プロセスをスキップし、転送されたライセンスを使用して暗号化されたビデオを再生できます。 ライセンスを帯域外で取得するには、Primetime DRMライセンスサーバーでライセンスを生成する必要があります。 ただし、Primetime DRMライセンスサーバーではなく、任意のHTTPサーバーでライセンスをホストするオプションがあります。

`DRMManager.storeVoucher()` は、複数のデバイス間でのライセンス共有をサポートする目的でも使用されます。 Primetime DRM 3.0以降、この機能は「デバイスドメインのサポート」と呼ばれます。 展開がこの使用例をサポートしている場合は、この方法を使用して複数のマシンをデバイスグループに登録で `DRMManager.addToDeviceGroup()` きます。 特定のコンテンツに対して有効なドメインバインドライセンスが割り当てられているコンピューターがある場合は、その方法を使用してシリアル化されたライセンスを抽出し、その他のコンピューターでその方法を使用してライセンスを読み込むことがで `DRMVoucher.toByteArray()``DRMManager.storeVoucher()` きます。

## デバイス登録について {#about-device-registration}

すべてのPrimetime DRMライセンスは、作成時にエンドエンティティに連結する必要があります。 連結とは、特定のエンティティに対してのみライセンスの消費を許可する暗号化プロセスです。 これは、任意のデバイスで使用できる「フローティングライセンス」を防ぐために必要です。 Primetime DRMから「事前生成」ライセンスへの移行については、これらの事前生成ライセンスの「ターゲット」が事前に認識されている必要があります。 Primetime DRMは、これを「デバイス登録」と呼びます。

## デバイスの登録 {#register-a-device}

次のタスクを実行したとします。

* Primetime DRMサーバーSDKを設定しました。
* 事前に生成されたライセンスを発行するHTTPサーバーを設定した。
* 保護されたコンテンツを表示するPrimetimeアプリケーションを作成しました。

 デバイスの登録段階では、次の操作を行います。

1. ランダムに生成されたIDが作成されます。
1. アプリケーションがメソッドを呼び `DRMManager.authenticate()` 出します。 アプリケーションは、ランダムに生成されたIDを認証リクエストに含める必要があります。 例えば、ユーザー名フィールドにIDを含めます。
1. 手順2で説明した操作により、Primetime DRMが顧客のサーバーに認証要求を送信します。 この要求には、デバイス証明書が含まれます。
   1. サーバは、要求からデバイス証明書と生成されたIDを抽出し、保存します。
   1. 顧客のサブシステムは、このデバイス証明書のライセンスを事前に生成し、保存し、生成されたIDに関連付ける方法でアクセス権を付与します。.
1. サーバーは、「成功」メッセージを使用してリクエストに応答します。
1. 生成されたIDがアプリケーションに保存されます。

デバイスの登録後、アプリケーションは、前のスキームでデバイスIDを使用した場合と同じ方法で、生成されたIDを使用します。
1. 生成されたIDの検索が試行されます。
1. 生成されたIDが見つかった場合、アプリケーションは、生成済みのライセンスをダウンロードする際に、生成されたIDを使用します。 アプリケーションは、この方法を使用して使用するために、Primetime DRMクライアントにライセンスを送信 `DRMManager.storeVoucher()` します。.
1. 生成されたIDが見つからない場合は、デバイス登録手順が実行されます。

## DRMファクトリのリセット {#drm-factory-reset}

デバイスのユーザーがDRMファクトリのリセットオプションを呼び出すと、デバイス証明書は削除されます。 保護されたコンテンツの再生を続行するには、アプリケーションがデバイス登録手順を再度実行する必要があります。 アプリケーションが古い事前生成ライセンスを送信する場合、Primetime DRMクライアントは、古いデバイスID用にライセンスが暗号化されているので、このライセンスを拒否します。

* Flash API: [DRMManager.resetDRMVouchers()](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/drm/DRMManager.html#resetDRMVouchers()) - （回復不可能な特定のDRMエラーコードに応じてのみ呼び出すことができます。）
* iOS API:DRMManager [resetDRM](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a0dd6c9662428583196e0419d3ea69446)
* Android API: [DRMManager.resetDRM()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#resetDRM(com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMOperationCompleteCallback))