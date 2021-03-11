---
description: 広告リゾルバーが機能するようにするには、Adobe Primetimead decisioningなどの広告プロバイダーがプロバイダーへの接続を有効にするために設定値を必要とします。
title: 広告挿入メタデータ
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---


# 広告挿入メタデータ{#ad-insertion-metadata}

広告リゾルバーが機能するようにするには、Adobe Primetimead decisioningなどの広告プロバイダーがプロバイダーへの接続を有効にするために設定値を必要とします。

TVSDKには、Primetime ad decisioningライブラリが含まれています。 Primetime ad decisioningサーバーから広告をコンテンツに含めるには、アプリケーションが以下の必要な`AuditudeSettings`情報を提供する必要があります。

* `mediaID`は、再生されるビデオの一意の識別子です。

   発行者は、ビデオコンテンツと広告情報をAdobe Primetimead decisioningサーバーに送信する際にmediaIDを割り当てます。 このIDは、Primetime ad decisioningがサーバーからビデオに関連する広告情報を取得するために使用します。

* `zoneID`は、Adobeによって割り当てられ、会社またはWebサイトを特定します。
* 割り当てられた広告サーバーのドメイン。
* その他のターゲティングパラメーター。

   広告プロバイダーのニーズおよびニーズに応じて、これらのパラメーターを含めることができます。

## 広告挿入メタデータの設定{#set-up-ad-insertion-metadata}

MetadataNodeクラスを拡張するヘルパークラスAuditudeSettingsを使用して、Adobe PrimetimeAd Decisioningメタデータを設定します。

>[!TIP]
>
>Adobe Primetimead decisioningは、以前はAuditudeと呼ばれていました。

広告メタデータは`MediaResource.metadata`プロパティにあります。 新しいビデオの再生を開始する場合、アプリケーションで正しい広告メタデータを設定する必要があります。

1. `AuditudeSettings`インスタンスを構築します。

   ```
   var auditudeSettings:AuditudeSettings = new AuditudeSettings();
   ```

1. Adobe Primetimead decisioning mediaID、zoneID、domainおよびオプションのターゲティングパラメーターを設定します。

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
   >メディアIDはTVSDKで文字列として使用され、md5値に変換され、Primetime ad decisioning URLリクエストの`u`値に使用されます。 例：
   >
   >
   >` https://ad.auditude.com/adserver? **u**=c76d04ee31c91c4ce5c8cee41006c97d &z=114100&l=20150206141527&of=1.4&tm=15&g=1000002`

1. メディアストリームURLと以前に作成した広告メタデータを使用して`MediaResource`インスタンスを作成します。

   ```
   var mediaResourceMetadata:MetadataNode = new MetadataNode(); 
   mediaResourceMetadata.setNode(DefaultMetadataKeys.AUDITUDE_METADATA_KEY, auditudeSettings); 
   var mediaResource:MediaResource = new MediaResource( 
         "www.example.com/video/test.m3u8", 
         MediaResourceType.HLS,  
         mediaResourceMetadata);
   ```

1. `MediaResource`オブジェクトを`MediaPlayer.replaceCurrentResource`メソッドを使用して読み込みます。

   `MediaPlayer`開始は、メディアストリームマニフェストを読み込み、処理します。

1. （オプション）`MediaPlayerItem`インスタンスをクエリして、代替オーディオトラックがあるかどうかに関係なく、ストリームがライブかどうかを確認します。また、ストリームが保護されているかどうかも関係ありません。

   この情報は、再生用のUIを準備するのに役立ちます。 例えば、2つのオーディオトラックがある場合は、これらのトラックを切り替えるUIコントロールを含めることができます。

1. `MediaPlayer.prepareToPlay`を呼び出して広告ワークフローを開始します。

   広告が解決されてタイムラインに配置された後、`MediaPlayer`トランジションはPREPARED状態になります。
1. `MediaPlayer.play`を呼び出して、再生を開始します。

メディアの再生時に、TVSDKに広告が含まれるようになりました。