---
description: ビデオのDRMメタデータがメディアストリームとは別の場合、再生を開始する前に認証を実行します。
seo-description: ビデオのDRMメタデータがメディアストリームとは別の場合、再生を開始する前に認証を実行します。
seo-title: 再生前のDRM認証
title: 再生前のDRM認証
uuid: 326ef93d-53b0-4e3a-b16d-f3b886837cc0
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# 再生前のDRM認証 {#drm-authentication-before-playback}

ビデオのDRMメタデータがメディアストリームとは別の場合、再生を開始する前に認証を実行します。

ビデオアセットには、DRMメタデータファイルを関連付けることができます。 例：

* &quot;url&quot;:&quot;<span></span>https://www.domain.com/asset.m3u8&quot;
* &quot;drmMetadata&quot;:&quot;<span></span>https://www.domain.com/asset.metadata&quot;

この場合、メソッドを使用して、DRM `DRMHelper` メタデータファイルのコンテンツをダウンロードし、解析し、DRM認証が必要かどうかを確認します。

1. を使用し `loadDRMMetadata` て、メタデータのURLコンテンツを読み込み、にダウンロードされたバイトを解析しま `DRMMetadata`す。

   他のネットワーク操作と同様に、このメソッドは非同期で、独自のスレッドを作成します。

   ```java
   public static void loadDRMMetadata( 
       final DRMManager drmManager, 
       final String drmMetadataUrl,  
       final DRMLoadMetadataListener loadMetadataListener); 
   ```

   例：

   ```java
   DRMHelper.loadDRMMetadata(drmManager, metadataURL, new DRMLoadMetadataListener());
   ```

1. 操作は非同期なので、ユーザーにそのことを知らせることをお勧めします。 そうしないと、再生が開始されない理由がわかります。 例えば、DRMメタデータのダウンロードと解析中にスピナーホイールを表示します。
1. でコールバックを実装しま `DRMLoadMetadataListener`す。 これらのイ `loadDRMMetadata` ベントハンドラーを呼び出します（これらのイベントをディスパッチします）。

   ```java
   public interface  
    <b>DRMLoadMetadataListener</b> { 
    public void  
    <b>onLoadMetadataUrlStart</b>(); 
    /** 
     * @param authNeeded 
     * whether DRM authentication is needed. 
     * @param drmMetadata 
     * the parsed DRMMetadata obtained.    */ 
    public void  
    <b>onLoadMetadataUrlComplete</b>(boolean authNeeded, DRMMetadata drmMetadata); 
    public void  
    <b>onLoadMetadataUrlError</b>(); 
   }
   ```

   * `onLoadMetadataUrlStart` メタデータのURLの読み込みが開始されたことを検出します。
   * `onLoadMetadataUrlComplete` メタデータURLの読み込みが完了したことを検出します。
   * `onLoadMetadataUrlError` メタデータの読み込みに失敗したことを示します。

1. 読み込みが完了したら、オブジェクトを `DRMMetadata` 調べて、DRM認証が必要かどうかを確認します。

   ```java
   public static boolean <b>isAuthNeeded</b>(DRMMetadata drmMetadata);
   ```

   例：

   ```java
   @Override 
   public void onLoadMetadataUrlComplete(boolean authNeeded, DRMMetadata drmMetadata) {  
     Log.i(LOG_TAG + "#onLoadMetadataUrlComplete",  
                     "Loaded metadata URL contents. Auth needed:" + authNeeded + "."); 
     if (!authNeeded) { 
         // Auth is not required. Start player activity.     
         showLoadingSpinner(false);     
         startPlayerActivity(ASSET_URL); 
         return; 
     }
   ```

1. 認証が必要ない場合は、再生を開始します。
1. 認証が必要な場合は、ライセンスを取得して認証を実行します。

   ```java
   /** 
   * Helper method to perform DRM authentication. 
   * 
   * @param drmManager 
   * the DRMManager, used to perform the authentication. 
   * @param drmMetadata 
   * the DRMMetadata, containing the DRM specific information. 
   * @param authenticationListener 
   * the listener, on which the user can be notified about the 
   * authentication process status. 
   */ 
   public static void performDrmAuthentication( 
        final DRMManager drmManager,  
        final DRMMetadata drmMetadata, 
        final String authUser,  
        final String authPass,  
        final DRMAuthenticationListener authenticationListener);
   ```

   この例では、わかりやすくするために、ユーザーの名前とパスワードを明示的にコード化しています。

   ```java
   DRMHelper.performDrmAuthentication(drmManager, drmMetadata, DRM_USERNAME, DRM_PASSWORD,  
     new DRMAuthenticationListener() { 
       @Override 
       public void onAuthenticationStart() { 
           Log.i(LOG_TAG + "#onAuthenticationStart", "DRM authentication started."); 
           // Spinner is already showing. 
       } 
       @Override 
       public void onAuthenticationError(int major, int minor, String errorString, String serverErrorURL) {  
           Log.e(LOG_TAG + "#onAuthenticationError", "DRM authentication failed. " +  
             major + " 0x" + Long.toHexString(minor)); 
           showToast(getString(R.string.drmAuthenticationError));   
           showLoadingSpinner(false); 
       } 
       @Override 
       public void onAuthenticationComplete(byte[] authenticationToken) { 
           Log.i(LOG_TAG + "#onAuthenticationComplete", "Auth successful. Launching content."); 
           showLoadingSpinner(false); 
           startPlayerActivity(ASSET_URL); 
       } 
   }); 
   ```

1. これはネットワーク通信を意味するので、これも非同期操作です。 イベントリスナーを使用して、認証ステータスを確認します。

   ```java
   public interface DRMAuthenticationListener { 
       /** 
       * Called to indicate that DRM authentication has started. 
       */ 
       public void onAuthenticationStart(); 
       /** 
       * Called to indicate that DRM authentication has been successful. 
       * 
       * @param authenticationToken 
       * the obtained token, which can be stored locally. 
       */ 
       public void onAuthenticationComplete(byte[] authenticationToken); 
       /** 
       * Called to indicate that an error occurred while performing the DRM 
       * authentication. 
       * 
       * @param major 
       * the major code. 
       * @param minorC 
       * the minor code. 
       * @param errorString 
       * the exception thrown. 
       * @param serverErrorURL 
       * the URL of the server  
       * on which the error occurred 
       */ 
       public void onAuthenticationError(int major, int minor,  
         String errorString, String serverErrorURL); 
   } 
   ```

1. 認証に成功した場合は、再生を開始します。
1. 認証に失敗した場合は、ユーザーに通知し、再生を開始しません。

アプリケーションで認証エラーを処理する必要があります。 再生前に認証に失敗すると、TVSDKはエラー状態になります。 つまり、状態がERRORに変更され、DRMライブラリのエラーコードを含むエラーが生成され、再生が停止します。 アプリケーションで問題を解決し、プレイヤーをリセットし、リソースを再読み込みする必要があります。

