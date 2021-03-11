---
description: デフォルトの広告動作を使用するように選択できます。
title: デフォルトの再生動作の使用
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '58'
ht-degree: 0%

---


# デフォルトの再生動作{#use-the-default-playback-behavior}を使用

デフォルトの広告動作を使用するように選択できます。

デフォルトの動作を使用するには：

* 独自の`ContentFactory`クラスを実装する場合は、`doRetrieveAdPolicySelector`の実装に`DefaultAdPolicySelector`の新しいインスタンスを返します。

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

* `ContentFactory`クラスのカスタム実装がない場合、TVSDKは`DefaultAdPolicySelector`を使用します。