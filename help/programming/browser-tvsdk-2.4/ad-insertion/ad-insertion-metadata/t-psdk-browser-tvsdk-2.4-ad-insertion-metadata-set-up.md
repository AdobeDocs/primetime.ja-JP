---
description: ヘルパークラスAuditudeSettingsを使用して、Adobe PrimetimeAd Decisioningメタデータを設定します。
seo-description: ヘルパークラスAuditudeSettingsを使用して、Adobe PrimetimeAd Decisioningメタデータを設定します。
seo-title: 広告挿入メタデータの設定
title: 広告挿入メタデータの設定
uuid: fc37e0ae-6acf-4a78-a468-f7b5b123b45e
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---


# 広告挿入メタデータの設定{#set-up-ad-insertion-metadata}

ヘルパークラスAuditudeSettingsを使用して、Adobe PrimetimeAd Decisioningメタデータを設定します。

>[!TIP]
>
>Adobe Primetimead decisioningは、以前はAuditudeと呼ばれていました。

1. `AuditudeSettings`インスタンスを構築します。

   ```java
   AuditudeSettings auditudeSettings = new AuditudeSettings();
   ```

1. Adobe Primetimead decisioning mediaID、zoneID、domainおよびオプションのターゲティングパラメーターを設定します。

   ```js
   auditudeSettings.domain = "yourdomain"; 
   auditudeSettings.mediaId = "mediaid"; 
   auditudeSettings.zoneId = "zoneid";
   ```

1. メディアストリームURLと以前に作成した広告メタデータを使用して`MediaResource`インスタンスを作成します。

   ```js
   mediaResource = new AdobePSDK.MediaResource ( 
         resourceUrl, 
         resourceType,  
         auditudeSettings);
   ```

1. `MediaResource`オブジェクトを`MediaPlayer.replaceCurrentResource(resource)`メソッドを使用して読み込みます。

   `MediaPlayer`開始は、メディアストリームマニフェストを読み込み、処理します。

1. `MediaPlayer`トランジションがINITIALIZED状態になったら、`MediaPlayer.CurrentItem`属性を介して`MediaPlayerItem`インスタンスの形式でメディアストリームの特性を取得します。
1. （オプション）`MediaPlayerItem`インスタンスをクエリして、代替オーディオトラックがあるかどうかに関係なく、ストリームがライブかどうかを確認します。

   この情報は、再生用のUIを準備するのに役立ちます。 例えば、2つのオーディオトラックがある場合は、これらのトラックを切り替えるUIコントロールを含めることができます。

1. `MediaPlayer.prepareToPlay`を呼び出して広告ワークフローを開始します。

   広告が解決されてタイムラインに配置された後、`  MediaPlayer `トランジションはPREPARED状態になります。
1. `MediaPlayer.play`を呼び出して、再生を開始します。
メディアの再生時に、ブラウザーTVSDKに広告が含まれるようになりました。
