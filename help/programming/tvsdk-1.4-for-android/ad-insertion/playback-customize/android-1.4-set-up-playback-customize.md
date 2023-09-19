---
description: 広告の動作をカスタマイズまたは上書きできます。
title: カスタマイズされた再生の設定
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# カスタマイズされた再生の設定 {#cset-up-customized-playback}

広告ポリシーインスタンスを TVSDK に登録することで、広告の動作をカスタマイズまたは上書きできます。

広告の動作をカスタマイズするには、次のいずれかの操作を行います。

* の実装 `AdPolicySelector` インターフェイスおよびそのすべてのメソッド。
デフォルトの広告動作をすべて上書きする必要がある場合は、このオプションをお勧めします。

* の拡張 `DefaultAdPolicySelector` クラスを作成し、カスタマイズが必要な動作に対してのみ実装を提供します。
デフォルトの動作の一部のみを上書きする必要がある場合は、このオプションを選択することをお勧めします。

両方のオプションについて、次のタスクを実行します。

広告の動作をカスタマイズするには：

1. AdPolicySelector インターフェイスとそのすべてのメソッドを実装します。

1. 広告ファクトリを通じて、TVSDK が使用するポリシーインスタンスを割り当てます。

>[!IMPORTANT]
>
>再生の開始時に登録されるカスタム広告ポリシーは、MediaPlayer インスタンスの割り当てが解除されるとクリアされます。新しい再生セッションが作成されるたびに、アプリケーションはポリシー/セレクターインスタンスを登録する必要があります。

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

1. カスタマイズ機能を実装します。
