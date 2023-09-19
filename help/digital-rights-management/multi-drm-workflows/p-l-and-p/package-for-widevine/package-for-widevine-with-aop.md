---
description: Adobeオフライン Packager は、暗号化されていない mp4 コンテンツを入力として取得します。
title: Adobeオフラインパッケージャでコンテンツをパッケージ化
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---

# Adobeオフラインパッケージャでコンテンツをパッケージ化{#package-your-content-with-adobe-offline-packager}

Adobeオフライン Packager は、暗号化されていない mp4 コンテンツを入力として取得します。

**Adobeオフラインパッケージャを呼び出し中**

一般的な adobe offline packager の呼び出しは、次のようになります。

    java -jar OfflinePackager.jar -conf_path Content_PR_WV.xml -in_path &quot;Jaigo.mp4&quot;
    -out_path &quot;Jaigo_DASH&quot;
    -key_file_path &quot;Jaigo_DASH/_info/key.B64.random&quot;
    -widevine_key_id c595f214d84dc7ecf31a8ebf1b7ddda5
    -widevine_provider intertrust
    -playready_LA_URL
    http://pr.test.expressplay.com/playready/RightsManager.asmx
    -playready_keyid c595f214d84dc7ecf31a8ebf1b7ddda5
    -content_id c595f214d84dc7ecf31a8ebf1b7ddda5

この場合、オフラインパッケージャは Widevine コンテンツ保護と PlayReady コンテンツ保護初期化データの両方を出力 DASH コンテンツに追加します。 の値 `-key_file_path` は、base64 でエンコードされたキーの場合に使用されます。 の値 `-playready_LA_URL` は、PlayReady ライセンス獲得用のものです。

conf_path 引数は、次の内容を含む設定ファイルを指します。

    &lt;config>
    &lt;frag_dur>4&lt;/frag_dur>
    &lt;target_dur>6&lt;/target_dur>
    &lt;encrypt_audio>false&lt;/encrypt_audio>
    &lt;/config>

特定の Android デバイス ( 主にAmazon Fire TV ) は、オーディオの復号化をサポートしていないので、オーディオの暗号化はオプションです。
