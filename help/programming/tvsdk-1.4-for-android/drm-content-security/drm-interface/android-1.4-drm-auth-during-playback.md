---
description: ビデオの DRM メタデータがメディアストリームに含まれている場合は、再生中に認証を実行します。
title: 再生中の DRM 認証
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# 再生中の DRM 認証 {#drm-authentication-during-playback}

ビデオの DRM メタデータがメディアストリームに含まれている場合は、再生中に認証を実行します。

アセットが複数の DRM ライセンスで暗号化されるライセンスローテーション機能を検討します。 新しい DRM メタデータが検出されるたびに、 `DRMHelper` DRM メタデータに DRM 認証が必要かどうかを確認するためのメソッド。

>[!NOTE]
>
>このチュートリアルでは、ドメインバインドライセンスを処理しません。 再生を開始する前に、ドメインバウンドライセンスを扱っているかどうかを確認するのが理想的です。 ドメイン認証を実行し（必要に応じて）、ドメインに参加します。

1. アセットで新しい DRM メタデータが検出されると、アプリケーションレイヤーでイベントがディスパッチされます。

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

1. 以下を使用します。 `DRMMetadata` 認証が必要かどうかを確認します。 そうでない場合は何もしないでください。再生は途切れずに続きます。
1. それ以外の場合は、DRM 認証を実行します。 この操作は非同期で、別のスレッドで処理されるので、ユーザーインターフェイスやビデオ再生には影響しません。
1. 認証に失敗した場合、ユーザーはビデオの視聴を続行できず、再生が停止します。 そうしないと、再生は途切れずに続行されます。

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
