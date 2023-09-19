---
description: デフォルトの広告動作を使用するように選択できます。
title: デフォルトの再生動作を使用
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '58'
ht-degree: 0%

---

# デフォルトの再生動作を使用{#use-the-default-playback-behavior}

デフォルトの広告動作を使用するように選択できます。

デフォルトの動作を使用するには：

* 独自の `ContentFactory` クラスで、 `DefaultAdPolicySelector` の実装 `doRetrieveAdPolicySelector`.

  ```
  public class CustomContentFactory extends ContentFactory { 
  
      //... 
      // your custom code for advertising classes 
      //... 
  
      /** 
       * @inheritDoc 
       */ 
      override protected function  
        doRetrieveAdPolicySelector(item:MediaPlayerItem):AdPolicySelector { 
          return new DefaultAdPolicySelector(item); 
      } 
  }
  ```

* のカスタム実装がない場合、 `ContentFactory` クラス、 TVSDK は `DefaultAdPolicySelector`.
