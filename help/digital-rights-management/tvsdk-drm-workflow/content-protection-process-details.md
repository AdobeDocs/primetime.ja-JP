---
seo-title: ライセンス取得プロセスの詳細
title: ライセンス取得プロセスの詳細
uuid: 4825c49e-fa6f-4c98-9d21-a2743930ca2e
translation-type: tm+mt
source-git-commit: 3fdef12b717bb6f70ca27d9278de61d709f8349c

---


# ライセンス取得プロセスの詳細 {#license-acquisition-process-details}

このプロセスは、Primetime DRM保護コンテンツワークフローのAPIレベルの詳細なビューを表示します。

1. オブジェクト `URLLoader` を使用して、保護されたコンテンツのメタデータファイルのバイトを読み込みます。

   このオブジェクトを変数（など）に設定しま `metadata_bytes`す。 Primetime DRMで制御されるすべてのコンテンツには、Primetime DRMメタデータが含まれます。 コンテンツをパッケージ化すると、このメタデータをコンテンツと共に別のメタデータファイル( [!DNL .metadata])として保存できます。 また、メタデータをBase64でエンコードし、ビデオマニフェストファイルの本体に挿入することもできます。 詳しくは、メディアファイルのパッケ [ージ化を参照してくださ](../protecting-content/packaging-media-overview/packaging-media-files.md)い。
   1. 必要に応じて、文字列の先頭から感嘆符 `!` を削除してください。
   1. HLSまたはHDSコンテンツに必要な場合は、Base64エンコードされた文字列に含まれるメタデータをバイナリデータにデコードしてから、渡します。
1. インスタンスを作 `DRMContentData` 成します。

   次のコードをtry-catchブロックに入れます。

   ```
   new DRMContentData(metadata_bytes)
   ```

   ここで、 `metadata_bytes` は手順1で `URLLoader` 取得したオブジェクトです。

   [iOS:DRMMetadata](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_metadata.html)

   [Android:DRMMetadata](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/index.html)

1. オブジェクトをリッスンし、オブジェクトから `DRMStatusEvent` ディスパッチ `DRMErrorEvent` するリスナーを作成 `DRMManager` します。

   ```
   DRMManager.addEventListener(DRMStatusEvent.DRM_STATUS, onDRMStatus); 
   DRMManager.addEventListener(DRMErrorEvent.DRM_ERROR, onDRMError);
   ```

   リスナーで、 `DRMStatusEvent` ライセンスが有効（ヌルではない）であることを確認します。 リスナーで、 `DRMErrorEvent` ハンドルを指定しま `DRMErrorEvents`す。 DRMStatusEventクラ *スの使用およびこのガイドの* DRMErrorEvent *クラスの使用* （英語のみ）を参照してください。

1. コンテンツの再生に必要なライセンスを読み込みます。
まず、コンテンツを再生するために、ローカルに保存されたライセンスを読み込もうとします。

   ```
   DRMManager.loadvoucher(drmContentData, LoadVoucherSetting.LOCAL_ONLY)
   ```

   [Android:DRMManager.acquireLicense()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#acquireLicense(com.adobe.ave.drm.DRMMetadata,%20com.adobe.ave.drm.DRMAcquireLicenseSettings,%20com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMLicenseAcquiredCallback))

   [iOS:acquireLicense:](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a52accb5ed5b49d6e5d91277d78279f1b)

   読み込みが完了すると、オブジェクトが `DRMManager` ディスパッチされま `DRMStatusEvent.DRM_Status`す。

1. オブジェクトをチェ `DRMVoucher` ックします。


   オブジェクト `DRMVoucher` がnullでない場合、ライセンスは有効です。 手順9に進みます。

   [Android:DRMLicenseAccivatedCallback](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMLicenseAcquiredCallback.html)

   [iOS:DRMLicenseAcquived](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/_d_r_m_interface_8h.html#afe5a9e3a003f312ee268d9b00927fa6d)
1. このコンテンツのポリシーで必要な認証方法を確認します。

   プロパティを使 `DRMContentData.authenticationMethod` 用します。
   1. 認証方法が有効な場合 `ANONYMOUS`は、手順9に進みます。 

      [Android:DRMAuthenticationMethod](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/index.html?com/adobe/ave/drm/DRMLicenseAcquiredCallback.html)

      [iOS:DRMAuthenticationMethod](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/_d_r_m_interface_8h.html#a2003f29af93898b52a4123c2dd92c457)
   1. 認証方法が有効な場合は、ユ `USERNAME_AND_PASSWORD`ーザーが資格情報を入力できるメカニズムをアプリケーションが提供する必要があります。

      ユーザーの資格情報をライセンスサーバーに渡して、ユーザーを認証します。

      ```
      DRMManager.authenticate( metadata.serverURL, metadata.domain, username, password)
      ```

      認証に `DRMManager` 失敗した場 `DRMAuthenticationErrorEvent` 合、または認証に成功した場合に、が `DRMAuthenticationCompleteEvent` ディスパッチされます。 これらのイベントのリスナーを作成します。

      [Android:authenticate()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#authenticate(com.adobe.ave.drm.DRMMetadata,%20java.lang.String,%20java.lang.String,%20java.lang.String,%20java.lang.String,%20com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMAuthenticationCompleteCallback))

      [iOS:認証：](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a169c1441f196a834094a8e0f5ecb4aca)

      >[!NOTE]
      >
      >アドビでは、証明書を提供する際に、より安全なメカニズムを使用することをお勧めします。 詳しくは、KeyGenParameterSpecを参照してく [ださい](https://developer.android.com/reference/android/security/keystore/KeyGenParameterSpec.html)。

   1. 認証方法が有効な場合は、カ `UNKNOWN`スタム認証方法を使用する必要があります。

      この場合、コンテンツプロバイダーは、Primetime APIを使用せず、帯域外で認証を行うように手配しています。 カスタム認証手順では、メソッドに渡すことのできる認証トークンを生成する必要があ `DRMManager.setAuthenticationToken()` ります。

      [Android:setAuthenticationToken()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#setAuthenticationToken(com.adobe.ave.drm.DRMMetadata,%20java.lang.String,%20byte[],%20com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMOperationCompleteCallback))

      [iOS:setAuthenticationToken:](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a17884b5d9bcc5b0b39503f61140f9b09)

      >[!NOTE]
      >
      >また、認証方法に関係なく、クライアント `.setAuthenticationToken()` からライセンスサーバーにカスタムデータを送信するために使用することもできます。 これはAPIのオーバーロードです。このメカニズムは、ライセンスの取得時に動的なカスタムデータをクライアントからライセンスサーバーに送信する唯一の方法です。 このカスタムデータ転送の方法については、 [Primetime DRM(Adobe Access)フォーラムの複数のフォーラム投稿で詳しく説明していま ](https://forums.adobe.com/community/adobe_access)す。

1. 認証に失敗した場合は、アプリケーションを手順6に戻す必要があります。

   アプリケーションに、認証エラーの繰り返しを処理および制限するメカニズムが備わっていることを確認します。 例えば、3回試行した後、認証に失敗し、コンテンツを再生できないことを示すメッセージをユーザーに表示します。
1. ユーザーに資格情報の入力を促す代わりに、保存されたトークンを使用するには、メソッドを使用してトークンを設定 `DRMManager.setAuthenticationToken()` します。

   次に、ライセンスサーバーからライセンスをダウンロードし、手順6と同様にコンテンツを再生します。
   1. **オプション：** 認証が成功した場合は、認証トークンを取り込むことができます。認証トークンは、メモリ内にキャッシュされたバイト配列です。

      このトークンをプロパティと共に取得 `DRMAuthenticationCompleteEvent.token` します。 認証トークンを保存して使用すると、ユーザーがこのコンテンツの資格情報を繰り返し入力する必要がなくなります。 ライセンスサーバは、認証トークンの有効期間を決定します。

      [Android:OperationComplete()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMOperationCompleteCallback.html)

      [iOS:DRMOperationComplete](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/_d_r_m_interface_8h.html#a5f2392ec6661b51bf7b0df71cd514731)
1. 認証に成功した場合は、ライセンスサーバーからライセンスをダウンロードします。

   ```
   DRMManager.loadvoucher( 
      drmContentData, 
      LoadVoucherSetting.FORCE_REFRESH)
   ```

   読み込みが完了すると、オブジェクトが `DRMManager` ディスパッチされま `DRMStatusEvent.DRM_STATUS`す。 このイベントをリッスンし、ディスパッチされたら、コンテンツを再生できます。  Primetimeオブジェクトを作成し、そのメソッドを呼び出してビデオを再生 `play()` します。

   ```
   stream = new Primetime(connection); 
   stream.addEventListener(DRMStatusEvent.DRM _STATUS, drmStatusHandler); 
   stream.addEventListener(DRMErrorEvent.DRM_ERROR, drmErrorHandler); 
   stream.addEventListener(NetStatusEvent.NET_STATUS, netStatusHandler); 
   stream.client = new CustomClient(); 
   video.attachPrimetime(stream); 
   stream.play(videoURL);
   ```

   [Android:acquireLicense()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#acquireLicense(com.adobe.ave.drm.DRMMetadata,%20com.adobe.ave.drm.DRMAcquireLicenseSettings,%20com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMLicenseAcquiredCallback))

   [iOS:acquireLicense:](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a52accb5ed5b49d6e5d91277d78279f1b)