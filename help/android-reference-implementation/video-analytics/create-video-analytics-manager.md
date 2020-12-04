---
description: ビデオ分析マネージャーの作成
seo-description: ビデオ分析マネージャーの作成
seo-title: ビデオ分析マネージャーの作成
title: ビデオ分析マネージャーの作成
uuid: d72e1dfe-df70-47cc-9e00-bd09017d6127
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '118'
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

