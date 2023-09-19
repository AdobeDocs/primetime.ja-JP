---
description: ビデオ分析マネージャーの作成
title: ビデオ分析マネージャーの作成
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 0%

---

# ビデオ分析マネージャーの作成 {#create-the-video-analytics-manager}

新しいマネージャクラス ( `VAManager`) が Android リファレンス実装に追加されました。 `VAManager` 単にのインスタンスを作成し、破棄する `VideoHeartbeat` クラス。 参照実装によって `VAManager` 新しい `MediaPlayer` が作成され、そのインスタンスが破棄されたときに、 `MediaPlayer` が破壊されました。 これは、で実装されます。 `PlayerFragment.java`.

## 新しいビデオ分析マネージャーを作成するには

```java
VAManager vaManager = ManagerFactory.getVAManager(true, config, mediaPlayer);  
vaManager.createVAProvider(getActivity().getApplicationContext()); 
```

config 変数は、 `IVAConfig` とにはランタイムが含まれます。 `VideoHeartbeat` 設定。

>[!NOTE]
>
>Android アプリケーションにAdobe Analyticsアカウントが設定されていない場合、ビデオトラッキングデータは生成されません ( `VAManager` が作成され、有効になっている。
