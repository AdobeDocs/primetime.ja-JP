---
description: DRMソリューションをテストするには、作業中の特定のDRMソリューションを処理できるビデオアプリケーションが必要です。 このプレーヤーは、アドビが提供するサンプルプレイヤー、または独自のTVSDKベースのビデオアプリケーションのいずれかです。
seo-description: DRMソリューションをテストするには、作業中の特定のDRMソリューションを処理できるビデオアプリケーションが必要です。 このプレーヤーは、アドビが提供するサンプルプレイヤー、または独自のTVSDKベースのビデオアプリケーションのいずれかです。
seo-title: 保護されたコンテンツの再生
title: 保護されたコンテンツの再生
uuid: 84f73ee7-43d0-481c-a5e7-14f92169323c
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# 保護されたコンテンツの再生 {#playback-your-protected-content}

DRMソリューションをテストするには、作業中の特定のDRMソリューションを処理できるビデオアプリケーションが必要です。 このプレーヤーは、アドビが提供するサンプルプレイヤー、または独自のTVSDKベースのビデオアプリケーションのいずれかです。

1. ExpressPlayサーバーから返されたトークン応答のライセンスサーバーURLを使用して、保護されたコンテンツを再生できるかどうかをテストします。

   * **Widevine** - ExpressPlayライセンストークンリクエストから受け取ったWidevine応答を直接使用します。
   * **PlayReady** — ライセンストークンリクエストから返されたJSONオブジェクトから、ライセンスサーバーのURLとトークンを取得します。
   * **FairPlay** - ExpressPlayライセンストークンリクエストから受け取ったFairPlay応答を直接使用します。

1. 独自のプレーヤーまたは既存のAdobeサンプルプレーヤーを使用して、保護されたコンテンツの再生をテストします。

   保護されたコンテンツへのURL（テストするDRMソリューションに応じて、M3U8またはMPDマニフェストの場所）を指定します。

   テストに使用するプレーヤーが提供するインターフェイスに応じて、ライセンスURLとトークンを入力フィールドの文字列として、またはテキストボックスに貼り付けるJSONオブジェクトとして、またはURLのクエリパラメーターとして指定するように求められます。

   テストプレーヤーの可能性を次に示します。

   * HTML5リファレンスプレイヤー：

      ```
      https://ptdemos.com/html5/internal/1_2/2.4_GM/samples/reference/reference_player.html
      ```

   * 釈迦演奏者

      ```
      https://shaka-player-demo.appspot.com
      ```

   * サンプルTVSDKプレイヤー（開発中） -

   ```
   https://drmtest2.adobe.com/TVSDK_HTML5/samples/reference/reference_player.html
   ```

   **FairPlay設定のテスト時の再生の確認：** FairPlayを使用する場合、ExpressPlayライセンスサーバーを使用する際に、コンテンツを再生するために追加の手順が必要です。 を使用して接続をテ [!DNL curl] ストする場合( [Licensing](../../multi-drm-workflows/quick-start/handle-the-licensing.md))、M3U8マニフェスト ** （パッケージ化されたコンテンツ）を次のように編集する必要があります。

1. ライセンストークンリクエストから返された応答をマニフェスト内の `#EXT-X-KEY:` タグに追加します。および
1. そのURLのプロトコルを（現在はマニフェスト内に）応答からからに変更し `https://` ます `skd://`。

   ライセンス手順を含む、FairPlayでの再生のテストの完全な例を次に示します。

1. FairPlayライセンストークンリクエストを使用して、ライセンストークンURLを取得します。 (独自の実稼動用ユーザー認証子を使用し、FairPlayコンテンツのパッケージ化に使用したCEK `iv` と同じCEKを必ず使用してください)。次のコマンドを実行して、サンプルコンテンツのライセンストークンURLを取得します。

   ```
   curl -v "https://fp-gen.service.expressplay.com/hms/fp/token? 
   customerAuthenticator=[YOUR-PRODUCTION-AUTHENTICATOR]&errorFormat=json 
   &contentKey CEK as query parameter contentKey 
   =[YOUR CONTENT KEY]&iv=[YOUR IV]"
   ```

   次のようなライセンストークンURLを含む応答が返されます。

   ```
   https://fp.service.expressplay.com:80/hms/fp/rights/? 
   ExpressPlayToken=AQAAABNlKcEAAABQaTjshua3cWjG_Il3fvhf3g-CR1rn 
   JKdtaVaAnhkfTCW0bWAU76YgwForbrXhD5tXUHhfP7FD1svvLPxN5qomYsnwY 
   SSwcDq1ZnRtXunFLueTw6LAL52aZllMLasCSzYRMaAVHw 
   ```

1. 返されたライセンストークンURL応答をM3U8マニフェストに入れ、 *ライセンストークンURLのスキームを* からに変更 `sdk://` します `https://`。 M3U8マニフェスト内の#EXT-X-KEYタグの例を次に示します。

   ```
   #EXT-X-KEY:METHOD=SAMPLE-AES, 
   URI="skd://fp.service.expressplay.com:80/hms/fp/rights/? 
   ExpressPlayToken=AQAAABNlKcEAAABQaTjshua3cWjG_Il3fvhf3g- 
   CR1rnJKdtaVaAnhkfTCW0bWAU76YgwForbrXhD5tXUHhfP7FD1svvLPx 
   N5qomYsnwYSSwcDq1ZnRtXunFLueTw6LAL52aZllMLasCSzYRMaAVHw", 
   KEYFORMAT="com.apple.streamingkeydelivery",KEYFORMATVERSIONS="1"
   ```

   >[!NOTE] {importance=&quot;high&quot;}
   >
   >上記の情報は、FairPlay設定のテストにのみ適用されます。 FairPlayハンドラーの設定方法によっては、実稼働環境の設定には適用されない場合があります。 詳しくは [、iOSアプリケーションでのApple FairPlayの有効化](../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-apple-fairplay-tvsdk.md) （英語のみ）を参照してください。

ビデオを再生すると、コンテンツのパッケージ化とライセンス認証が完了します。 ビデオが再生されない場合は、トラブルシューティングページで問題の解決方法を確認してください。

<!--<a id="example_603D92A1F3924467B5D66EC862B8F59C"></a>-->

例えば、上記の最初のテストプレーヤーのUIの一部を次に示します。ここで、ExpressPlayサーバーから取得したライセンス情報を指定します。

<!--<a id="fig_zjy_q2c_rw"></a>-->

![](assets/sample-player-drm-settings-web.png)
