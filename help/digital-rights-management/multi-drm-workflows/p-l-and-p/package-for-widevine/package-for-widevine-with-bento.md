---
description: Bento4パッケージャーとAdobe Offline Packagerの両方を使用して、暗号化されたDASHコンテンツを作成します。 Bento4は、暗号化されていないmp4コンテンツを入力として受け取ります。
seo-description: Bento4パッケージャーとAdobe Offline Packagerの両方を使用して、暗号化されたDASHコンテンツを作成します。 Bento4は、暗号化されていないmp4コンテンツを入力として受け取ります。
seo-title: Bento4でコンテンツをパッケージ化する
title: Bento4でコンテンツをパッケージ化する
uuid: 88323a4e-d0b5-4a41-acec-7126d3e0c90b
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c

---


# WidevineおよびPlayReady用コンテンツのパッケージ化 {#package-for-widevine}

Bento4パッケージャーとAdobe Offline Packagerの両方を使用して、暗号化されたDASHコンテンツを作成します。 Bento4は、暗号化されていないmp4コンテンツを入力として受け取ります。

## Bento4でコンテンツをパッケージ化する{#package-your-content-with-bento}

Bento4パッケージャは、入力mp4が事前にフラグメント化されていることを想定しています。 Bento4パッケージャーの配布には、このツールが含まれています。

**Bento4の呼び出し**

一般的なBento4パッケージャーの呼び出しは、次の例のようになります。

    ./mp4dash
    -f
    —use-segment-list
    —use-segment-timeline—subtitles
    —encryption-key=7cc7f0470019ac10d06bca13a580a9ff:5fa05f94e8cd09fc0747c7c5ac215b3b
    —widevine
    
    
    —widevine-header=provider:intertrust#content_id:2a &quot;CC_300_640x360x360.mp4&quot;CC_300.mp4&quot;3000x360_DASH&quot;
>
    ./mp4dash
    -f
    —use-segment-list
    —use-segment-timeline—subtitles
    —encryption-key=7cc7f0470019ac10d06bca13a580a9ff:5fa05f94e8cd09fc0747c7c5ac215b3b
    —playready
    
    —playready-header=\&quot;LA_URL:http://pr.test.expressplay.com/playready/RightsManager.asmx\&quot;

次の例は、PlayReadyとWidevineのスキームを組み合わせたものです。 この場合、Widevineコンテンツ保護とPlayReadyコンテンツ保護の両方の初期化データが出力DASHコンテンツに追加されます。

    /mp4dash
    -f
    —use-segment-list
    —use-segment-timeline—subtitles
    —encryption-key=7cc7f0470019ac10d06bca13a580a9ff:5fa05f94e8cd09fc0747c7c5ac215b3b
    —playready
    
    
    
    
    
    
    —playready-header=\&quot;LA_URL:http://pr.test.expressplay.com/playready/RightsManager.asmx\&quot;devine-widevine-header=provider—devine-header:2a &quot;CC_300_640x360.mp4CC_300_640x360_DASH

フラグの値は `--encryption-key` フォーム内にあります `<base16 encoded key id>:<base16 encoded encryption key>`。

このフ `--widevine-header=provider:intertrust#content_id:2a` ラグは、現在TVSDKが再生に必要としているpsshボックスをマニフェストに含めるようパッケージャーに指示します。
の値は、PlayReadyライ `-playready-header` センス取得用です。

## Adobe Offline Packagerでコンテンツをパッケージ化する {#package-your-content-with-adobe-offline-packager}

Adobe Offline Packagerは、暗号化されていないmp4コンテンツを入力として受け取ります。

**Adobe Offline Packagerの呼び出し**

一般的なAdobe Offline Packagerの呼び出しは、次の呼び出しのようになります。

    java -jar OfflinePackager.jar -conf_path Content_PR_WV.xml -in_path &quot;Jaigo.mp4&quot;
    -out_path &quot;Jaigo_DASH&quot;
    -key_file_path &quot;Jaigo_DASH/_info/key.B64.random&quot;
    -widevine_key_id_c595f214d84dcecf31a8ebf1b7ddda5
    -widevine_provider intertrust
    -playready_LA_URLhttp://pr.test.expressplay.com/playready/RightsManager.asmx
    
    
    -playready_keyid c595f214d84dc7ecf31a8ebf1bb7da5ddd_id c595c2514d84dc7ecf31a8ebf1b7ddda5

この場合、オフラインパッケージャーは、Widevineコンテンツ保護とPlayReadyコンテンツ保護の両方の初期化データを出力DASHコンテンツに追加します。 の値は、base64エ `-key_file_path` ンコードされたキーに対するものです。 の値は、PlayReadyライ `-playready_LA_URL` センス取得用です。

conf_path引数は、次の値を含む設定ファイルを指します。

    &lt;config>
    &lt;frag_dur>4&lt;/frag_dur>
    &lt;target_dur>6&lt;/target_dur>
    &lt;encrypt_audio>false&lt;/encrypt_audio>
    &lt;/config>

特定のAndroidデバイス — 主にAmazon Fire TV — オーディオの復号化はサポートされていません。オーディオの暗号化はオプションです。