---
description: ヘルパークラス AuditudeSettings を使用して、Adobe Primetime ad decisioning メタデータを設定します。
title: 広告挿入メタデータの設定
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---

# 広告挿入メタデータの設定{#set-up-ad-insertion-metadata}

ヘルパークラス AuditudeSettings を使用して、Adobe Primetime ad decisioning メタデータを設定します。

>[!TIP]
>
>Adobe Primetime ad decisioning は、以前はAuditudeと呼ばれていました。

1. のビルド `AuditudeSettings` インスタンス。

   ```java
   AuditudeSettings auditudeSettings = new AuditudeSettings();
   ```

1. Adobe Primetime Ad Decisioning mediaID、zoneID、domain およびオプションのターゲティングパラメーターを設定します。

   ```js
   auditudeSettings.domain = "yourdomain"; 
   auditudeSettings.mediaId = "mediaid"; 
   auditudeSettings.zoneId = "zoneid";
   ```

1. の作成 `MediaResource` インスタンスを作成できます。

   ```js
   mediaResource = new AdobePSDK.MediaResource ( 
         resourceUrl, 
         resourceType,  
         auditudeSettings);
   ```

1. を読み込む `MediaResource` ～を通して目的を達成する `MediaPlayer.replaceCurrentResource(resource)` メソッド。

   The `MediaPlayer` メディアストリームマニフェストの読み込みと処理を開始します。

1. 次の場合に `MediaPlayer` を INITIALIZED ステータスに切り替え、メディアストリームの特性を `MediaPlayerItem` インスタンスを通して `MediaPlayer.CurrentItem` 属性。
1. （オプション） `MediaPlayerItem` インスタンスを使用して、代替オーディオトラックがあるかどうかに関係なく、ストリームがライブかどうかを確認します。

   この情報は、再生用の UI を準備する際に役立ちます。 例えば、2 つのオーディオトラックがある場合は、これらのトラックを切り替える UI コントロールを含めることができます。

1. 通話 `MediaPlayer.prepareToPlay` ：広告ワークフローを開始します。

   広告が解決され、タイムラインに配置された後、 `  MediaPlayer ` を PREPARED 状態に切り替えます。
1. 通話 `MediaPlayer.play` 再生を開始します。
メディアが再生される際に、ブラウザー TVSDK に広告が含まれるようになりました。
