---
description: Bento4 PackagerとAdobeOffline Packagerの両方を使用して、暗号化されたDASHコンテンツを作成します。 Bento4は、暗号化されていないmp4コンテンツを入力として受け取ります。
seo-description: Bento4 PackagerとAdobeOffline Packagerの両方を使用して、暗号化されたDASHコンテンツを作成します。 Bento4は、暗号化されていないmp4コンテンツを入力として受け取ります。
seo-title: Bento4でコンテンツをパッケージ化する
title: Bento4でコンテンツをパッケージ化する
uuid: 88323a4e-d0b5-4a41-acec-7126d3e0c90b
translation-type: tm+mt
source-git-commit: 75702ea2a524d7b38bb9ac83cb094c8482b1098f
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---


# WidevineおよびPlayReady用コンテンツのパッケージ化 {#package-for-widevine}

Bento4 PackagerとAdobeOffline Packagerの両方を使用して、暗号化されたDASHコンテンツを作成します。 Bento4は、暗号化されていないmp4コンテンツを入力として受け取ります。

## Bento4でコンテンツをパッケージ化する{#package-your-content-with-bento}

Bento4パッケージャーは、入力mp4が事前にフラグメント化されていることを想定しています。 Bento4 packagerの配布版には、この機能を実現するためのツールが含まれています。

**Bento4の呼び出し**

一般的なBento4 packagerの呼び出しは、次の例のようになります。

```
./mp4dash
-f
--use-segment-list
--use-segment-timeline
--subtitles
--encryption-key=7cc7f0470019ac10d06bca13a580a9ff:5fa05f94e8cd09fc0747c7c5ac215b3b
--widevine
--widevine-header=provider:intertrust#content_id:2a "CC_300_640x360.mp4"
-o "CC_300_640x360_DASH"
```

```
./mp4dash
-f
--use-segment-list
--use-segment-timeline
--subtitles
--encryption-key=7cc7f0470019ac10d06bca13a580a9ff:5fa05f94e8cd09fc0747c7c5ac215b3b
--playready
--playready-header=\"LA_URL:http://pr.test.expressplay.com/playready/RightsManager.asmx\"
```

次の例は、PlayReadyとWidevineのスキームを組み合わせたものです。 この場合、パッケージャーは、Widevineコンテンツ保護とPlayReadyコンテンツ保護の初期化データの両方を出力DASHコンテンツに追加します。

```
/mp4dash
-f
--use-segment-list
--use-segment-timeline
--subtitles
--encryption-key=7cc7f0470019ac10d06bca13a580a9ff:5fa05f94e8cd09fc0747c7c5ac215b3b
--playready
--playready-header=\"LA_URL:http://pr.test.expressplay.com/playready/RightsManager.asmx\"
--widevine
--widevine-header=provider:intertrust#content_id:2a "CC_300_640x360.mp4"
-o "CC_300_640x360_DASH"
```

where

フ `--encryption-key` ラグの値は次の形式で示されま `<base16 encoded key id>:<base16 encoded encryption key>`す。

この `--widevine-header=provider:intertrust#content_id:2a` フラグは、パッケージャーにマニフェストにpsshボックスを含めるように指示します。このTVSDKは現在、再生に必要としています。

の値 `-playready-header` は、PlayReadyライセンス取得用です。

## AdobeのOffline Packagerでコンテンツをパッケージ化する {#package-your-content-with-adobe-offline-packager}

AdobeOffline Packagerは、暗号化されていないmp4コンテンツを入力として受け取ります。

**Adobeオフラインパッケージャーの呼び出し**

一般的なadobe offline packagerの呼び出しは、次のようになります。

```
java -jar OfflinePackager.jar -conf_path Content_PR_WV.xml -in_path "Jaigo.mp4"
-out_path "Jaigo_DASH"
-key_file_path "Jaigo_DASH/_info/key.B64.random"
-widevine_key_id c595f214d84dc7ecf31a8ebf1b7ddda5
-widevine_provider intertrust
-playready_LA_URL
http://pr.test.expressplay.com/playready/RightsManager.asmx
-playready_keyid c595f214d84dc7ecf31a8ebf1b7ddda5
-content_id c595f214d84dc7ecf31a8ebf1b7ddda5
```

この場合、オフラインパッケージャーは、Widevineコンテンツ保護とPlayReadyコンテンツ保護の初期化データの両方を出力DASHコンテンツに追加します。 の値 `-key_file_path` は、base64エンコードされたキーに対して設定されます。 の値 `-playready_LA_URL` は、PlayReadyライセンス取得用です。

conf_path引数は、次の値を含む設定ファイルを指します。

```
<config>
<frag_dur>4</frag_dur>
<target_dur>6</target_dur>
<encrypt_audio>false</encrypt_audio>
</config>
```

一部のAndroidデバイス(主にAmazonFire TV)は、オーディオの復号化をサポートしないので、オーディオの暗号化はオプションです。
