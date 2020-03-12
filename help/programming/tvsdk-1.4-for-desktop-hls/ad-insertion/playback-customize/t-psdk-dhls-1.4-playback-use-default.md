---
description: デフォルトの広告動作を使用するように選択できます。
seo-description: デフォルトの広告動作を使用するように選択できます。
seo-title: デフォルトの再生動作の使用
title: デフォルトの再生動作の使用
uuid: 7139384c-167a-4cab-816a-c02fb723a5cb
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# デフォルトの再生動作の使用{#use-the-default-playback-behavior}

デフォルトの広告動作を使用するように選択できます。

デフォルトの動作を使用するには：

    *独自の&#39;ContentFactory&#39;クラスを実装する場合、&#39;doRetrieveAdPolicySelector&#39;の実装に&#39;DefaultAdPolicySelector&#39;の新しいインスタンスを返します。
    
    &quot;
    public class CustomContentFactory extends ContentFactory {
    
    //...
    // your custom code for advertising classes
    //...
    
    /**
    * @Doc
    */
    override protected
    functiondoRetrieveAdPolicySelector(item:MediaPlayerItem):MediaPolicySelector {
    return new DefaultAdPolicySelector(item);}
    
    
    
    
    }inherit Ad Selector*}カスタム`コンテンツを継承しない場合は、`クラスの場合、TVSDKは&#39;DefaultAdPolicySelector&#39;を使用します。