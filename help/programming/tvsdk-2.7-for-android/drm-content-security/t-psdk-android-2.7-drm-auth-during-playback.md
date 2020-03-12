---
description: ビデオのDRMメタデータがメディアストリームに含まれる場合、再生中に認証を実行できます。
seo-description: ビデオのDRMメタデータがメディアストリームに含まれる場合、再生中に認証を実行できます。
seo-title: 再生中のDRM認証
title: 再生中のDRM認証
uuid: b3ff8edd-a3d4-470e-8899-580eca9fff4a
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# 再生中のDRM認証 {#drm-authentication-during-playback}

ビデオのDRMメタデータがメディアストリームに含まれる場合、再生中に認証を実行できます。

ライセンスのローテーションでは、アセットは複数のDRMライセンスで暗号化されます。 新しいDRMメタデータが見つかるたびに、DRMメタデ `DRMHelper` ータにDRM認証が必要かどうかを確認するためにメソッドが使用されます。

>[!TIP]
>
>再生を開始する前に、ドメインバインドライセンスを処理しているかどうか、およびドメイン認証が必要かどうかを確認します。 ドメイン認証が有効な場合は、ドメイン認証を完了し、ドメインに参加します。

1. アセット内で新しいDRMメタデータが見つかると、アプリケーションレイヤーでイベントがディスパッチされます。

   ```java
   mediaPlayer.addEventListener(MediaPlayerEvent.DRM_METADATA,  
                                drmMetadataInfoEventListener); 
   
   DRMMetadataInfoEventListener drmMetadataInfoEventListener =  
     new DRMMetadataInfoEventListener() { 
       @Override 
       public void onDRMMetadataInfo(DRMMetadataInfoEvent drmMetadataInfoEvent) { 
           ... 
       } 
   };
   ```

1. を使用して、 `DRMMetadata` 認証が必要かどうかを確認します。

   * 認証が不要な場合は、何も行う必要はなく、再生は中断されずに続行されます。
   * 認証が必要な場合は、DRM認証を完了します。

      この操作は非同期で、別のスレッドで処理されるので、ユーザーインターフェイスやビデオ再生に影響を与えません。

1. 認証に失敗した場合、ユーザーはビデオの表示を続行できず、再生が停止します。

<!--<a id="example_939B95F831A245869F9248E2767F260C"></a>-->

例：

```java
DRMMetadataInfoEventListener drmMetadataInfoEventListener =  
  new DRMMetadataInfoEventListener() { 
    @Override 
    public void onDRMMetadataInfo(DRMMetadataInfoEvent drmMetadataInfoEvent) { 
        final DRMMetadataInfo drmMetadataInfo =  
          drmMetadataInfoEvent.getDRMMetadataInfo(); 
 
        if (drmMetadataInfo == null ||  
          !DRMHelper.isAuthNeeded(drmMetadataInfo.getDRMMetadata())) { 
            return; 
        } 
 
        // Perform DRM auth. 
        // Possible logic might take into consideration a threshold between the  
        // current player time and the DRM metadata start time. For the time being,  
        // we resolve it as soon as we receive the DRM metadata. 
 
        DRMManager drmManager = _mediaPlayer.getDRMManager(); 
        if (drmManager == null) { 
            return; 
        } 
 
        SharedPreferences sharedPreferences =  
          PreferenceManager.getDefaultSharedPreferences(getActivity()); 
        String authUser = sharedPreferences.getString(PrimetimeReference.SETTINGS_DRM_USERNAME,  
          getResources().getString(R.string.drmUsername)); 
        String authPass = sharedPreferences.getString(PrimetimeReference.SETTINGS_DRM_PASSWORD,  
          getResources().getString(R.string.drmPassword)); 
 
        DRMHelper.performDrmAuthentication(drmManager, drmMetadataInfo.getDRMMetadata(),  
          authUser, authPass, new DRMAuthenticationListener() { 
 
            @Override 
            public void onAuthenticationStart() { 
                ... 
            } 
 
            @Override 
            public void onAuthenticationError(int major,  
                                              int minor,  
                                              String erroString,  
                                              String serverErrorURL) { 
                if (getActivity() == null) { 
                    return; 
                } 
                _handler.post(new Runnable() { 
                    @Override 
                    public void run() { 
                        showToast(getString(R.string.drmAuthenticationError)); 
                        getActivity().finish(); 
                    } 
                }); 
            } 
 
            @Override 
            public void onAuthenticationComplete(byte[] authenticationToken) { 
            } 
 
        }); 
    } 
}; 
```

