---
description: ビデオのDRMメタデータがメディアストリームに含まれる場合、再生中に認証を実行します。
seo-description: ビデオのDRMメタデータがメディアストリームに含まれる場合、再生中に認証を実行します。
seo-title: 再生中のDRM認証
title: 再生中のDRM認証
uuid: a1a63e3e-be34-49e1-96c4-ae266003b3d1
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# 再生中のDRM認証 {#drm-authentication-during-playback}

ビデオのDRMメタデータがメディアストリームに含まれる場合、再生中に認証を実行します。

アセットが複数のDRMライセンスで暗号化されるライセンスローテーション機能について考えてみます。 新しいDRMメタデータが見つかるたびに、メソッドを使用し `DRMHelper` て、DRMメタデータにDRM認証が必要かどうかを確認します。

>[!NOTE]
>
>このチュートリアルでは、ドメインバインドライセンスは扱いません。 再生を開始する前に、ドメインバインドライセンスを扱っているかどうかを確認するのが理想的です。 ドメイン認証が必要な場合は、ドメイン認証を実行し（必要に応じて）、ドメインに参加します。

1. アセット内で新しいDRMメタデータが見つかると、アプリケーションレイヤーでイベントがディスパッチされます。

   ```java
   mediaPlayer.addEventListener(MediaPlayerEvent.DRM_METADATA,  
                                drmMetadataInfoEventListener); 
   
   DRMMetadataInfoEventListener drmMetadataInfoEventListener =  
     new DRMMetadataInfoEventListener() { 
           @Override 
           public void onDRMMetadataInfo(DRMMetadataInfoEvent drmMetadataInfoEvent) { 
           } 
   };
   ```

1. を使用して、 `DRMMetadata` 認証が必要かどうかを確認します。 そうでない場合は、何もしない。再生は途切れずに続行します。
1. それ以外の場合は、DRM認証を実行します。 この操作は非同期で、別のスレッドで処理されるので、ユーザーインターフェイスやビデオ再生に影響を与えません。
1. 認証に失敗した場合、ユーザーはビデオの表示を続行できず、再生が停止します。 そうしないと、再生は途切れずに続行されます。

```java
DRMMetadataInfoEventListener drmMetadataInfoEventListener =  
  new DRMMetadataInfoEventListener() { 
    @Override 
    public void onDRMMetadataInfo(DRMMetadataInfoEvent drmMetadataInfoEvent) { 
        final DRMMetadataInfo drmMetadataInfo = drmMetadataInfoEvent.getDRMMetadataInfo(); 
 
        if (drmMetadataInfo == null || !DRMHelper.isAuthNeeded(drmMetadataInfo.getDRMMetadata())) { 
            return; 
        } 
 
        // Perform DRM auth. 
        // Possible logic might take into consideration a threshold between the current player time and the 
        // DRM metadata start time. For the time being, we resolve it as soon as we receive the DRM metadata. 
 
        DRMManager drmManager = _mediaPlayer.getDRMManager(); 
        if (drmManager == null) { 
            return; 
        } 
 
        SharedPreferences sharedPreferences = PreferenceManager.getDefaultSharedPreferences(getActivity()); 
        String authUser = sharedPreferences.getString(PrimetimeReference.SETTINGS_DRM_USERNAME,  
          getResources().getString(R.string.drmUsername)); 
          String authPass = sharedPreferences.getString(PrimetimeReference.SETTINGS_DRM_PASSWORD,  
          getResources().getString(R.string.drmPassword)); 
 
        DRMHelper.performDrmAuthentication(drmManager, drmMetadataInfo.getDRMMetadata(),  
          authUser, authPass, new DRMAuthenticationListener() { 
 
            @Override 
            public void onAuthenticationStart() { 
            } 
 
            @Override 
            public void onAuthenticationError(int major, int minor, String erroString, String serverErrorURL) { 
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
