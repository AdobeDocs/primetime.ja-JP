---
description: 広告リゾルバーを機能させるには、Adobe Primetime Ad Decisioning などの広告プロバイダーが、プロバイダーへの接続を有効にするために設定値を必要とします。
title: 広告挿入メタデータ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# 広告挿入メタデータ {#ad-insertion-metadata}

広告リゾルバーを機能させるには、Adobe Primetime Ad Decisioning などの広告プロバイダーが、プロバイダーへの接続を有効にするために設定値を必要とします。

TVSDK には、 Primetime ad decisioning ライブラリが含まれています。 コンテンツに Primetime ad decisioning サーバーからの広告を含めるには、アプリケーションが次の必要事項を提供する必要があります `AuditudeSettings` 情報：

* `mediaID`：再生するビデオの一意の識別子です。

  公開者は、ビデオコンテンツと広告情報をAdobe Primetime Ad Decisioning サーバーに送信する際に、mediaID を割り当てます。 この ID は、Primetime ad decisioning がビデオに関連する広告情報をサーバーから取得するために使用します。

* お使いの `zoneID`:Adobeによって割り当てられ、会社または Web サイトを識別します。
* 割り当てられた広告サーバーのドメイン。
* その他のターゲティングパラメーター。

  広告プロバイダーのニーズやニーズに応じて、これらのパラメーターを含めることができます。

## 広告挿入メタデータの設定 {#set-up-ad-insertion-metadata}

Adobe Primetime Ad Decisioning メタデータを設定するには、MetadataNode クラスを拡張するヘルパークラス AuditudeSettings を使用します。

>[!TIP]
>
>Adobe Primetime ad decisioning は、以前はAuditudeと呼ばれていました。

広告メタデータは `MediaResource.metadata` プロパティ。 新しいビデオの再生を開始する場合、アプリケーションは正しい広告メタデータを設定する必要があります。

1. のビルド `AuditudeSettings` インスタンス。

   ```
   var auditudeSettings:AuditudeSettings = new AuditudeSettings();
   ```

1. Adobe Primetime Ad Decisioning mediaID、zoneID、domain およびオプションのターゲティングパラメーターを設定します。

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
   >メディア ID は、TVSDK によって文字列として使用され、md5 値に変換されて、 `u` Primetime ad decisioning URL リクエストの値。 例：
   >
   >
   >` https://ad.auditude.com/adserver? **u**=c76d04ee31c91c4ce5c8cee41006c97d &z=114100&l=20150206141527&of=1.4&tm=15&g=1000002`

1. の作成 `MediaResource` インスタンスを作成できます。

   ```
   var mediaResourceMetadata:MetadataNode = new MetadataNode(); 
   mediaResourceMetadata.setNode(DefaultMetadataKeys.AUDITUDE_METADATA_KEY, auditudeSettings); 
   var mediaResource:MediaResource = new MediaResource( 
         "www.example.com/video/test.m3u8", 
         MediaResourceType.HLS,  
         mediaResourceMetadata);
   ```

1. を読み込む `MediaResource` ～を通して目的を達成する `MediaPlayer.replaceCurrentResource` メソッド。

   The `MediaPlayer` メディアストリームマニフェストの読み込みと処理を開始します。

1. （オプション） `MediaPlayerItem` インスタンスを使用して、代替オーディオトラックがあるかどうか、またはストリームが保護されているかどうかに関係なく、ストリームがライブかどうかを確認します。

   この情報は、再生用の UI を準備する際に役立ちます。 例えば、2 つのオーディオトラックがある場合は、これらのトラックを切り替える UI コントロールを含めることができます。

1. 通話 `MediaPlayer.prepareToPlay` ：広告ワークフローを開始します。

   広告が解決され、タイムラインに配置された後、 `MediaPlayer` を PREPARED 状態に切り替えます。
1. 通話 `MediaPlayer.play` 再生を開始します。

メディアが再生される際に、 TVSDK に広告が含まれるようになりました。
