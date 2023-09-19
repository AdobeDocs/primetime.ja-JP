---
description: ビデオの DRM メタデータがメディアストリームとは別の場合、再生を開始する前に認証が必要です。
title: 再生前の DRM 認証
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# 再生前の DRM 認証 {#drm-authentication-before-playback}

ビデオの DRM メタデータがメディアストリームとは別の場合、再生を開始する前に認証が必要です。

ビデオアセットには、次のような DRM メタデータファイルを関連付けることができます。

* `"url": "https://www.domain.com/asset.m3u8"`
* `"drmMetadata": "https://www.domain.com/asset.metadata"`

この例では、 `DRMHelper` DRM メタデータファイルのコンテンツをダウンロードし、解析して、DRM 認証が必要かどうかを確認するためのメソッド。

1. 用途 `loadDRMMetadata` メタデータ URL コンテンツを読み込み、にダウンロードしたバイトを解析するには、以下を実行します。 `DRMMetadata`.

   >[!TIP]
   >
   >このメソッドは非同期で、独自のスレッドを作成します。

   ```java
   public static void loadDRMMetadata( 
       final DRMManager drmManager, 
       final String drmMetadataUrl,  
       final DRMLoadMetadataListener loadMetadataListener); 
   ```

   例：

   ```java
   DRMHelper.loadDRMMetadata(drmManager,  
                                      metadataURL,  
                                      new DRMLoadMetadataListener());
   ```

1. この操作が非同期であることをユーザーに通知する場合は、それをユーザーに知らせることをお勧めします。

   操作が非同期であることがわからない場合は、なぜ再生がまだ開始されていないのかと疑問に思うことがあります。 例えば、DRM メタデータをダウンロードして解析する際に、スピナーホイールを表示できます。

1. にコールバックを実装します。 `DRMLoadMetadataListener`.

   The `loadDRMMetadata` は、これらのイベントハンドラーを呼び出します。

   ```java
   public interface DRMLoadMetadataListener { 
   
       public void onLoadMetadataUrlStart(); 
   
       /** 
       * @param authNeeded 
       * whether DRM authentication is needed. 
       * @param drmMetadata 
       * the parsed DRMMetadata obtained.    */ 
       public void onLoadMetadataUrlComplete(boolean authNeeded, DRMMetadata drmMetadata); 
       public void onLoadMetadataUrlError(); 
   } 
   ```

   ハンドラーの詳細を次に示します。

   * `onLoadMetadataUrlStart` は、メタデータ URL の読み込みが開始された際にを検出します。
   * `onLoadMetadataUrlComplete` は、メタデータ URL の読み込みが完了したことを検出します。
   * `onLoadMetadataUrlError` メタデータの読み込みに失敗したことを示します。

1. 読み込みが完了したら、 `DRMMetadata` オブジェクトを使用して、DRM 認証が必要かどうかを判断します。

   ```java
   public static boolean isAuthNeeded(DRMMetadata drmMetadata);
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
   } 
   ```

1. 次のいずれかの作業を実行します。

   * 認証が必要ない場合は、再生を開始します。
   * 認証が必要な場合は、ライセンスを取得して認証を完了します。

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

     この例では、簡単にするために、ユーザーの名前とパスワードが明示的にコード化されています。

     ```java
     DRMHelper.performDrmAuthentication(drmManager,  
                                        drmMetadata,  
                                        DRM_USERNAME,  
                                        DRM_PASSWORD, new DRMAuthenticationListener() { 
         @Override 
         public void onAuthenticationStart() { 
             Log.i(LOG_TAG + "#onAuthenticationStart", "DRM authentication started."); 
             // Spinner is already showing. 
         } 
         @Override 
         public void onAuthenticationError(int major,  
                                           int minor,  
                                           String errorString,  
                                           String serverErrorURL) { 
             Log.e(LOG_TAG +  
                   "#onAuthenticationError",  
                   "DRM authentication failed. " +  
                   major + " 0x" + Long.toHexString(minor)); 
             showToast(getString(R.string.drmAuthenticationError));   
             showLoadingSpinner(false); 
         } 
         @Override 
         public void onAuthenticationComplete(byte[] authenticationToken) { 
             Log.i(LOG_TAG +  
                   "#onAuthenticationComplete", "Auth successful. Launching content."); 
             showLoadingSpinner(false); 
             startPlayerActivity(ASSET_URL); 
         } 
     }); 
     ```

1. イベントリスナーを使用して認証状態を確認します。

   このプロセスはネットワーク通信を意味するので、これは非同期操作でもあります。

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
       public void onAuthenticationError(int major,  
                                         int minor,  
                                         String errorString,  
                                         String serverErrorURL); 
   } 
   ```

1. 認証に成功した場合は、再生を開始します。
1. 認証に成功しなかった場合は、ユーザーに通知し、再生を開始しません。

   アプリケーションで認証エラーが発生した場合は処理する必要があります。 再生前に認証に失敗すると、TVSDK はエラー状態になり、再生が停止します。 アプリケーションで問題を解決し、プレーヤーをリセットして、リソースを再読み込みする必要があります。
