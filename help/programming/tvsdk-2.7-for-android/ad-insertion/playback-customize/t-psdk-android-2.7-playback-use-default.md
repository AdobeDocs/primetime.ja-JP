---
description: デフォルトの広告動作を使用するように選択できます。
seo-description: デフォルトの広告動作を使用するように選択できます。
seo-title: デフォルトの再生動作の使用
title: デフォルトの再生動作の使用
uuid: 20785251-eb2f-4cc0-b919-1a88c0b1c57c
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# デフォルトの再生動作の使用 {#use-the-default-playback-behavior}

デフォルトの広告動作を使用するように選択できます。

1. デフォルトの動作を使用するには、次のいずれかのタスクを実行します。

   * 独自のクラスを実装する `AdvertisingFactory` 場合は、に対してnullを返しま `createAdPolicySelector`す。

   * クラスのカスタム実装がない場合、TVSDKはデフォ `AdvertisingFactory` ルトの広告ポリシーセレクターを使用します。

## カスタマイズされた再生の設定 {#set-up-customized-playback}

広告の動作は、カスタマイズまたは上書きできます。

広告の動作をカスタマイズまたは上書きする前に、広告ポリシーインスタンスをTVSDKに登録します。

* インターフェイス `AdPolicySelector` とそのすべてのメソッドを実装します。

   すべてのデフォルトの広告動作を上書きする必要がある場合 **は** 、このオプションをお勧めします。

* クラスを拡張 `DefaultAdPolicySelector` し、カスタマイズが必要な動作のみを実装します。

   このオプションは、一部のデフォルトの動作のみを上書きする **必要が** ある場合に推奨されます。

動作をカスタマイズするには：

1. インターフェイス `AdPolicySelector` とそのすべてのメソッドを実装します。
1. TVSDKが広告ファクトリを介して使用するポリシーインスタンスを割り当てます。

   >[!NOTE]
   >
   >再生の開始時に登録されたカスタム広告ポリシーは、インスタンスの割り当てが解除され `MediaPlayer` るとクリアされます。 新しい再生セッションが作成されるたびに、アプリケーションでポリシーセレクターインスタンスを登録する必要があります。

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