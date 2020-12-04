---
description: ブラウザーTVSDKプレイヤーのほとんどのメソッドを使用する前に、プレイヤーが有効な状態にある必要があります。
seo-description: ブラウザーTVSDKプレイヤーのほとんどのメソッドを使用する前に、プレイヤーが有効な状態にある必要があります。
seo-title: 有効な状態を待つ
title: 有効な状態を待つ
uuid: 0add29a8-fbd8-483a-8c99-e4bc6de9e3d3
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---


# 有効な状態を待つ{#wait-for-a-valid-state}

ブラウザーTVSDKプレイヤーのほとんどのメソッドを使用する前に、プレイヤーが有効な状態にある必要があります。

プレイヤーは様々な状態を移動します。 プレイヤーが正しい状態になるのを待つことで、メディアリソースが正常に読み込まれたことが確認されます。 プレイヤーが少なくとも必要な状態にない場合は、多くのプレーヤーメソッドは`IllegalStateException`をスローします。

必要な状態は、通常PREPAREDです。

1. 状態がPREPAREDであることを確認するには：

   プレイヤーが初期化を進めているときに、ブラウザーTVSDKが`AdobePSDK.MediaPlayerStatusChangeEvent`イベントをディスパッチするまで待ち、`event.status`が`MediaPlayerStatus.PREPARED`の状態になります。

   MediaPlayerオブジェクトの現在の状態がPREPARED以上であるかどうかを確認するには、次のように記述します。

   ```
   <readonly> status :AdobePSDK.MediaPlayerStatus
   ```

