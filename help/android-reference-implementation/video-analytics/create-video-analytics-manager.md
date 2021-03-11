---
description: ビデオ分析マネージャーの作成
title: ビデオ分析マネージャーの作成
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 0%

---


# ビデオ分析マネージャーの作成{#create-the-video-analytics-manager}

新しいマネージャークラス(`VAManager`)がAndroidリファレンスの実装に追加されました。 `VAManager` クラスのインスタンスを作成し、破棄するだけで `VideoHeartbeat` す。参照実装は、新しい`MediaPlayer`が作成されると`VAManager`インスタンスを作成し、`MediaPlayer`が破棄されるとそのインスタンスを破棄します。 これは`PlayerFragment.java`に実装されています。

## 新しいビデオ分析マネージャーを作成するには

```java
VAManager vaManager = ManagerFactory.getVAManager(true, config, mediaPlayer);  
vaManager.createVAProvider(getActivity().getApplicationContext()); 
```

config変数は、`IVAConfig`の具体的な実装で、ランタイム`VideoHeartbeat`の設定が含まれています。

>[!NOTE]
>
>AndroidアプリケーションがAdobe Analyticsアカウントで設定されていない場合、`VAManager`のインスタンスが作成され、有効になっていても、ビデオトラッキングデータは生成されません。

