---
description: デフォルトの広告動作を使用するように選択できます。
seo-description: デフォルトの広告動作を使用するように選択できます。
seo-title: デフォルトの再生動作の使用
title: デフォルトの再生動作の使用
uuid: 7139384c-167a-4cab-816a-c02fb723a5cb
translation-type: tm+mt
source-git-commit: 1985694f99c548284aad6e6b4e070bece230bdf4
workflow-type: tm+mt
source-wordcount: '71'
ht-degree: 0%

---


# デフォルトの再生動作の使用{#use-the-default-playback-behavior}

デフォルトの広告動作を使用するように選択できます。

デフォルトの動作を使用するには：

* 独自の `ContentFactory` クラスを実装する場合は、の実装内にの新しいインスタンス `DefaultAdPolicySelector` を返し `doRetrieveAdPolicySelector`ます。

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

* クラスのカスタム実装がない場合、TVSDKは `ContentFactory` を使用し `DefaultAdPolicySelector`ます。