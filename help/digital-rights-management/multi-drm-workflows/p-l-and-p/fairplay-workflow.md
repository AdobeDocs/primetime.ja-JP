---
description: DRMワークフローでは、コンテンツのパッケージ化、コンテンツのライセンスの提供、および保護されたコンテンツの独自のビデオアプリケーションからの再生が行われます。 ワークフローは、各DRMソリューションに対して一般的に似ていますが、詳細にはいくつかの違いがあります。
seo-description: DRMワークフローでは、コンテンツのパッケージ化、コンテンツのライセンスの提供、および保護されたコンテンツの独自のビデオアプリケーションからの再生が行われます。 ワークフローは、各DRMソリューションに対して一般的に似ていますが、詳細にはいくつかの違いがあります。
seo-title: FairPlay用のMulti-DRMワークフロー
title: FairPlay用のMulti-DRMワークフロー
uuid: cd940a70-400c-435e-8322-55bd624164e1
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '1514'
ht-degree: 0%

---


# FairPlay用のMulti-DRMワークフロー{#multi-drm-workflow-for-fairplay}

DRMワークフローでは、コンテンツのパッケージ化、コンテンツのライセンスの提供、および保護されたコンテンツの独自のビデオアプリケーションからの再生が行われます。 ワークフローは、各DRMソリューションに対して一般的に似ていますが、詳細にはいくつかの違いがあります。

このMulti-DRMワークフローでは、Apple FairPlayで保護されたHLSコンテンツのセットアップ、パッケージ化、ライセンス、再生を行います。 このワークフローには、オフライン再生とライセンスのローテーションを実装するためのオプションの手順も含まれています。

## FairPlay向けExpressPlayサービスを有効にする{#enable-expressplay-service-for-fairplay}

AppleのFairPlay DRMソリューションをExpressPlay DRMサービスで使用する場合は、ある程度の設定が必要です。 これには、Appleから秘密鍵証明書を取得し、ExpressPlayにアップロードする必要があります。

FairPlayコンテンツ保護用にExpressPlayサービスを有効にするには、次の手順に従います。

1. Appleから資格情報を取得します。

   これらの資格情報は、各サービスプロバイダーに対して一意にプロビジョニングされます。 次のフォームに記入して、リクエストを行う必要があります。[https://developer.apple.com/contact/fps/](https://developer.apple.com/contact/fps/).

   >[!NOTE]
   >
   >「プライマリロール」に&#x200B;**[!UICONTROL Content Provider]**&#x200B;を選択します。

   リクエストが承認されると、Appleから&#x200B;*FairPlay Streaming Deployment Package*&#x200B;が送信されます。
1. 証明書署名要求を生成します。

   [!DNL openssl]を使用して、公開鍵と秘密鍵のペアと、証明書署名要求(CSR)を生成できます。

   1. キーペアを生成します。

      ```
      openssl genrsa -aes256 -out privatekey.pem 1024 
      ```

   1. CSRを生成します。

      ```
      openssl req -new -sha1 -key privatekey.pem -out certreq.csr  
        -subj "/CN=SubjectName /OU=OrganizationalUnit /O=Organization /C=US"
      ```

      >[!NOTE]
      >
      >この手順は&#x200B;*FairPlay Streaming Deployment Package*&#x200B;に記載されていますが、参考のためにここに記載します。 プロセスのこの部分で問題が発生した場合は、（展開パッケージ内の）*FairPlayCertificateCreation.pdf*&#x200B;の説明を確認してください。

1. Apple Developer PortalでCSRをアップロードします。
   1. 開発チームのチームエージェントは[!DNL developer.apple.com/account]にログインする必要があります。
   1. **[!UICONTROL Certificates, Identifiers & Profiles]**&#x200B;をクリックし、ページの左上にある&#x200B;**[!UICONTROL iOS, tvOS, watchOS]**&#x200B;ドロップダウンを選択してから、ページの左にある&#x200B;**[!UICONTROL Certificates->Production]**&#x200B;をクリックします。
   1. ページ右上の&#x200B;**[!UICONTROL +]**&#x200B;ボタンをクリックして、新しい証明書を要求します。 **[!UICONTROL Production]**&#x200B;の下の&#x200B;**[!UICONTROL FairPlay Streaming Certificate]**&#x200B;オプションを選択します。

      *iOS追加証明書*&#x200B;ダイアログが開きます。
   1. *追加 iOS証明書*&#x200B;に、手順2.bで生成したCSRファイルをアップロードし、**[!UICONTROL Generate]**&#x200B;をクリックします。

      アプリケーション秘密鍵キー(ASK)が同じダイアログに表示されます。
   1. ASKを書き留め、安全な場所に保存します。
   1. ASKのキーを入力して証明書の生成を完了し、**[!UICONTROL Continue]**&#x200B;をクリックします。
   1. ASKを保存したことを確認したら、**[!UICONTROL Generate]**&#x200B;をクリックして続行します。

      >[!NOTE]
      >
      >ASKのコピーを保存し、安全に保存することが重要です。 *ASKに問題が発生した場合、FairPlay Streamingでコンテンツを保護できなくなります。* チームに割り当てられるASKは1つだけです。値は再度提供されなくなり、後で取得することはできません。

   1. FPS証明書をダウンロードします。

      （手順2.aの）秘密鍵と公開鍵（この手順でダウンロードしたFPS証明書）のバックアップコピーを必ず安全な場所に保存してください。
1. FairPlayの資格情報を使用して、ExpressPlayアカウントを設定します。
   1. 手順3.hでダウンロードした証明書名を考えてみましょう。は[!DNL fairplay.cer]です。
   1. Apple Keychain Accessユーティリティで[!DNL fairplay.cer]ファイルを開きます。
   1. 右上の検索フィールドに「`fairplay`」と入力して、多数の証明書をフィルターします。
   1. 会社のFairPlay証明書を識別します。

      会社名は、Appleが発行した証明書と関連付ける必要があります。
   1. 展開矢印を選択して証明書を展開し、秘密鍵を右クリックします。
   1. **[!UICONTROL Export "Your Company Name"]**&#x200B;を選択し、[!DNL .p12]ファイルを保存します。

      このファイルを保護するためのパスワードを割り当てるように求められます。 このパスワードは資格情報パッケージと共に送信する必要があるので、書き留めておいてください。
   1. [www.expressplay.com](https://www.expressplay.com)でアカウントにログインします。
   1. 左上の&#x200B;**[!UICONTROL DRM SERVICES]**&#x200B;をクリックし、「**[!UICONTROL FairPlay]**」タブを選択します。
   1. FairPlayの資格情報をExpressPlayアカウントにアップロードします。

      1. ASKの値を含むテキストファイルを作成します(例：`1234567890abcdef1234567890abcdef`)に置き換え、アップロードするファイルを選択します。
      1. 手順4.fのPKCS12ファイルを選択します。をアップロード用に追加します。
      1. 手順4.fのPKCS12ファイルのパスワードを入力します。
      1. 「アップロード」ボタンをクリックします。

これで、FairPlay向けExpressPlayサービスを使用して、[!DNL fairplay.cer]証明書と共に、FairPlayコンテンツ保護を備えたiOSアプリまたはHTML5ページを作成できます。

<!--<a id="fig_sjr_2pn_sv"></a>-->

![](assets/multi_drm_expressplay_drm_services_web.png)

### FairPlay用にコンテンツをパッケージ化する{#package-your-content-for-fairplay}

コンテンツをパッケージ化するには、AdobeのOffline Packagerを使用するか、ExpressPlayのBento4パッケージャーなどの他のツールを使用します。

パッケージャーは、再生するビデオを準備（元のファイルをフラグメント化してマニフェストに含めるなど）し、選択したDRMソリューション（この場合FairPlay）でビデオを保護します。

* [FairPlay DRM用のAdobeオフラインパッケージャー](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf#page=21)
* [ExpressPlayパッケージャー — Bento4 for HLS](https://www.bento4.com/developers/hls/)

<!--<a id="fig_jbn_fw5_xw"></a>-->

![](assets/pkg_lic_play_hls_web.png)

1. コンテンツをパッケージ化します。

   AdobeOffline Packagerを使用したパッケージ化の例を次に示します。 Packagerは設定ファイル（例：[!DNL fairplay.xml]）を使用し、次のようになります。

   ```
   <config>
   <in_path>mp4_file_path</in_path>
   <out_type>hls</out_type>
   <out_path>out_file_path</out_path>
   <drm/>
   <drm_sys>FAIRPLAY</drm_sys>
   <frag_dur>4</frag_dur>
   <target_dur>6</target_dur>
   <key_file_path>creds/fairplay.bin</key_file_path>
   <iv_file_path>creds/iv.bin</iv_file_path>
   <key_url>user_provided_value</key_url>
   <content_id>_default_</content_id>
   </config>
   ```

   * `in_path`  — このエントリは、パッケージ化を行うローカルコンピューター上のソースビデオの場所を指します。
   * `out_type`  — このエントリは、パッケージ化された出力のタイプを示します。この場合は、FairPlay向けHLSです。
   * `out_path`  — 出力を送信するローカルマシン上の場所。
   * `drm_sys`  — パッケージ化の対象とするDRMソリューション。この場合は`FAIRPLAY`です。
   * `frag_dur`  — フラグメントの時間（秒単位）
   * `target_dur` - HLS出力のターゲット時間。
   * `key_file_path`  — コンテンツ暗号化キー(CEK)の役割を果たすパッケージ化を行ったコンピューター上のライセンスファイルの場所です。Base-64エンコードされた16バイトの16進文字列です。
   * `iv_file_path`  — これは、パッケージ化を行うコンピューター上のIVファイルの場所です。
   * `key_url` - `EXT-X-KEY` ファイルの [!DNL .m3u8] タグのURIパラメータ。
   * `content_id`  — デフォルト値。

   [Packagerドキュメント](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf#page=7)に記載されているように、「ベストプラクティスとして、出力の生成に使用する一般的なオプションを含む設定ファイルを作成します。 次に、コマンドライン引数として特定のオプションを指定して、出力を作成します。」

   ```
   java -jar OfflinePackager.jar -in_path sample.mp4 -out_type hls 
   -out_path out_file_path -drm -drm_sys FAIRPLAY -key_file_path "creds/fairplay.bin" 
   -key_url "user_provided_value"
   ```

   生成されたM3U8ファイルには、次のような`EXT-X-KEY`属性があります。

   ```
   #EXT-X-KEY:METHOD=SAMPLE-AES,URI="user_provided_value",​
   KEYFORMAT="com.apple.streamingkeydelivery",KEYFORMATVERSIONS="1" 
   ```

### FairPlay {#setting-policies-for-fairplay}のポリシーの設定

エンタイトルメントサーバーを使用して、FairPlayで保護されたコンテンツのポリシーを設定できます。 独自のエンタイトルメントサーバーを設定することも、Adobeが提供するサンプルのエンタイトルメントサーバーを使用することもできます。

Adobeには、*時間ベースの*&#x200B;および&#x200B;*デバイスバインディング*&#x200B;のエンタイトルメントを行う方法を示す、ExpressPlayエンタイトルメントサーバー(SEES)のサンプルが用意されています。 このエンタイトルメントサーバーのサンプルは、ExpressPlayサービスに基づいて構築されています。

[参照サーバー：ExpressPlay権利付与サーバーのサンプル(SEE)](../../multi-drm-workflows/feature-topics/sees-reference-server.md)

* [リファレンスサービス：時間ベースの権利付与](../../multi-drm-workflows/feature-topics/sees-reference-server-time-entitlement.md)
* [リファレンスサービス：デバイスバインディングのエンタイトルメント](../../multi-drm-workflows/feature-topics/sees-reference-server-binding-entitlement.md)

## FairPlay {#licensing-and-playback-for-fairplay}のライセンスと再生

FairPlayで保護されたコンテンツのライセンスと再生には、ビデオマニフェストファイル(skd:)で使用されているスキームとExpressPlayトークンリクエスト(https:)で使用されているスキームとの間で、URLスキームを入れ替える必要があります。

iOS TVSDKクライアントからのライセンスおよび再生を実装する手順は、次のとおりです。[TVSDKアプリケーションでApple FairPlayを有効にする](../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-apple-fairplay-tvsdk.md)。 オプションで、FairPlay用にオフライン再生とライセンスローテーションを実装することもできます。

## FairPlayでHLSオフライン{#section_047A05D1E3B64883858BC601CFC8F759}

プレーヤーがWeb上（飛行機など）から切り離されているので、ライセンスを取得できない場合に、FairPlayで保護されたコンテンツをユーザーが再生できるようにしたい場合があります。

このタスクを開始する前に、Appleドキュメント&#x200B;**「Offline Playback with FairPlay Streaming and HTTP Live Streaming」**&#x200B;をダウンロードしてお読みください。 Transport Stream(TS)セグメントをダウンロードしてローカルマシンに保存する方法を学ぶには、このガイドを読んでください。

次のワークフローで、FairPlay用にオフライン再生を実装します。

1. HLS TSセグメントをダウンロードします。
1. FairPlayサーバーから永続的なレンタルライセンスを要求します（**&quot;FairPlay Persistent Rental Policy&quot;**&#x200B;を参照）。
1. `persistentContentKey`を保存します。
1. FairPlayコンテンツをオフラインで再生します。

>[!NOTE]
>
>クライアント上のFairPlay Streamingは、持続的なコンテンツキーの有効期限が切れた場合、復号を開始しません。 ただし、再生中にコンテンツキーの有効期限が切れても、ユーザーエクスペリエンスは引き続き有効です。
>
>詳しくは、[HTTPライブストリーミング](https://developer.apple.com/library/content/documentation/AudioVideo/Conceptual/MediaPlaybackGuide/Contents/Resources/en.lproj/HTTPLiveStreaming/HTTPLiveStreaming.html#//apple_ref/doc/uid/TP40016757-CH11-SW3)のドキュメントの使用を参照してください。

### FairPlayライセンスローテーション{#section_D32AA08C61474B4F876AC2A5F18CB879}

ライセンスのローテーションは、長い間再生されるコンテンツのライセンスのハッキングを防ぐためのスキームです。

M3U8マニフェストでは、各キータグは次のキータグまで、またはファイルの最後まで、次のTSセグメントに適用されます。

ライセンスローテーションを追加するには、次の手順を実行します。

* ライセンスのローテーション時間中に新しいFairPlayキータグを挿入します。

   任意の数のキータグを追加できます。

   リニアコンテンツの場合は、M3U8ウィンドウで最新のキータグを維持してください。 再生するTSセグメントが2つ（約20秒）ある場合、iOSは次のM3U8をリクエストします。 新しいM3U8に新しいキータグが含まれる場合は、すべてのキーリクエストが即座に実行されます。 以前の既存のキーは、再度要求されません。 iOSは、再生が開始する前に、すべての主要な要求が完了するのを待ちます。

   ライセンスローテーションを含むVODコンテンツの場合、すべての主要なリクエストは再生の開始時に発生します。

   以下は、キーが回転するM3U8の例です。

   ```
   #EXTM3U
   #EXT-X-TARGETDURATION:10
   #EXT-X-VERSION:5
   #EXT-X-MEDIA-SEQUENCE:0
   #EXT-X-PLAYLIST-TYPE:VOD
   #EXT-X-KEY:METHOD=SAMPLE-AES,URI="skd://one?cek=1dc2cc71d913f4f74eca0c4632
   212b25&iv=e21f0f72b6363ff6143737cb1e9ca8d7",KEYFORMAT="com.apple.streaming
   keydelivery",KEYFORMATVERSIONS="1"
   #EXTINF:10,
   fileSequence0.ts
   #EXTINF:10,
   fileSequence1.ts
   #EXTINF:10,
   fileSequence2.ts
   #EXTINF:10,
   fileSequence3.ts
   #EXTINF:10,
   fileSequence4.ts
   #EXTINF:10,
   fileSequence5.ts
   #EXTINF:10,
   fileSequence6.ts
   #EXTINF:10,
   fileSequence7.ts
   #EXTINF:10,
   #EXT-X-KEY:METHOD=SAMPLE-AES,URI="skd://two?cek=f6efc698b96cf8f4fa46d5237d
   337c77&iv=18401077091784bcda8079acf978dc95",KEYFORMAT="com.apple.streaming
   keydelivery",KEYFORMATVERSIONS="1"
   #EXTINF:10,
   fileSequence8.ts
   #EXTINF:10,
   ```
