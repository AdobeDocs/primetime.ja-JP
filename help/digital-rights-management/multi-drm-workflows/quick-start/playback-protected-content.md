---
description: DRMソリューションをテストするには、操作している特定のDRMソリューションを処理できるビデオアプリケーションが必要です。 このプレイヤーは、Adobeが提供するサンプルプレイヤー、または独自のTVSDKベースのビデオアプリケーションにすることができます。
title: 保護されているコンテンツの再生
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 0%

---


# 保護されたコンテンツの再生{#playback-your-protected-content}

DRMソリューションをテストするには、操作している特定のDRMソリューションを処理できるビデオアプリケーションが必要です。 このプレイヤーは、Adobeが提供するサンプルプレイヤー、または独自のTVSDKベースのビデオアプリケーションにすることができます。

1. ExpressPlayサーバーから返されたトークンレスポンスのLicense Server URLを使用して、保護されたコンテンツを再生できるかどうかをテストします。

   * **Widevine**  - ExpressPlayライセンストークンリクエストに対して受け取ったWidevineレスポンスを直接使用します。
   * **PlayReady**  — ライセンストークンリクエストから返されるJSONオブジェクトから、ライセンスサーバーのURLとトークンを取得します。
   * **FairPlay**  - ExpressPlayライセンストークンリクエストに対して受け取ったFairPlayレスポンスを直接使用します。

1. 独自のプレーヤーまたは既存のAdobeのサンプルプレーヤーを使用して、保護されたコンテンツの再生をテストします。

   保護されたコンテンツへのURLを指定します（テストするDRMソリューションに応じて、M3U8またはMPDマニフェストの場所）。

   テストに使用するプレーヤーが提供するインターフェイスに応じて、ライセンスURLとトークンを入力フィールドの文字列として、またはテキストボックスに貼り付けるJSONオブジェクトとして、またはおそらくURLのクエリパラメーターとして指定するように求められます。

   テストプレーヤーの可能性を以下に示します。

   * HTML5リファレンスプレイヤ：

      ```
      https://ptdemos.com/html5/internal/1_2/2.4_GM/samples/reference/reference_player.html
      ```

   * 釈迦奏者

      ```
      https://shaka-player-demo.appspot.com
      ```

   * サンプルTVSDKプレイヤー（開発中） -

   ```
   https://drmtest2.adobe.com/TVSDK_HTML5/samples/reference/reference_player.html
   ```

   **FairPlay設定のテスト時に再生をチェックする：FairPlay** を使用する場合、ExpressPlayライセンスサーバーを使用するときに、コンテンツを再生するために追加の手順が必要です。[!DNL curl]を使用して接続をテストする場合（[ライセンス](../../multi-drm-workflows/quick-start/handle-the-licensing.md)で説明）は、次のように&#x200B;*M3U8マニフェスト*（パッケージ化されたコンテンツ）を編集する必要があります。

1. ライ追加センストークンリクエストからマニフェスト内の`#EXT-X-KEY:`タグに返された応答。と
1. そのURLのプロトコルを（現在はマニフェスト内に）応答から`https://`に変更し、`skd://`に変更します。

   FairPlayを使用して再生をテストする例を、ライセンス手順を含めて以下に示します。

1. FairPlayライセンストークンリクエストを使用して、ライセンストークンURLを取得します。 （独自の実稼働用ユーザー認証子を使用し、FairPlayコンテンツのパッケージ化に使用したのと同じCEKおよび`iv`を必ず使用してください）。 次のコマンドを実行して、サンプルコンテンツのライセンストークンURLを取得します。

   ```
   curl -v "https://fp-gen.service.expressplay.com/hms/fp/token? 
   customerAuthenticator=[YOUR-PRODUCTION-AUTHENTICATOR]&errorFormat=json 
   &contentKey CEK as query parameter contentKey 
   =[YOUR CONTENT KEY]&iv=[YOUR IV]"
   ```

   次のようなライセンストークンURLが返されます。

   ```
   https://fp.service.expressplay.com:80/hms/fp/rights/? 
   ExpressPlayToken=AQAAABNlKcEAAABQaTjshua3cWjG_Il3fvhf3g-CR1rn 
   JKdtaVaAnhkfTCW0bWAU76YgwForbrXhD5tXUHhfP7FD1svvLPxN5qomYsnwY 
   SSwcDq1ZnRtXunFLueTw6LAL52aZllMLasCSzYRMaAVHw 
   ```

1. 返されたライセンストークンURLレスポンスをM3U8マニフェストに追加し、*ライセンストークンURLのスキームを`https://`から* `sdk://`に変更します。 M3U8マニフェスト内の#EXT-X-KEYタグの例を以下に示します。

   ```
   #EXT-X-KEY:METHOD=SAMPLE-AES, 
   URI="skd://fp.service.expressplay.com:80/hms/fp/rights/? 
   ExpressPlayToken=AQAAABNlKcEAAABQaTjshua3cWjG_Il3fvhf3g- 
   CR1rnJKdtaVaAnhkfTCW0bWAU76YgwForbrXhD5tXUHhfP7FD1svvLPx 
   N5qomYsnwYSSwcDq1ZnRtXunFLueTw6LAL52aZllMLasCSzYRMaAVHw", 
   KEYFORMAT="com.apple.streamingkeydelivery",KEYFORMATVERSIONS="1"
   ```

   >[!NOTE]
   >
   >上記の情報は、FairPlay設定のテストにのみ適用されます。 FairPlayハンドラーの設定方法によっては、実稼働環境の設定には適用されない場合があります。 詳しくは、[iOSアプリケーションでApple FairPlayを有効にする](../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-apple-fairplay-tvsdk.md)を参照してください。

ビデオを再生できた場合は、コンテンツのパッケージ化とライセンスが正常に完了しています。 ビデオが再生されない場合は、トラブルシューティングページでトラブルの解決方法を確認してください。

<!--<a id="example_603D92A1F3924467B5D66EC862B8F59C"></a>-->

例えば、上に示した最初のテストプレイヤーのUIの一部を次に示します。ここで、ExpressPlayサーバーから取得したライセンス情報を指定します。

<!--<a id="fig_zjy_q2c_rw"></a>-->

![](assets/sample-player-drm-settings-web.png)
