---
description: 広告動作は、カスタマイズまたは上書きできます。
title: カスタマイズされた再生の設定
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 1%

---


# カスタマイズされた再生のセットアップ{#cset-up-customized-playback}

広告ポリシーインスタンスをTVSDKに登録することで、広告の動作をカスタマイズまたは上書きできます。

広告動作をカスタマイズするには、次のいずれかを実行します。

* `AdPolicySelector`インターフェイスとそのすべてのメソッドを実装します。
デフォルトの広告動作をすべて上書きする必要がある場合は、このオプションをお勧めします。

* `DefaultAdPolicySelector`クラスを拡張し、必要な動作に対してのみ実装を提供する
カスタマイズ。
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