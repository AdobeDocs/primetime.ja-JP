---
description: DRMワークフローでは、コンテンツのパッケージ化、コンテンツのライセンスの提供、および保護されたコンテンツの独自のビデオアプリケーションからの再生が行われます。 ワークフローは、各DRMソリューションで一般的に似ていますが、いくつかの違いが詳細にあります。
seo-description: DRMワークフローでは、コンテンツのパッケージ化、コンテンツのライセンスの提供、および保護されたコンテンツの独自のビデオアプリケーションからの再生が行われます。 ワークフローは、各DRMソリューションで一般的に似ていますが、いくつかの違いが詳細にあります。
seo-title: FairPlayのMulti-DRMワークフロー
title: FairPlayのMulti-DRMワークフロー
uuid: cd940a70-400c-435e-8322-55bd624164e1
translation-type: tm+mt
source-git-commit: 29149594c4b41956a091ef27093304e74ff15f2f

---


# FairPlayのMulti-DRMワークフロー {#multi-drm-workflow-for-fairplay}

DRMワークフローでは、コンテンツのパッケージ化、コンテンツのライセンスの提供、および保護されたコンテンツの独自のビデオアプリケーションからの再生が行われます。 ワークフローは、各DRMソリューションで一般的に似ていますが、いくつかの違いが詳細にあります。

このMulti-DRMワークフローでは、Apple FairPlayで保護されたHLSコンテンツのセットアップ、パッケージ化、ライセンス、再生を行います。 このワークフローには、オフライン再生とライセンスのローテーションを実装するためのオプションの手順も含まれています。

## FairPlayでExpressPlayサービスを有効にする {#enable-expressplay-service-for-fairplay}

AppleのFairPlay DRMソリューションをExpressPlay DRMサービスと共に使用する場合は、ある程度の設定が必要です。 これには、Appleから資格情報を取得し、ExpressPlayにアップロードする必要があります。

FairPlayコンテンツ保護用にExpressPlayサービスを有効にするには、次の手順に従います。

1. Appleから資格情報を取得します。

   これらの資格情報は、各サービスプロバイダーに対して一意にプロビジョニングされます。 次のフォームに入力して、リクエストを送信する必要があります。 [https://developer.apple.com/contact/fps/](https://developer.apple.com/contact/fps/)。

   >[!NOTE]
   >
   >「プライマリ **[!UICONTROL Content Provider]** ロール」を選択します。

   リクエストが承認されると、 *FairPlay Streaming Deployment PackageがAppleから送信されます*。
1. 証明書署名要求の生成を参照してください。

   を使用して、公 [!DNL openssl] 開鍵と秘密鍵のペア、および証明書署名要求(CSR)を生成できます。

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
      >この手順は、 *FairPlay Streaming Deployment Packageに記載されていますが*、参考のためにここに記載されています。 プロセスのこの部分で問題が発生した場合は、(展開パッケージの ** )FairPlayCertificateCreation.pdfの手順を確認してください。

1. Apple Developer PortalからCSRをアップロードします。
   1. 開発チームのチームエージェントは、ログインする必要がありま [!DNL developer.apple.com/account]す。
   1. をクリック **[!UICONTROL Certificates, Identifiers & Profiles]**&#x200B;し、次にペ **[!UICONTROL iOS, tvOS, watchOS]** ージの左上にあるドロップダウンを選択して、ページの左 **[!UICONTROL Certificates->Production]** 側にあるをクリックします。
   1. ページの右 **[!UICONTROL +]** 上にあるボタンをクリックして、新しい証明書を要求します。 の下のオプション **[!UICONTROL FairPlay Streaming Certificate]** を選択しま **[!UICONTROL Production]**&#x200B;す。

      iOS証明 *書を追加ダイアログ* が開きます。
   1. iOS証明書 *の追加で*、手順2.bで生成したCSRファイルをアップロードし、をクリックします **[!UICONTROL Generate]**。

      同じダイアログにアプリケーション秘密鍵(ASK)が表示されます。
   1. ASKを書き留め、安全な場所に保存します。
   1. ASKのキーを押して証明書の生成を完了し、をクリックしま **[!UICONTROL Continue]**&#x200B;す。
   1. ASKを保存したことを確認したら、をクリックして続 **[!UICONTROL Generate]** 行します。

      >[!NOTE] {importance=&quot;high&quot;}
      >
      >ASKのコピーを保存し、安全に保存することが重要です。 *ASKが侵害された場合、FairPlay Streamingでコンテンツを保護できなくなります。* チームに割り当てられるASKは1つだけです。 この値は再び提供されず、後で取得することはできません。

   1. FPS証明書をダウンロードします。

      （手順2.aの）秘密鍵と公開鍵（この手順でダウンロードしたFPS証明書）のバックアップコピーを安全な場所に保存してください。
1. FairPlayの資格情報を使用してExpressPlayアカウントを設定します。
   1. 手順3.hでダウンロードした証明書名を考えてみましょう。が含まれ [!DNL fairplay.cer]る。
   1. Apple Keychain Accessユーテ [!DNL fairplay.cer] ィリティでファイルを開きます。
   1. 右上の検索フィールドに「 `fairplay`」と入力して、多数の証明書をフィルタリングします。
   1. 会社のFairPlay証明書を特定します。

      会社名は、Appleが発行した証明書に関連付ける必要があります。
   1. 展開矢印を選択して証明書を展開し、秘密鍵を右クリックします。
   1. ファイル **[!UICONTROL Export "Your Company Name"]** を選択して保存 [!DNL .p12] します。

      このファイルを保護するためのパスワードを割り当てるように求められます。 このパスワードは、資格情報パッケージと共に送信する必要があるので、メモしておきます。
   1. www.expressplay.comでアカウントにログイン [します](https://www.expressplay.com)。
   1. 左上 **[!UICONTROL DRM SERVICES]** のをクリックし、タブを選択し **[!UICONTROL FairPlay]** ます。
   1. FairPlayの資格情報をExpressPlayアカウントにアップロードします。

      1. ASKの値を含むテキストファイルを作成します(例： `1234567890abcdef1234567890abcdef`)をクリックし、アップロードするファイルを選択します。
      1. 手順4.fでPKCS12ファイルを選択します。をアップロードします。
      1. 手順4.fのPKCS12ファイルのパスワードを入力します。
      1. 「アップロード」ボタンをクリックします。

これで、FairPlay用のExpressPlayサービスを使用して、証明書と共にFairPlayコンテンツ保護を備えたiOSアプリケーションま [!DNL fairplay.cer] たはHTML5ページを作成できます。

<!--<a id="fig_sjr_2pn_sv"></a>-->

![](assets/multi_drm_expressplay_drm_services_web.png)

### FairPlay用にコンテンツをパッケージ化する {#package-your-content-for-fairplay}

コンテンツをパッケージ化するには、Adobe Offline PackagerまたはExpressPlayのBento4パッケージャーなどの他のツールを使用できます。

パッケージャーは、再生するビデオを準備（元のファイルをフラグメント化し、マニフェストに含めるなど）し、選択したDRMソリューション（この場合はFairPlay）でビデオを保護します。

* [FairPlay DRM用Adobe Offline Packager](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf#page=21)
* [ExpressPlayパッケージャー — Bento4 for HLS](https://www.bento4.com/developers/hls/)

<!--<a id="fig_jbn_fw5_xw"></a>-->

![](assets/pkg_lic_play_hls_web.png)

1. コンテンツをパッケージ化します。

   Adobe Offline Packagerを使用したパッケージ化の例を次に示します。 Packagerでは設定ファイル(例： [!DNL fairplay.xml])が使用され、次のようになります。

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

   * `in_path`  — このエントリは、ローカルのパッケージ化コンピューター上のソースビデオの場所を指します。
   * `out_type`  — このエントリは、パッケージ化された出力のタイプを示します。この例では、FairPlayのHLSです。
   * `out_path`  — 出力先のローカルマシン上の場所。
   * `drm_sys`  — パッケージ化するDRMソリューション。 これはこ `FAIRPLAY` の場合です。
   * `frag_dur`  — フラグメントの時間（秒単位）。
   * `target_dur` - HLS出力のターゲット期間。
   * `key_file_path`  — これは、コンテンツ暗号化キー(CEK)として機能するパッケージ化コンピューター上のライセンスファイルの場所です。 これは、Base-64エンコードされた16バイトの16進文字列です。
   * `iv_file_path`  — これは、パッケージ化を行うコンピューター上のIVファイルの場所です。
   * `key_url`  — ファイルのタグのURI `EXT-X-KEY` パラメータ [!DNL .m3u8] ー。
   * `content_id`  — デフォルト値。
   [Packagerのドキュメントに記載されているように](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf#page=7)、「ベストプラクティスとして、出力の生成に使用する一般的なオプションを含む設定ファイルを作成します。 次に、特定のオプションをコマンドライン引数として指定して、出力を作成します。」

   ```
   java -jar OfflinePackager.jar -in_path sample.mp4 -out_type hls 
   -out_path out_file_path -drm -drm_sys FAIRPLAY -key_file_path "creds/fairplay.bin" 
   -key_url "user_provided_value"
   ```

   生成されたM3U8ファイルには、次のよ `EXT-X-KEY` うな属性が含まれます。

   ```
   #EXT-X-KEY:METHOD=SAMPLE-AES,URI="user_provided_value",​
   KEYFORMAT="com.apple.streamingkeydelivery",KEYFORMATVERSIONS="1" 
   ```

### FairPlayのポリシーの設定 {#setting-policies-for-fairplay}

エンタイトルメントサーバーを使用して、FairPlayで保護されたコンテンツのポリシーを設定できます。 独自の設定を行うことも、アドビが提供するサンプルのエンタイトルメントサーバーを使用することもできます。

アドビでは、時間ベースおよびデバイスバインディングのエンタイトルメントを行う方法を示す *サンプルのExpressPlay* Entitlement Server(SEES *)* を提供しています。 このサンプルのエンタイトルメントサーバーは、ExpressPlayサービスの上に構築されています。

[参照サーバ：ExpressPlayエンタイトルメントサーバーの例(SEE)](../../multi-drm-workflows/feature-topics/sees-reference-server.md)

* [リファレンスサービス：時間ベースの権利付与](../../multi-drm-workflows/feature-topics/sees-reference-server-time-entitlement.md)
* [リファレンスサービス：デバイスバインディングのエンタイトルメント](../../multi-drm-workflows/feature-topics/sees-reference-server-binding-entitlement.md)

## FairPlayのライセンスと再生 {#licensing-and-playback-for-fairplay}

FairPlayで保護されたコンテンツのライセンスと再生には、ビデオマニフェストファイル(skd:)で使用されるスキームとExpressPlayトークンリクエスト(https:)で使用されるスキームとの間で、URLスキームの入れ替えが必要です。

iOS TVSDKクライアントからのライセンスおよび再生を実装する手順は、次のとおりです。TVSDKア [プリケーションでApple FairPlayを有効にします](../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-apple-fairplay-tvsdk.md)。 また、FairPlay用に、オフライン再生とライセンスローテーションをオプションで実装することもできます。

## HLS Offline with FairPlay {#section_047A05D1E3B64883858BC601CFC8F759}

FairPlayで保護されたコンテンツは、Web上（飛行機など）から離れているため、ライセンスを取得できない場合に、ユーザーがFairPlayで保護されたコンテンツを再生できるようにすることが必要な場合があります。

この作業を開始する前に、Appleのドキュメント「Offline Playback with FairPlay Streaming and HTTP Live Streaming」 **をダウンロードしてお読みください**。 Transport Stream(TS)セグメントをダウンロードし、ローカルマシンに保存する方法について説明します。

FairPlay用のオフライン再生を次のワークフローで実装します。

1. HLS TSセグメントをダウンロードします。
1. FairPlayサーバーから永続的なレンタルライセンスをリクエストします( **「FairPlayの永続的なレンタルポリシー」を参照**)。
1. を保存しま `persistentContentKey`す。
1. FairPlayコンテンツをオフラインで再生します。

>[!NOTE]
>
>クライアント上のFairPlay Streamingは、持続的なコンテンツキーの有効期限が切れた場合、復号化を開始しません。 ただし、再生中にコンテンツキーの有効期限が切れた場合は、引き続きユーザーエクスペリエンスが使用されます。
>
>詳しくは [、『HTTPライブストリーミングの操作](https://developer.apple.com/library/content/documentation/AudioVideo/Conceptual/MediaPlaybackGuide/Contents/Resources/en.lproj/HTTPLiveStreaming/HTTPLiveStreaming.html#//apple_ref/doc/uid/TP40016757-CH11-SW3) 』ドキュメントを参照してください。

### FairPlayライセンスローテーション {#section_D32AA08C61474B4F876AC2A5F18CB879}

ライセンスのローテーションは、長時間再生されるコンテンツのライセンスハッキングを防ぐためのスキームです。

M3U8マニフェストでは、各キータグは次のキータグまで、またはファイルの最後まで、次のTSセグメントに適用されます。

ライセンスローテーションを追加するには、次の手順を実行します。

* ライセンスのローテーション時に新しいFairPlayキータグを挿入します。

   任意の数のキータグを追加できます。

   リニアコンテンツの場合は、M3U8ウィンドウで最新のキータグを必ず保持してください。 再生するTSセグメントが2つ残っている場合（約20秒）、iOSは次のM3U8をリクエストします。 新しいM3U8に新しいキータグが含まれている場合、すべてのキー要求が直ちに発生します。 以前の既存のキーは、再び要求されません。 iOSは、再生が開始される前に、すべての主要な要求が完了するのを待ちます。

   ライセンスローテーションを含むVODコンテンツの場合、すべてのキー要求は再生の開始時に発生します。

   以下は、キーの回転を伴うM3U8の例です。

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
