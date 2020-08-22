---
description: 広告動作は、カスタマイズまたは上書きできます。
seo-description: 広告動作は、カスタマイズまたは上書きできます。
seo-title: カスタマイズされた再生の設定
title: カスタマイズされた再生の設定
uuid: 9cbf0bcf-7932-409e-a690-e79f284eaf74
translation-type: tm+mt
source-git-commit: 23a48208ac1d3625ae7d925ab6bfba8f2a980766
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 1%

---


# カスタマイズされた再生の設定 {#cset-up-customized-playback}

広告ポリシーインスタンスをTVSDKに登録することで、広告の動作をカスタマイズまたは上書きできます。

広告動作をカスタマイズするには、次のいずれかを実行します。

* インターフェイスとそのすべてのメソッドを実装し `AdPolicySelector` ます。
デフォルトの広告動作をすべて上書きする必要がある場合は、このオプションをお勧めします。

* クラスを拡張し、カスタマイズが必要な動作のみに実装を提供します。 `DefaultAdPolicySelector` 
一部のデフォルトの動作のみを上書きする必要がある場合は、このオプションをお勧めします。

両方のオプションに対して、次のタスクを実行します。

広告動作をカスタマイズするには：

1. AdPolicySelectorインターフェイスとそのすべてのメソッドを実装します。

1. TVSDKが使用するポリシーインスタンスを、広告ファクトリを介して割り当てます。

>[!IMPORTANT]
>
>>playbackの開始時に登録されるカスタム広告ポリシーは、MediaPlayerインスタンスが>割り当て解除されるとクリアされます。新しい再生セッションが作成されるたびに、アプリケーションがポリシー/セレクターインスタンスを登録する必要があります。

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