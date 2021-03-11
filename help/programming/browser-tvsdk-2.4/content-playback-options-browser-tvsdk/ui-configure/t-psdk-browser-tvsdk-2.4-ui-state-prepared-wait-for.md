---
description: ブラウザーTVSDKプレイヤーのほとんどのメソッドを使用する前に、プレイヤーが有効な状態にある必要があります。
title: 有効な状態を待つ
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '130'
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

