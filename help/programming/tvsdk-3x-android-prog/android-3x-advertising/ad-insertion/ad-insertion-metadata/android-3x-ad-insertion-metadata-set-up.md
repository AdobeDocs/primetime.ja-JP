---
description: MetadataNodeクラスを拡張するヘルパークラスAuditudeSettingsを使用して、Adobe PrimetimeAd Decisioningメタデータを設定します。
title: 広告挿入メタデータの設定
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---


# 広告挿入メタデータの設定{#set-up-ad-insertion-metadata}

`MetadataNode`クラスを拡張するヘルパークラス`AuditudeSettings`を使用して、Adobe PrimetimeAd Decisioningメタデータを設定します。

>[!TIP]
>
>Adobe Primetimead decisioningは、以前はAuditudeと呼ばれていました。

広告メタデータは`MediaResource.Metadata`プロパティにあります。 新しいビデオの再生を開始する場合、アプリケーションで正しい広告メタデータを設定する必要があります。

1. `AuditudeSettings`インスタンスを構築します。

   ```java
   AuditudeSettings auditudeSettings = new AuditudeSettings();
   ```

1. Adobe Primetimead decisioning `mediaID`、`zoneID`、`<ph conkeyref="phrases/primetime-sdk-name"/>`およびオプションのターゲティングパラメーターを設定します。

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
   >メディアIDはTVSDKで文字列として使用され、md5値に変換され、Primetime ad decisioning URLリクエストの`u`値に使用されます。 例：
   >
   >`https://ad.auditude.com/adserver? **u**=c76d04ee31c91c4ce5c8cee41006c97d &z=114100&l=20150206141527&of=1.4&tm=15&g=1000002`

1. メディアストリームURLと以前に作成した広告メタデータを使用して`MediaResource`インスタンスを作成します。

   ```java
   MediaResource mediaResource = new MediaResource( 
   "https://example.com/media/test_media.m3u8", MediaResource.Type.HLS, Metadata);
   ```

1. `MediaResource`オブジェクトを`MediaPlayer.replaceCurrentResource`メソッドを使用して読み込みます。

   `MediaPlayer`開始は、メディアストリームマニフェストを読み込み、処理します。

1. `MediaPlayer`トランジションがINITIALIZED状態になったら、`MediaPlayer.CurrentItem`メソッドを使用して`MediaPlayerItem`インスタンスの形式でメディアストリームの特性を取得します。
1. （オプション）`MediaPlayerItem`インスタンスをクエリして、代替オーディオトラックがあるか、ストリームが保護されているかに関係なく、ストリームがライブかどうかを確認します。

   この情報は、再生用のUIを準備するのに役立ちます。 例えば、2つのオーディオトラックがある場合は、これらのトラックを切り替えるUIコントロールを含めることができます。

1. `MediaPlayer.prepareToPlay`を呼び出して広告ワークフローを開始します。

   広告が解決されてタイムラインに配置された後、`MediaPlayer`トランジションが`PREPARED`状態になります。
1. `MediaPlayer.play`を呼び出して、再生を開始します。
メディアの再生時に、TVSDKに広告が含まれるようになりました。
