---
description: 広告動作は、カスタマイズまたは上書きできます。
title: カスタマイズされた再生の設定
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---


# カスタマイズされた再生の設定{#set-up-customized-playback}

広告動作は、カスタマイズまたは上書きできます。

広告動作をカスタマイズまたは上書きする前に、に広告ポリシーインスタンスを登録します。
広告動作をカスタマイズするには、次のいずれかを実行します。

* `AdPolicySelector`インターフェイスとそのすべてのメソッドを実装します。

   デフォルトの広告動作&#x200B;**すべての**&#x200B;を上書きする必要がある場合は、このオプションをお勧めします。

* `DefaultAdPolicySelector`クラスを拡張し、カスタマイズが必要な動作のみに実装を提供します。

   デフォルトの動作の&#x200B;**一部**&#x200B;のみを上書きする必要がある場合は、このオプションをお勧めします。

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

1. 広告ワークフローでTVSDKが使用する新しいコンテンツファクトリを登録します。

   ```
   PSDKConfig.advertisingFactory = new CustomContentFactory();
   ```

   >[!TIP]
   >
   >カスタムコンテンツファクトリが`MediaPlayerItemConfig`クラスを通じて特定のストリームに登録された場合、`MediaPlayer`インスタンスの割り当てが解除されるとクリアされます。 新しい再生セッションが作成されるたびに、アプリケーションでそのセッションを登録する必要があります。