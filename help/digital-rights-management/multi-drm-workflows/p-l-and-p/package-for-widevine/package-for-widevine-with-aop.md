---
description: Adobe Offline Packagerは、暗号化されていないmp4コンテンツを入力として受け取ります。
seo-description: Adobe Offline Packagerは、暗号化されていないmp4コンテンツを入力として受け取ります。
seo-title: Adobe Offline Packagerでコンテンツをパッケージ化する
title: Adobe Offline Packagerでコンテンツをパッケージ化する
uuid: d0676147-c20f-49ea-93a6-9c8dbbbba992
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c

---


# Adobe Offline Packagerでコンテンツをパッケージ化する{#package-your-content-with-adobe-offline-packager}

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
