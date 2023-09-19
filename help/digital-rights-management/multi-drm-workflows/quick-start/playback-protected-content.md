---
description: DRM ソリューションをテストするには、使用している特定の DRM ソリューションを処理できるビデオアプリケーションが必要です。 このプレーヤーには、Adobeが使用可能にしたサンプルプレーヤー、または独自の TVSDK ベースのビデオアプリケーションが含まれます。
title: 保護されたコンテンツの再生
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 0%

---

# 保護されたコンテンツの再生 {#playback-your-protected-content}

DRM ソリューションをテストするには、使用している特定の DRM ソリューションを処理できるビデオアプリケーションが必要です。 このプレーヤーには、Adobeが使用可能にしたサンプルプレーヤー、または独自の TVSDK ベースのビデオアプリケーションが含まれます。

1. ExpressPlay サーバーから返されたトークン応答のライセンスサーバー URL を使用して、保護されたコンテンツを再生できるかどうかをテストします。

   * **Widevine** - ExpressPlay ライセンストークンリクエストから受け取った Widevine 応答を直接使用します。
   * **PlayReady**  — ライセンストークンリクエストから返された JSON オブジェクトから、ライセンスサーバーの URL とトークンを取得します。
   * **FairPlay** - ExpressPlay ライセンストークンリクエストから受け取った FairPlay 応答を直接使用します。

1. 独自のプレーヤーまたは既存のプレーヤーサンプルプレーヤーを使用して、保護されたコンテンツのAdobeをテストします。

   保護されたコンテンツの URL を指定します（テストする DRM ソリューションに応じて、M3U8 または MPD マニフェストの場所）。

   テストするプレーヤーが提供するインターフェイスに応じて、ライセンス URL とトークンを入力フィールドの文字列として、またはテキストボックスに貼り付けた JSON オブジェクトとして、または URL のクエリパラメーターとして指定するよう求められます。

   テストプレーヤーの可能性の一部を以下に示します。

   * HTML5 リファレンスプレーヤー：

     ```
     https://ptdemos.com/html5/internal/1_2/2.4_GM/samples/reference/reference_player.html
     ```

   * 釈迦奏者：

     ```
     https://shaka-player-demo.appspot.com
     ```

   * サンプル TVSDK プレーヤー（開発中） -

   ```
   https://drmtest2.adobe.com/TVSDK_HTML5/samples/reference/reference_player.html
   ```

   **FairPlay 設定をテストする際の再生の確認：** FairPlay では、ExpressPlay ライセンスサーバーを使用する際に、コンテンツを再生するために追加の手順が必要です。 を使用している場合、 [!DNL curl] 接続をテストするには、 [ライセンス](../../multi-drm-workflows/quick-start/handle-the-licensing.md))、 *M3U8 マニフェストを編集* （パッケージ化されたコンテンツ）を次に示します。

1. ライセンストークンリクエストから返された応答をに追加します。 `#EXT-X-KEY:` マニフェスト内のタグ、および
1. その URL のプロトコルを（現在はマニフェスト内に）から、 `https://` から `skd://`.

   ライセンス手順を含む、FairPlay で再生をテストする完全な例を次に示します。

1. FairPlay ライセンストークンリクエストを使用して、ライセンストークン URL を取得します。 ( 独自の実稼動用ユーザー認証子を使用し、必ず同じ CEK と `iv` FairPlay コンテンツのパッケージ化に使用された )。 次のコマンドを実行して、サンプルコンテンツのライセンストークン URL を取得します。

   ```
   curl -v "https://fp-gen.service.expressplay.com/hms/fp/token? 
   customerAuthenticator=[YOUR-PRODUCTION-AUTHENTICATOR]&errorFormat=json 
   &contentKey CEK as query parameter contentKey 
   =[YOUR CONTENT KEY]&iv=[YOUR IV]"
   ```

   次のようなライセンストークン URL が返されます。

   ```
   https://fp.service.expressplay.com:80/hms/fp/rights/? 
   ExpressPlayToken=AQAAABNlKcEAAABQaTjshua3cWjG_Il3fvhf3g-CR1rn 
   JKdtaVaAnhkfTCW0bWAU76YgwForbrXhD5tXUHhfP7FD1svvLPxN5qomYsnwY 
   SSwcDq1ZnRtXunFLueTw6LAL52aZllMLasCSzYRMaAVHw 
   ```

1. 返されたライセンストークン URL の応答を M3U8 マニフェストに入れ、 *ライセンストークン URL のスキームを次に変更します。* `sdk://` から `https://`. M3U8 マニフェスト内の#EXT-X-KEYタグの例を次に示します。

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
   >前述の情報は、FairPlay 設定のテストにのみ適用されます。 FairPlay ハンドラーの設定方法によっては、実稼動環境の設定には適用されない場合があります。 詳しくは、 [iOSアプリケーションでのApple FairPlay の有効化](../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-apple-fairplay-tvsdk.md) 」を参照してください。

ビデオが再生された場合は、コンテンツのパッケージ化とライセンスが正常に完了しています。 ビデオが再生されない場合は、トラブルシューティングページで、問題の解決方法を確認してください。

<!--<a id="example_603D92A1F3924467B5D66EC862B8F59C"></a>-->

例えば、上記の最初のテストプレーヤーの UI には、ExpressPlay サーバーから取得したライセンス情報を次のように表示しています。

<!--<a id="fig_zjy_q2c_rw"></a>-->

![](assets/sample-player-drm-settings-web.png)
