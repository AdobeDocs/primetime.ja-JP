---
description: デフォルトの広告動作を使用するように選択できます。
title: デフォルトの再生動作を使用
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '60'
ht-degree: 0%

---

# デフォルトの再生動作を使用 {#use-the-default-playback-behavior}

デフォルトの広告動作を使用するように選択できます。

デフォルトの動作を使用するには：

    *独自の「AdvertisingFactory」クラスを実装する場合、「createAdPolicySelector」に null を返します。
    
    * 「AdvertisingFactory」クラスのカスタム実装がない場合、 TVSDK はデフォルトの広告ポリシーセレクターを使用します。
