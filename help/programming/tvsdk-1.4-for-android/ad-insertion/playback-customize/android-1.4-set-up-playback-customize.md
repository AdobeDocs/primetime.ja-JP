---
description: 広告の動作は、カスタマイズまたは上書きできます。
seo-description: 広告の動作は、カスタマイズまたは上書きできます。
seo-title: カスタマイズされた再生の設定
title: カスタマイズされた再生の設定
uuid: 9cbf0bcf-7932-409e-a690-e79f284eaf74
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# カスタマイズされた再生の設定 {#cset-up-customized-playback}

広告ポリシーインスタンスをTVSDKに登録することで、広告の動作をカスタマイズまたは上書きできます。

動作をカスタマイズするには、次のいずれかの操作を行います。

* インターフェイス `AdPolicySelector` とそのすべてのメソッドを実装します。
すべてのデフォルトの広告動作を上書きする必要がある場合は、このオプションをお勧めします。

* クラスを拡張 `DefaultAdPolicySelector` し、カスタマイズが必要な動作のみを実装します。
このオプションは、一部のデフォルトの動作のみを上書きする必要がある場合に推奨されます。

両方のオプションに対して、次のタスクを実行します。

動作をカスタマイズするには：

1. AdPolicySelectorインターフェイスとそのすべてのメソッドを実装します。

1. TVSDKが広告ファクトリを介して使用するポリシーインスタンスを割り当てます。

>[!ATTENTION]
>
>>playbackの開始時に登録されたカスタム広告ポリシーは、MediaPlayerインスタンスが>割り当て解除されるとクリアされます。新しい再生セッションが作成されるたびに、アプリケーションがポリシー>セレクターインスタンスを登録する必要があります。

例：

```
    class CustomContentFactory extends ContentFactory {
     ...
    @Override
    public AdPolicySelector retrieveAdPolicySelector(MediaPlayerItem mediaPlayerItem) {
    return new CustomAdPolicySelector(mediaPlayerItem);
    }
     ...
    }
    TVSDK 1.4 for Android Programmer's Guide 46
    // register the custom content factory with media player
    MediaPlayerItemConfig config = new MediaPlayerItemConfig();
    config.setAdvertisingFactory(new CustomContentFactory());
    // this config will should be later passed while loading the resource
    mediaPlayer.replaceCurrentResource(resource, config);
```

1. カスタマイズを実装します。