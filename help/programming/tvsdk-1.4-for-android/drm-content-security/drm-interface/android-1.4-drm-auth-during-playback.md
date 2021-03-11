---
description: ビデオのDRMメタデータがメディアストリームに含まれている場合、再生中に認証を実行します。
title: 再生中のDRM認証
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# 再生中のDRM認証{#drm-authentication-during-playback}

ビデオのDRMメタデータがメディアストリームに含まれている場合、再生中に認証を実行します。

アセットが複数のDRMライセンスで暗号化される場合は、ライセンスローテーション機能を考慮します。 新しいDRMメタデータが見つかるたびに、`DRMHelper`メソッドを使用して、DRMメタデータにDRM認証が必要かどうかを確認します。

>[!NOTE]
>
>このチュートリアルでは、ドメインバインドライセンスは扱いません。 理想的には、再生を開始する前に、ドメインバウンドライセンスを扱うかどうかを確認します。 ドメイン認証が必要な場合は、ドメイン認証を実行し（必要に応じて）、ドメインに参加します。

1. アセットに新しいDRMメタデータが見つかると、アプリケーションレイヤーでイベントがディスパッチされます。

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

1. `DRMMetadata`を使用して、認証が必要かどうかを確認します。 そうでなければ、何もしない。再生は途切れることなく続行されます。
1. それ以外の場合は、DRM認証を実行します。 この操作は非同期的で、別のスレッドで処理されるので、ユーザーインターフェイスやビデオ再生に影響しません。
1. 認証に失敗した場合、ユーザーはビデオの視聴を続行できず、再生は中止されます。 そうしないと、再生は途切れずに続行されます。

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
