---
description: 暗号化された DASH コンテンツを作成するには、Bento4 パッケージャーとAdobeオフラインパッケージャーの両方を使用します。 Bento4 は、暗号化されていない mp4 コンテンツを入力として取り込みます。
title: Bento4 でコンテンツをパッケージ化
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# Widevine および PlayReady 用コンテンツのパッケージ化 {#package-for-widevine}

暗号化された DASH コンテンツを作成するには、Bento4 パッケージャーとAdobeオフラインパッケージャーの両方を使用します。 Bento4 は、暗号化されていない mp4 コンテンツを入力として取り込みます。

## Bento4 でコンテンツをパッケージ化{#package-your-content-with-bento}

Bento4 パッケージャは、入力 mp4 が事前に断片化されていることを想定しています。 Bento4 パッケージャの配布には、このツールが含まれています。

**Bento4 の呼び出し**

一般的な Bento4 パッケージャの呼び出しは、次の例のようになります。

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

以下の例は、PlayReady と Widevine のスキームを組み合わせたものです。 この場合、パッケージャは Widevine コンテンツ保護と PlayReady コンテンツ保護初期化データの両方を出力 DASH コンテンツに追加します。

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

場所

の値 `--encryption-key` フラグがフォーム内にある `<base16 encoded key id>:<base16 encoded encryption key>`.

The `--widevine-header=provider:intertrust#content_id:2a` フラグは、現在 TVSDK が再生に必要としている pssh ボックスをマニフェストに含めるようにパッケージャに指示します。

の値 `-playready-header` は、PlayReady ライセンス獲得用のものです。

## Adobeオフラインパッケージャでコンテンツをパッケージ化 {#package-your-content-with-adobe-offline-packager}

Adobeオフライン Packager は、暗号化されていない mp4 コンテンツを入力として取得します。

**Adobeオフラインパッケージャを呼び出し中**

一般的な adobe offline packager の呼び出しは、次のようになります。

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

この場合、オフラインパッケージャは Widevine コンテンツ保護と PlayReady コンテンツ保護初期化データの両方を出力 DASH コンテンツに追加します。 の値 `-key_file_path` は、base64 でエンコードされたキーの場合に使用されます。 の値 `-playready_LA_URL` は、PlayReady ライセンス獲得用のものです。

conf_path 引数は、次の内容を含む設定ファイルを指します。

```
<config>
<frag_dur>4</frag_dur>
<target_dur>6</target_dur>
<encrypt_audio>false</encrypt_audio>
</config>
```

特定の Android デバイス ( 主にAmazon Fire TV ) は、オーディオの復号化をサポートしていないので、オーディオの暗号化はオプションです。
