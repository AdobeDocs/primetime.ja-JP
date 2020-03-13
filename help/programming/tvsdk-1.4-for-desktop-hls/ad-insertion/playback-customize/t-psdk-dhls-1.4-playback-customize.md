---
description: 広告の動作は、カスタマイズまたは上書きできます。
seo-description: 広告の動作は、カスタマイズまたは上書きできます。
seo-title: カスタマイズされた再生の設定
title: カスタマイズされた再生の設定
uuid: 479ca1b0-6b3f-42fa-85e1-31d707da8730
translation-type: tm+mt
source-git-commit: a21a5fcc819a7bec58ad36e118d04f462ec3fd92

---


# カスタマイズされた再生の設定{#set-up-customized-playback}

広告の動作は、カスタマイズまたは上書きできます。

広告の動作をカスタマイズまたは上書きする前に、広告ポリシーインスタンスをに登録します。
動作をカスタマイズするには、次のいずれかの操作を行います。

* インターフェイス `AdPolicySelector` とそのすべてのメソッドを実装します。

   すべてのデフォルトの広告動作を上書きする必要がある場合 **は** 、このオプションをお勧めします。

* クラスを拡張 `DefaultAdPolicySelector` し、カスタマイズが必要な動作のみを実装します。

   このオプションは、一部のデフォルトの動作のみを上書きする **必要が** ある場合に推奨されます。

両方のオプションに対して、次のタスクを実行します。

1. 独自のカスタム広告ポリシーセレクターを実装します。

   ```
   public class CustomAdPolicySelector implements AdPolicySelector { 
       // your own customization here 
   }
   ```

1. カスタム広告ポリシーセレクターを使用するようにコンテンツファクトリを拡張します。

   ```
   public class CustomContentFactory extends DefaultContentFactory { 
       /** 
        * @inheritDoc 
        */ 
       override protected function doRetrieveAdPolicySelector(item:MediaPlayerItem):AdPolicySelector { 
           return new CustomAdPolicySelector(item); 
       } 
   }
   ```

   ```
   psdkutils::PSDKSharedPointer<psdk::ContentFactory> factory; 
   psdkFactory->createDefaultContentFactory(&factory); 
   psdkutils::PSDKSharedPointer<psdk::AdPolicySelector> defaultAdPolicySelector; 
   factory->retrieveAdPolicySelector(item, &defaultAdPolicySelector);
   ```

1. TVSDKが広告ワークフローで使用する新しいコンテンツファクトリを登録します。

   ```
   PSDKConfig.advertisingFactory = new CustomContentFactory();
   ```

   >[!TIP]
   >
   >カスタムコンテンツファクトリがクラスを通じて特定のストリームに登録され `MediaPlayerItemConfig` た場合、インスタンスの割り当てが解除されると `MediaPlayer` クリアされます。 新しい再生セッションが作成されるたびに、アプリケーションで登録する必要があります。