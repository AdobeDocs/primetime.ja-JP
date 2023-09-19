---
description: デフォルトの広告動作を使用するように選択できます。
title: デフォルトの再生動作を使用
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---

# デフォルトの再生動作を使用  {#use-the-default-playback-behavior}

デフォルトの広告動作を使用するように選択できます。

1. デフォルトの動作を使用するには、次のいずれかのタスクを実行します。

   * 独自の `AdvertisingFactory` クラスは、の null を返します。 `createAdPolicySelector`.

   * のカスタム実装がない場合、 `AdvertisingFactory` クラスの場合、 TVSDK はデフォルトの広告ポリシーセレクターを使用します。

## カスタマイズされた再生の設定 {#set-up-customized-playback}

広告の動作をカスタマイズまたは上書きできます。

広告の動作をカスタマイズまたは上書きする前に、広告ポリシーインスタンスを TVSDK に登録します。

* の実装 `AdPolicySelector` インターフェイスおよびそのすべてのメソッド。

  このオプションは、 **すべて** デフォルトの広告の動作です。

* の拡張 `DefaultAdPolicySelector` クラスを作成し、カスタマイズが必要な動作に対してのみ実装を提供します。

  このオプションは、 **some** のデフォルトの動作を設定します。

広告の動作をカスタマイズするには：

1. の実装 `AdPolicySelector` インターフェイスとそのすべてのメソッド。
1. 広告ファクトリを通じて、TVSDK が使用するポリシーインスタンスを割り当てます。

   >[!NOTE]
   >
   >再生開始時に登録されるカスタム広告ポリシーは、 `MediaPlayer` インスタンスの割り当てが解除されました。 新しい再生セッションが作成されるたびに、アプリケーションはポリシーセレクターインスタンスを登録する必要があります。

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

1. カスタマイズ機能を実装します。
