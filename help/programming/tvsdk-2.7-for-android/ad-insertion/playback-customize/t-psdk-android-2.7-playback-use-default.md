---
description: デフォルトの広告動作を使用するように選択できます。
seo-description: デフォルトの広告動作を使用するように選択できます。
seo-title: デフォルトの再生動作の使用
title: デフォルトの再生動作の使用
uuid: 20785251-eb2f-4cc0-b919-1a88c0b1c57c
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---


# デフォルトの再生動作{#use-the-default-playback-behavior}を使用

デフォルトの広告動作を使用するように選択できます。

1. デフォルトの動作を使用するには、次のタスクのいずれかを実行します。

   * 独自の`AdvertisingFactory`クラスを実装する場合、`createAdPolicySelector`に対してnullを返します。

   * `AdvertisingFactory`クラスのカスタム実装がない場合、TVSDKはデフォルトの広告ポリシーセレクターを使用します。

## カスタマイズ再生の設定{#set-up-customized-playback}

広告動作は、カスタマイズまたは上書きできます。

広告動作をカスタマイズまたは上書きする前に、広告ポリシーインスタンスをTVSDKに登録します。

* `AdPolicySelector`インターフェイスとそのすべてのメソッドを実装します。

   デフォルトの広告動作&#x200B;**すべての**&#x200B;を上書きする必要がある場合は、このオプションをお勧めします。

* `DefaultAdPolicySelector`クラスを拡張し、カスタマイズが必要な動作のみに実装を提供します。

   デフォルトの動作の&#x200B;**一部**&#x200B;のみを上書きする必要がある場合は、このオプションをお勧めします。

広告動作をカスタマイズするには：

1. `AdPolicySelector`インターフェイスとそのすべてのメソッドを実装します。
1. TVSDKが使用するポリシーインスタンスを、広告ファクトリを介して割り当てます。

   >[!NOTE]
   >
   >再生開始時に登録されるカスタム広告ポリシーは、`MediaPlayer`インスタンスの割り当てが解除されるとクリアされます。 新しい再生セッションが作成されるたびに、ポリシーセレクターインスタンスをアプリケーションで登録する必要があります。

   例：

   ```java
   class CustomContentFactory extends ContentFactory { 
       ... 
       @Override 
       public AdPolicySelector retrieveAdPolicySelector(MediaPlayerItem mediaPlayerItem) { 
           return new CustomAdPolicySelector(mediaPlayerItem); 
       } 
       ... 
   } 
   
   // register the custom content factory with media player 
   MediaPlayerItemConfig config =  new MediaPlayerItemConfig(); 
   config.setAdvertisingFactory(new CustomContentFactory()); 
   
   // this config will should be later passed while loading the resource 
   mediaPlayer.replaceCurrentResource(resource, config);
   ```

1. カスタマイズを実装します。