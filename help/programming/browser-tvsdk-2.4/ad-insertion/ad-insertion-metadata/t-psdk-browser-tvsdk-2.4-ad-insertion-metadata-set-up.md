---
description: Adobe Primetime ad decisioningメタデータを設定するには、ヘルパークラスAuditudeSettingsを使用します。
seo-description: Adobe Primetime ad decisioningメタデータを設定するには、ヘルパークラスAuditudeSettingsを使用します。
seo-title: 広告挿入メタデータの設定
title: 広告挿入メタデータの設定
uuid: fc37e0ae-6acf-4a78-a468-f7b5b123b45e
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# 広告挿入メタデータの設定{#set-up-ad-insertion-metadata}

Adobe Primetime ad decisioningメタデータを設定するには、ヘルパークラスAuditudeSettingsを使用します。

>[!TIP]
>
>Adobe Primetime ad decisioningは、以前はAuditudeと呼ばれていました。

1. インスタンスを作 `AuditudeSettings` 成します。

   ```java
   AuditudeSettings auditudeSettings = new AuditudeSettings();
   ```

1. Adobe Primetime ad decisioningのmediaID、zoneID、domainおよびオプションのターゲティングパラメーターを設定します。

   ```js
   auditudeSettings.domain = "yourdomain"; 
   auditudeSettings.mediaId = "mediaid"; 
   auditudeSettings.zoneId = "zoneid";
   ```

1. メディアストリ `MediaResource` ームURLと、以前に作成した広告メタデータを使用して、インスタンスを作成します。

   ```js
   mediaResource = new AdobePSDK.MediaResource ( 
         resourceUrl, 
         resourceType,  
         auditudeSettings);
   ```

1. メソッドを使用し `MediaResource` てオブジェクトを読み `MediaPlayer.replaceCurrentResource(resource)` 込みます。

   メディア `MediaPlayer` ストリームマニフェストの読み込みと処理を開始します。

1. INITIALIZED状態に `MediaPlayer` 移行したら、属性を介して、メディアストリームの特性をインスタンスの形 `MediaPlayerItem` 式で取得し `MediaPlayer.CurrentItem` ます。
1. （オプション）代替オーディオトラ `MediaPlayerItem` ックがあるかどうかに関係なく、ストリームがライブかどうかを調べるためにインスタンスをクエリします。

   この情報は、再生用のUIを準備するのに役立ちます。 例えば、2つのオーディオトラックがある場合は、これらのトラックを切り替えるUIコントロールを含めることができます。

1. 広告ワー `MediaPlayer.prepareToPlay` クフローを開始するための呼び出し。

   広告が解決され、タイムラインに配置された後、PREPARED `  MediaPlayer ` 状態に移行します。
1. を呼び出 `MediaPlayer.play` して、再生を開始します。
メディアの再生時に、ブラウザーTVSDKに広告が含まれるようになりました。
