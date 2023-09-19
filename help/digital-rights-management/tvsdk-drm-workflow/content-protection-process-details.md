---
title: ライセンス取得プロセスの詳細
description: ライセンス取得プロセスの詳細
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '968'
ht-degree: 0%

---

# ライセンス取得プロセスの詳細 {#license-acquisition-process-details}

このプロセスでは、Primetime DRM protected-content ワークフローの API レベルの詳細な表示を示します。

1. の使用 `URLLoader` オブジェクトの場合は、保護されたコンテンツのメタデータファイルのバイトを読み込みます。

   このオブジェクトを次のような変数に設定します。 `metadata_bytes`. Primetime DRM で制御されるすべてのコンテンツには、Primetime DRM メタデータが含まれます。 コンテンツをパッケージ化する際に、このメタデータを別のメタデータファイル ( [!DNL .metadata]) をコンテンツと共にクリックします。 また、メタデータを Base64 でエンコードして、ビデオマニフェストファイルの本文に挿入することもできます。 詳しくは、 [メディアファイルのパッケージ化](../protecting-content/packaging-media-overview/packaging-media-files.md).
   1. 必要に応じて、感嘆符を削除します。 `!` 文字列の先頭から。
   1. HLS または HDS コンテンツに必要な場合は、Base64 エンコードされた文字列に含まれるメタデータをバイナリデータにデコードしてから、渡します。
1. の作成 `DRMContentData` インスタンス。

   次のコードを try-catch ブロックに配置します。

   ```
   new DRMContentData(metadata_bytes)
   ```

   場所 `metadata_bytes` が `URLLoader` オブジェクトは、手順 1 で取得します。

   [iOS:DRMMetadata](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_metadata.html)

   [Android: DRMMetadata](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/index.html)

1. リスナーを作成して、 `DRMStatusEvent` および `DRMErrorEvent` ～から派遣される `DRMManager` オブジェクト。

   ```
   DRMManager.addEventListener(DRMStatusEvent.DRM_STATUS, onDRMStatus); 
   DRMManager.addEventListener(DRMErrorEvent.DRM_ERROR, onDRMError);
   ```

   Adobe Analytics の `DRMStatusEvent` リスナー、ライセンスが有効（null ではない）であることを確認します。 Adobe Analytics の `DRMErrorEvent` リスナー、ハンドル `DRMErrorEvents`. 詳しくは、 *DRMStatusEvent クラスの使用* および *DRMErrorEvent クラスの使用* 」を参照してください。

1. コンテンツの再生に必要なライセンスを読み込みます。
まず、ローカルに保存されているライセンスを読み込んでコンテンツを再生します。

   ```
   DRMManager.loadvoucher(drmContentData, LoadVoucherSetting.LOCAL_ONLY)
   ```

   [Android: DRMManager.acquireLicense()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#acquireLicense(com.adobe.ave.drm.DRMMetadata,%20com.adobe.ave.drm.DRMAcquireLicenseSettings,%20com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMLicenseAcquiredCallback))

   [iOS: acquireLicense:](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a52accb5ed5b49d6e5d91277d78279f1b)

   読み込みが完了した後、 `DRMManager` オブジェクトのディスパッチ `DRMStatusEvent.DRM_Status`.

1. 次を確認します。 `DRMVoucher` オブジェクト。


   次の場合、 `DRMVoucher` オブジェクトが null ではない場合、ライセンスは有効です。 手順 9 に進みます。

   [Android: DRMLicenseAccuratedCallback](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMLicenseAcquiredCallback.html)

   [iOS:DRMLicenseAccariated](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/_d_r_m_interface_8h.html#afe5a9e3a003f312ee268d9b00927fa6d)
1. このコンテンツのポリシーで必要な認証方法を確認します。

   以下を使用します。 `DRMContentData.authenticationMethod` プロパティ。
   1. 認証方法が `ANONYMOUS`、手順 9 に進みます。 

      [Android: DRMAuthenticationMethod](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/index.html?com/adobe/ave/drm/DRMLicenseAcquiredCallback.html)

      [iOS:DRMAuthenticationMethod](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/_d_r_m_interface_8h.html#a2003f29af93898b52a4123c2dd92c457)
   1. 認証方法が `USERNAME_AND_PASSWORD`を使用する場合、アプリケーションは、ユーザーに資格情報を入力させるメカニズムを提供している必要があります。

      ユーザーの資格情報をライセンスサーバーに渡して、ユーザーを認証します。

      ```
      DRMManager.authenticate( metadata.serverURL, metadata.domain, username, password)
      ```

      The `DRMManager` を派遣する `DRMAuthenticationErrorEvent` 認証に失敗した場合、または `DRMAuthenticationCompleteEvent` 認証が成功した場合は。 これらのイベントのリスナーを作成します。

      [Android: authenticate()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#authenticate(com.adobe.ave.drm.DRMMetadata,%20java.lang.String,%20java.lang.String,%20java.lang.String,%20java.lang.String,%20com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMAuthenticationCompleteCallback))

      [iOS：認証：](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a169c1441f196a834094a8e0f5ecb4aca)

      >[!NOTE]
      >
      >Adobeでは、より安全なメカニズムを使用して資格情報を提供することをお勧めします。 詳しくは、 [KeyGenParameterSpec](https://developer.android.com/reference/android/security/keystore/KeyGenParameterSpec.html).

   1. 認証方法が `UNKNOWN`に値を入力する場合は、カスタム認証方式を使用する必要があります。

      この場合、コンテンツプロバイダーは、Primetime API を使用せずに、帯域外で認証をおこなうように設定しています。 カスタム認証手順では、に渡すことができる認証トークンを生成する必要があります。 `DRMManager.setAuthenticationToken()` メソッド。

      [Android: setAuthenticationToken()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#setAuthenticationToken(com.adobe.ave.drm.DRMMetadata,%20java.lang.String,%20byte[],%20com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMOperationCompleteCallback))

      [iOS: setAuthenticationToken:](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a17884b5d9bcc5b0b39503f61140f9b09)

      >[!NOTE]
      >
      >また、認証方法に関係なく、 `.setAuthenticationToken()` を使用して、クライアントからライセンスサーバーにカスタムデータを送信できます。 これは API のオーバーロードです。このメカニズムを使用して、ライセンスの取得時にクライアントからライセンスサーバーに動的なカスタムデータを送信する唯一の方法です。 このカスタムデータ転送の方法については、 [Primetime DRM(Adobeアクセス ) フォーラム](https://forums.adobe.com/community/adobe_access).

1. 認証に失敗した場合、アプリケーションは手順 6 に戻る必要があります。

   アプリケーションに、認証エラーの繰り返しを処理および制限するメカニズムがあることを確認します。 例えば、3 回試みた後に、認証に失敗し、コンテンツを再生できないことを示すメッセージをユーザーに表示します。
1. ユーザーに資格情報の入力を促す代わりに、保存されたトークンを使用するには、 `DRMManager.setAuthenticationToken()` メソッド。

   次に、手順 6 に従って、ライセンスサーバからライセンスをダウンロードし、コンテンツを再生します。
   1. **オプション：** 認証が成功した場合は、認証トークンを取り込むことができます。認証トークンは、メモリにキャッシュされたバイト配列です。

      このトークンを `DRMAuthenticationCompleteEvent.token` プロパティ。 認証トークンを保存して使用すると、ユーザーがこのコンテンツの資格情報を繰り返し入力する必要がなくなります。 ライセンスサーバは、認証トークンの有効期間を決定します。

      [Android: OperationComplete()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMOperationCompleteCallback.html)

      [iOS:DRMOperationComplete](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/_d_r_m_interface_8h.html#a5f2392ec6661b51bf7b0df71cd514731)
1. 認証に成功した場合は、ライセンスサーバからライセンスをダウンロードします。

   ```
   DRMManager.loadvoucher( 
      drmContentData, 
      LoadVoucherSetting.FORCE_REFRESH)
   ```

   読み込みが完了した後、 `DRMManager` オブジェクトのディスパッチ `DRMStatusEvent.DRM_STATUS`. このイベントをリッスンします。ディスパッチされると、コンテンツを再生できます。  Primetime オブジェクトを作成し、そのを呼び出してビデオを再生します。 `play()` メソッド：

   ```
   stream = new Primetime(connection); 
   stream.addEventListener(DRMStatusEvent.DRM _STATUS, drmStatusHandler); 
   stream.addEventListener(DRMErrorEvent.DRM_ERROR, drmErrorHandler); 
   stream.addEventListener(NetStatusEvent.NET_STATUS, netStatusHandler); 
   stream.client = new CustomClient(); 
   video.attachPrimetime(stream); 
   stream.play(videoURL);
   ```

   [Android: acquireLicense()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#acquireLicense(com.adobe.ave.drm.DRMMetadata,%20com.adobe.ave.drm.DRMAcquireLicenseSettings,%20com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMLicenseAcquiredCallback))

   [iOS: acquireLicense:](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a52accb5ed5b49d6e5d91277d78279f1b)
