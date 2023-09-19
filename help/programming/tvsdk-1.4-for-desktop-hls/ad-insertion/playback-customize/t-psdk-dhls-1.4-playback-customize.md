---
description: 広告の動作をカスタマイズまたは上書きできます。
title: カスタマイズされた再生の設定
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# カスタマイズされた再生の設定{#set-up-customized-playback}

広告の動作をカスタマイズまたは上書きできます。

広告の動作をカスタマイズまたは上書きする前に、広告ポリシーインスタンスをに登録します。
広告の動作をカスタマイズするには、次のいずれかの操作を行います。

* の実装 `AdPolicySelector` インターフェイスおよびそのすべてのメソッド。

  このオプションは、 **すべて** デフォルトの広告の動作です。

* の拡張 `DefaultAdPolicySelector` クラスを作成し、カスタマイズが必要な動作に対してのみ実装を提供します。

  このオプションは、 **some** のデフォルトの動作を設定します。

両方のオプションについて、次のタスクを実行します。

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

1. TVSDK が広告ワークフローで使用する新しいコンテンツファクトリを登録します。

   ```
   PSDKConfig.advertisingFactory = new CustomContentFactory();
   ```

   >[!TIP]
   >
   >カスタムコンテンツファクトリが、 `MediaPlayerItemConfig` クラス、次の時点でクリアされます `MediaPlayer` インスタンスの割り当てが解除されました。 新しい再生セッションが作成されるたびに、アプリケーションを登録する必要があります。
