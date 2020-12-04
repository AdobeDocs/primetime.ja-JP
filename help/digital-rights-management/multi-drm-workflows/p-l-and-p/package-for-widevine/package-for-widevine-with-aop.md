---
description: AdobeOffline Packagerは、暗号化されていないmp4コンテンツを入力として受け取ります。
seo-description: AdobeOffline Packagerは、暗号化されていないmp4コンテンツを入力として受け取ります。
seo-title: AdobeのOffline Packagerでコンテンツをパッケージ化する
title: AdobeのOffline Packagerでコンテンツをパッケージ化する
uuid: d0676147-c20f-49ea-93a6-9c8dbbbba992
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---


# AdobeのOffline Packager{#package-your-content-with-adobe-offline-packager}でコンテンツをパッケージ化する

AdobeOffline Packagerは、暗号化されていないmp4コンテンツを入力として受け取ります。

**Adobeオフラインパッケージャーの呼び出し**

一般的なadobe offline packagerの呼び出しは、次のようになります。

    java -jar OfflinePackager.jar -conf_path Content_PR_WV.xml -in_path &quot;Jaigo.mp4&quot;
    -out_path &quot;Jaigo_DASH&quot;
    -key_file_path &quot;Jaigo_DASH/_info/key.B64.random&quot;
    -widevine_key_id c595f214d84dcecf31a8ebf1b7ddda5
    -widevine_provider intertrust
    -playready_LA_URLhttp://pr.test.expressplay.com/playready/RightsManager.asmx
    
    
    -playready_keyid c595f214d84dc7ecf31a ebf1dda5ddd-c595f14d84dc7ecf31a8ebf1b7dda5

この場合、オフラインパッケージャーは、Widevineコンテンツ保護とPlayReadyコンテンツ保護の初期化データの両方を出力DASHコンテンツに追加します。 `-key_file_path`の値は、base64エンコードされたキーに対する値です。 `-playready_LA_URL`の値は、PlayReadyライセンス取得のためのものです。

conf_path引数は、次の値を含む設定ファイルを指します。

    &lt;config>
    &lt;frag_dur>4&lt;/frag_dur>
    &lt;target_dur>6&lt;/target_dur>
    &lt;encrypt_audio>false&lt;/encrypt_audio>
    &lt;/config>

一部のAndroidデバイス(主にAmazonFire TV)は、オーディオの復号化をサポートしないので、オーディオの暗号化はオプションです。
