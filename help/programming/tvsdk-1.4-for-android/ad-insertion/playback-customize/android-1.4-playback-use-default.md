---
description: デフォルトの広告動作を使用するように選択できます。
title: デフォルトの再生動作の使用
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '60'
ht-degree: 0%

---


# デフォルトの再生動作{#use-the-default-playback-behavior}を使用

デフォルトの広告動作を使用するように選択できます。

デフォルトの動作を使用するには：

    *独自の&#39;AdvertisingFactory&#39;クラスを実装している場合、&#39;createAdPolicySelector&#39;に対してnullを返します。
    
    * &#39;AdvertisingFactory&#39;クラスのカスタム実装がない場合、TVSDKはデフォルトの広告ポリシーセレクターを使用します。