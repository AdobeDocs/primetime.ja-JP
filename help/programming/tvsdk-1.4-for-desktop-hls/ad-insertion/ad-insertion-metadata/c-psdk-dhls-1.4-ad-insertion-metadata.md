---
description: 広告リゾルバーが機能するようにするには、Adobe Primetime ad decisioningなどの広告プロバイダーが、プロバイダーへの接続を有効にするために設定値を必要とします。
seo-description: 広告リゾルバーが機能するようにするには、Adobe Primetime ad decisioningなどの広告プロバイダーが、プロバイダーへの接続を有効にするために設定値を必要とします。
seo-title: 広告挿入メタデータ
title: 広告挿入メタデータ
uuid: 3eb024c3-4bb5-4bee-943e-fe0c60379e60
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40

---


# 広告挿入メタデータ {#ad-insertion-metadata}

広告リゾルバーが機能するようにするには、Adobe Primetime ad decisioningなどの広告プロバイダーが、プロバイダーへの接続を有効にするために設定値を必要とします。

TVSDKには、Primetime ad decisioningライブラリが含まれています。 Primetime ad decisioningサーバーからの広告をコンテンツに含めるには、アプリケーションが次の必要な情報を提供する必要があ `AuditudeSettings` ります。

* `mediaID`に含まれている場合、再生されるビデオの一意の識別子です。

   発行者は、ビデオコンテンツと広告情報をAdobe Primetime Ad Decisioningサーバーに送信する際に、mediaIDを割り当てます。 このIDは、Primetime ad decisioningで、サーバーからビデオに関連する広告情報を取得するために使用されます。

* アドビ `zoneID`が割り当てたユーザーは、会社またはWebサイトを識別します。
* 割り当てられた広告サーバーのドメイン。
* その他のターゲティングパラメーター。

   これらのパラメーターは、ニーズおよび広告プロバイダーのニーズに応じて含めることができます。

## 広告挿入メタデータの設定 {#set-up-ad-insertion-metadata}

MetadataNodeクラスを拡張するヘルパークラスAuditudeSettingsを使用して、Adobe Primetime ad decisioningメタデータを設定します。

>[!TIP]
>
>Adobe Primetime ad decisioningは、以前はAuditudeと呼ばれていました。

広告メタデータはプロパティ内に `MediaResource.metadata` あります。 新しいビデオの再生を開始する際、アプリで正しい広告メタデータを設定する必要があります。

1. インスタンスを作 `AuditudeSettings` 成します。

   ```
   var auditudeSettings:AuditudeSettings = new AuditudeSettings();
   ```

1. Adobe Primetime ad decisioningのmediaID、zoneID、domainおよびオプションのターゲティングパラメーターを設定します。

   ```
   auditudeSettings.zoneId = "yourZoneID"; 
   auditudeSettings.mediaId = "media_identifier"; 
   auditudeSettings.domain = "yourAuditudeDomain"; 
   var targetingInfo:Metadata = new Metadata(); 
   targetingInfo.setValue("yourParamName", "yourParamValue"); 
   auditudeSettings.targetingInfo = targetingInfo;
   ```

   >[!TIP]
   >
   >メディアIDは、TVSDKが文字列として使用し、md5値に変換され、Primetime ad decisioning URLリクエストの値に `u` 使用されます。 例：
   >
   >
   >` https://ad.auditude.com/adserver? **u**=c76d04ee31c91c4ce5c8cee41006c97d &z=114100&l=20150206141527&of=1.4&tm=15&g=1000002`

1. メディアストリ `MediaResource` ームURLと、以前に作成した広告メタデータを使用して、インスタンスを作成します。

   ```
   var mediaResourceMetadata:MetadataNode = new MetadataNode(); 
   mediaResourceMetadata.setNode(DefaultMetadataKeys.AUDITUDE_METADATA_KEY, auditudeSettings); 
   var mediaResource:MediaResource = new MediaResource( 
         "www.example.com/video/test.m3u8", 
         MediaResourceType.HLS,  
         mediaResourceMetadata);
   ```

1. メソッドを使用し `MediaResource` てオブジェクトを読み `MediaPlayer.replaceCurrentResource` 込みます。

   メディア `MediaPlayer` ストリームマニフェストの読み込みと処理を開始します。

1. （オプション）代替オーディオト `MediaPlayerItem` ラックが含まれているかどうか、ストリームが保護されているかどうかに関係なく、ストリームがライブかどうかをインスタンスに問い合わせます。

   この情報は、再生用のUIを準備するのに役立ちます。 例えば、2つのオーディオトラックがある場合は、これらのトラックを切り替えるUIコントロールを含めることができます。

1. 広告ワー `MediaPlayer.prepareToPlay` クフローを開始するための呼び出し。

   広告が解決され、タイムラインに配置された後、PREPARED `MediaPlayer` 状態に移行します。
1. を呼び出 `MediaPlayer.play` して、再生を開始します。

TVSDKは、メディアの再生時に広告を含むようになりました。