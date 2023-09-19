---
description: Adobe Primetime Ad Decisioning メタデータを設定するには、MetadataNode クラスを拡張するヘルパークラス AuditudeSettings を使用します。
title: 広告挿入メタデータの設定
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# 広告挿入メタデータの設定 {#set-up-ad-insertion-metadata}

ヘルパークラスの使用 `AuditudeSettings`（を拡張） `MetadataNode` クラスを使用して、Adobe Primetime ad decisioning メタデータを設定します。

>[!TIP]
>
>Adobe Primetime ad decisioning は、以前はAuditudeと呼ばれていました。

広告メタデータは `MediaResource.Metadata` プロパティ。 新しいビデオの再生を開始する場合、アプリケーションは正しい広告メタデータを設定する必要があります。

1. のビルド `AuditudeSettings` インスタンス。

   ```java
   AuditudeSettings auditudeSettings = new AuditudeSettings();
   ```

1. Adobe Primetime Ad Decisioning の設定 `mediaID`, `zoneID`, `<ph conkeyref="phrases/primetime-sdk-name"/>`、およびオプションのターゲティングパラメーター。

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
   >メディア ID は、TVSDK によって文字列として使用され、md5 値に変換されて、 `u` Primetime ad decisioning URL リクエストの値。 例：
   >
   >`https://ad.auditude.com/adserver? **u**=c76d04ee31c91c4ce5c8cee41006c97d &z=114100&l=20150206141527&of=1.4&tm=15&g=1000002`

1. の作成 `MediaResource` インスタンスを作成できます。

   ```java
   MediaResource mediaResource = new MediaResource( 
   "https://example.com/media/test_media.m3u8", MediaResource.Type.HLS, Metadata);
   ```

1. を読み込む `MediaResource` ～を通して目的を達成する `MediaPlayer.replaceCurrentResource` メソッド。

   The `MediaPlayer` メディアストリームマニフェストの読み込みと処理を開始します。

1. 次の場合に `MediaPlayer` を INITIALIZED ステータスに切り替え、メディアストリームの特性を `MediaPlayerItem` インスタンスを通して `MediaPlayer.CurrentItem` メソッド。
1. （オプション） `MediaPlayerItem` インスタンスを使用して、代替オーディオトラックがあるか、ストリームが保護されているかに関係なく、ストリームがライブかどうかを確認します。

   この情報は、再生用の UI を準備する際に役立ちます。 例えば、2 つのオーディオトラックがある場合は、これらのトラックを切り替える UI コントロールを含めることができます。

1. 通話 `MediaPlayer.prepareToPlay` ：広告ワークフローを開始します。

   広告が解決され、タイムラインに配置された後、 `MediaPlayer` への切り替え `PREPARED` 状態。
1. 通話 `MediaPlayer.play` 再生を開始します。
メディアが再生される際に、 TVSDK に広告が含まれるようになりました。
