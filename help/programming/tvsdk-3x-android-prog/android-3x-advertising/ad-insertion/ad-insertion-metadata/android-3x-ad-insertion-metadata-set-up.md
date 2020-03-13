---
description: MetadataNodeクラスを拡張するヘルパークラスAuditudeSettingsを使用して、Adobe Primetime ad decisioningメタデータを設定します。
seo-description: MetadataNodeクラスを拡張するヘルパークラスAuditudeSettingsを使用して、Adobe Primetime ad decisioningメタデータを設定します。
seo-title: 広告挿入メタデータの設定
title: 広告挿入メタデータの設定
uuid: 7400813c-6af0-4c96-a6c7-d9ea1ba6a7b9
translation-type: tm+mt
source-git-commit: 4102780d0c7d0b96d120c1c2b3d14c47bc1b0e6f

---


# 広告挿入メタデータの設定 {#set-up-ad-insertion-metadata}

クラスを拡張するヘル `AuditudeSettings`パークラスを使 `MetadataNode` 用して、Adobe Primetime Ad Decisioningメタデータを設定します。

>[!TIP]
>
>Adobe Primetime ad decisioningは、以前はAuditudeと呼ばれていました。

広告メタデータはプロパティ内に `MediaResource.Metadata` あります。 新しいビデオの再生を開始する際、アプリで正しい広告メタデータを設定する必要があります。

1. インスタンスを作 `AuditudeSettings` 成します。

   ```java
   AuditudeSettings auditudeSettings = new AuditudeSettings();
   ```

1. Adobe Primetime ad decisioning、およびオプションのタ `mediaID`ーゲッ `zoneID`ト設定パ `<ph conkeyref="phrases/primetime-sdk-name"/>`ラメーターを設定します。

   ```java
   auditudeSettings.setZoneId("yourZoneId"); 
   auditudeSettings.setMediaId("yourVideoId"); 
   auditudeSettings.setDefaultMediaId("defVideoId"); 
   auditudeSettings.setDomain("yourAuditudeDomain"); 
   
   // Optionally set user agent  
   auditudeSettings.setUserAgent("yourUserAgent"); 
   
   Metadata targetingParameters = new Metadata(); 
   targetingParameters.setValue("desired_param", "desired_value"); 
   auditudeSettings.setTargetingParameters(targetingParameters);
   ```

   >[!TIP]
   >
   >メディアIDは、TVSDKが文字列として使用し、md5値に変換され、Primetime ad decisioning URLリクエストの値に `u` 使用されます。 例：
   >
   >`https://ad.auditude.com/adserver? **u**=c76d04ee31c91c4ce5c8cee41006c97d &z=114100&l=20150206141527&of=1.4&tm=15&g=1000002`

1. メディアストリ `MediaResource` ームURLと、以前に作成した広告メタデータを使用して、インスタンスを作成します。

   ```java
   MediaResource mediaResource = new MediaResource( 
   "https://example.com/media/test_media.m3u8", MediaResource.Type.HLS, Metadata);
   ```

1. メソッドを使用し `MediaResource` てオブジェクトを読み `MediaPlayer.replaceCurrentResource` 込みます。

   メディア `MediaPlayer` ストリームマニフェストの読み込みと処理を開始します。

1. INITIALIZED状態に移 `MediaPlayer` 行したら、メソッドを使用して、メディアストリームの特性をインスタンスの形 `MediaPlayerItem` 式で取得し `MediaPlayer.CurrentItem` ます。
1. （オプション）代替オーディオトラ `MediaPlayerItem` ックがあるか、ストリームが保護されているかに関係なく、ストリームがライブかどうかをインスタンスに問い合わせます。

   この情報は、再生用のUIを準備するのに役立ちます。 例えば、2つのオーディオトラックがある場合は、これらのトラックを切り替えるUIコントロールを含めることができます。

1. 広告ワー `MediaPlayer.prepareToPlay` クフローを開始するための呼び出し。

   広告が解決され、タイムラインに配置された後、状態 `MediaPlayer` に遷移し `PREPARED` ます。
1. を呼び出 `MediaPlayer.play` して、再生を開始します。
TVSDKは、メディアの再生時に広告を含むようになりました。
