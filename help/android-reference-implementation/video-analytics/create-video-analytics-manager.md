---
description: ビデオ分析マネージャーの作成
seo-description: ビデオ分析マネージャーの作成
seo-title: ビデオ分析マネージャーの作成
title: ビデオ分析マネージャーの作成
uuid: d72e1dfe-df70-47cc-9e00-bd09017d6127
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# ビデオ分析マネージャーの作成 {#create-the-video-analytics-manager}

新しいマネージャークラ `VAManager`ス()がAndroidリファレンスの実装に追加されました。 `VAManager` クラスのインスタンスを作成し、破棄 `VideoHeartbeat` します。 参照実装は、新しいインスタ `VAManager` ンスが作成されると `MediaPlayer` インスタンスを作成し、破棄されるとそのインスタンスを破 `MediaPlayer` 棄します。 これは、で実装されま `PlayerFragment.java`す。

## 新しいビデオ分析マネージャーを作成するには

```java
VAManager vaManager = ManagerFactory.getVAManager(true, config, mediaPlayer);  
vaManager.createVAProvider(getActivity().getApplicationContext()); 
```

config変数は、の具体的な実装で、ランタ `IVAConfig` イム設定が含まれ `VideoHeartbeat` ます。

>[!NOTE]
>
>AndroidアプリケーションがAdobe Analyticsアカウントを使用して設定されていない場合、のインスタンスが作成され有効になっていても、ビデオトラッキングデータ `VAManager` は生成されません。

