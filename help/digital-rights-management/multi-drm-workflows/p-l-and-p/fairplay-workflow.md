---
description: DRM ワークフローには、コンテンツのパッケージ化、コンテンツのライセンス提供、独自のビデオアプリケーションからの保護されたコンテンツの再生が含まれます。 一般的に、ワークフローは各 DRM ソリューションで似ていますが、詳細にはいくつか違いがあります。
title: FairPlay の Multi-DRM ワークフロー
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1470'
ht-degree: 0%

---

# FairPlay の Multi-DRM ワークフロー {#multi-drm-workflow-for-fairplay}

DRM ワークフローには、コンテンツのパッケージ化、コンテンツのライセンス提供、独自のビデオアプリケーションからの保護されたコンテンツの再生が含まれます。 一般的に、ワークフローは各 DRM ソリューションで似ていますが、詳細にはいくつか違いがあります。

この Multi-DRM ワークフローでは、Apple FairPlay で保護された HLS コンテンツの設定、パッケージ化、ライセンス、再生をおこないます。 このワークフローには、オフラインでの再生とライセンスのローテーションを実装するためのオプションの手順も含まれています。

## FairPlay 向け ExpressPlay サービスの有効化 {#enable-expressplay-service-for-fairplay}

Appleの FairPlay DRM ソリューションを ExpressPlay DRM サービスで使用する場合は、いくつかの設定が必要です。 これには、Appleから資格情報を取得し、ExpressPlay にアップロードする必要があります。

FairPlay コンテンツ保護のために ExpressPlay サービスを有効にするには、次の手順に従います。

1. Appleから資格情報を取得します。

   これらの資格情報は、各サービスプロバイダーに一意にプロビジョニングされます。 次のフォームに入力して、リクエストする必要があります。 [https://developer.apple.com/contact/fps/](https://developer.apple.com/contact/fps/).

   >[!NOTE]
   >
   >選択 **[!UICONTROL Content Provider]** プライマリの役割。

   リクエストが承認されると、Appleから *FairPlay ストリーミングデプロイメントパッケージ*.
1. 証明書署名要求を生成します。

   以下を使用できます。 [!DNL openssl] 公開鍵と秘密鍵のペア、および証明書署名済み要求 (CSR) を生成する。

   1. キーペアを生成します。

      ```
      openssl genrsa -aes256 -out privatekey.pem 1024 
      ```

   1. CSR を生成します。

      ```
      openssl req -new -sha1 -key privatekey.pem -out certreq.csr  
        -subj "/CN=SubjectName /OU=OrganizationalUnit /O=Organization /C=US"
      ```

      >[!NOTE]
      >
      >この手順は、 *FairPlay ストリーミングデプロイメントパッケージ*&#x200B;に含めることはできますが、便宜上、ここに含めることができます。 プロセスのこの部分で問題が発生した場合は、 *FairPlayCertificateCreation.pdf* （デプロイメントパッケージ内）。

1. Apple開発者ポータルから CSR をアップロードします。
   1. 開発チームのチームエージェントは、 [!DNL developer.apple.com/account].
   1. クリック： **[!UICONTROL Certificates, Identifiers & Profiles]**&#x200B;を選択し、 **[!UICONTROL iOS, tvOS, watchOS]** ページの左上にあるドロップダウンから、 **[!UICONTROL Certificates->Production]** をクリックします。
   1. 次をクリック： **[!UICONTROL +]** ボタンをクリックして、新しい証明書を要求します。 を選択します。 **[!UICONTROL FairPlay Streaming Certificate]** 下のオプション **[!UICONTROL Production]**.

      The *iOS証明書を追加* ダイアログが開きます。
   1. Adobe Analytics の *iOS証明書を追加*、手順 2.b で生成した CSR ファイルをアップロードし、「 **[!UICONTROL Generate]**.

      同じダイアログにアプリケーション秘密鍵 (ASK) が表示されます。
   1. ASK を書き留め、安全な場所に保存します。
   1. ASK のキーで証明書の生成を完了し、「 **[!UICONTROL Continue]**.
   1. ASK を保存したことを確認したら、 **[!UICONTROL Generate]** をクリックして続行します。

      >[!NOTE]
      >
      >ASK のコピーを保存し、安全に保存することが重要です。 *ASK に問題が生じた場合、FairPlay Streaming でコンテンツを保護できなくなります。* ASK は 1 つだけチームに割り当てられます。 この値は再度指定されず、後で取得することはできません。

   1. FPS 証明書をダウンロードします。

      （手順 2.a.の）秘密鍵と公開鍵（この手順でダウンロードした FPS 証明書）のバックアップコピーを安全な場所に保存してください。
1. FairPlay の資格情報を使用して ExpressPlay アカウントを設定します。
   1. 手順 3.h でダウンロードした証明書の名前が [!DNL fairplay.cer].
   1. を開きます。 [!DNL fairplay.cer] ファイルに、Apple Keychain Access ユーティリティを追加します。
   1. 「 」と入力して、多数の証明書をフィルターします。 `fairplay`」と入力します。
   1. 会社の FairPlay 証明書を特定します。

      会社名は、Appleが発行した証明書に関連付ける必要があります。
   1. 展開矢印を選択して証明書を展開し、秘密鍵を右クリックします。
   1. 選択 **[!UICONTROL Export "Your Company Name"]** をクリックし、 [!DNL .p12] ファイル。

      このファイルを保護するためのパスワードを割り当てるように求められます。 このパスワードは資格情報パッケージと共に送信する必要があるので、メモしておいてください。
   1. 次の日にアカウントにログイン [www.expressplay.com](https://www.expressplay.com).
   1. クリック **[!UICONTROL DRM SERVICES]** 左上で、 **[!UICONTROL FairPlay]** タブをクリックします。
   1. FairPlay の資格情報を ExpressPlay アカウントにアップロードします。

      1. ASK の値を含むテキストファイルを作成します (32 文字にする必要があります。例： `1234567890abcdef1234567890abcdef`) をクリックし、アップロードするファイルを選択します。
      1. 手順 4.f の PKCS12 ファイルをアップロード用に選択します。
      1. 手順 4.f の PKCS12 ファイルのパスワードを入力します。
      1. 「アップロード」ボタンをクリックします。

FairPlay コンテンツ保護機能を備えたiOSアプリケーションやHTML5 ページを、 [!DNL fairplay.cer] FairPlay 用の ExpressPlay サービスを使用する証明書。

<!--<a id="fig_sjr_2pn_sv"></a>-->

![](assets/multi_drm_expressplay_drm_services_web.png)

### FairPlay 用にコンテンツをパッケージ化 {#package-your-content-for-fairplay}

コンテンツをパッケージ化するには、Adobeオフラインパッケージャまたは ExpressPlay の Bento4 パッケージャなどの他のツールを使用できます。

パッケージャーは、再生するビデオを準備し（例えば、元のファイルをフラグメント化してマニフェストに含める）、選択した DRM ソリューション（この場合は FairPlay）でビデオを保護します。

* [FairPlay DRM 用のAdobeオフラインパッケージャ](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf#page=21)
* [ExpressPlay パッケージャー — Bento4 for HLS](https://www.bento4.com/developers/hls/)

<!--<a id="fig_jbn_fw5_xw"></a>-->

![](assets/pkg_lic_play_hls_web.png)

1. コンテンツをパッケージ化します。

   以下に、Offline Packager を使用したAdobeの例を示します。 Packager は設定ファイル ( [!DNL fairplay.xml]) は次のようになります。

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

   * `in_path`  — このエントリは、ローカルパッケージングマシン上のソースビデオの場所を指します。
   * `out_type`  — このエントリは、パッケージ化された出力のタイプを示します。この場合は、FairPlay 用の HLS です。
   * `out_path`  — 出力先のローカルマシン上の場所。
   * `drm_sys`  — パッケージ化する DRM ソリューション。 これは `FAIRPLAY` この場合、
   * `frag_dur`  — フラグメントの時間（秒）。
   * `target_dur` - HLS 出力のターゲット期間。
   * `key_file_path`  — これは、コンテンツ暗号化キー (CEK) として機能する、パッケージ化マシン上のライセンスファイルの場所です。 Base-64 でエンコードされた 16 バイトの 16 進文字列です。
   * `iv_file_path`  — パッケージ化したコンピューター上の IV ファイルの場所です。
   * `key_url`  — の URI パラメーター `EXT-X-KEY` タグ [!DNL .m3u8] ファイル。
   * `content_id`  — デフォルト値。

   次に示すように、 [Packager のドキュメント](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf#page=7)「ベストプラクティスとして、出力の生成に使用する共通オプションを含む設定ファイルを作成します。 次に、特定のオプションをコマンドライン引数として指定して出力を作成します。」

   ```
   java -jar OfflinePackager.jar -in_path sample.mp4 -out_type hls 
   -out_path out_file_path -drm -drm_sys FAIRPLAY -key_file_path "creds/fairplay.bin" 
   -key_url "user_provided_value"
   ```

   生成された M3U8 ファイルには `EXT-X-KEY` 属性は次のように表示されます。

   ```
   #EXT-X-KEY:METHOD=SAMPLE-AES,URI="user_provided_value",​
   KEYFORMAT="com.apple.streamingkeydelivery",KEYFORMATVERSIONS="1" 
   ```

### FairPlay 用のポリシーの設定 {#setting-policies-for-fairplay}

FairPlay で保護されたコンテンツのポリシーは、エンタイトルメントサーバーを使用して設定できます。 独自の設定をおこなうことも、Adobeが提供するサンプルのエンタイトルメントサーバーを使用することもできます。

Adobeには、実行方法を示す ExpressPlay エンタイトルメントサーバー (SEES) のサンプルが用意されています。 *時間ベース* および *device-binding* 使用権限 このサンプルのエンタイトルメントサーバーは、ExpressPlay サービス上に構築されています。

[参照サーバー： ExpressPlay 使用権限サーバーの例 (SEES)](../../multi-drm-workflows/feature-topics/sees-reference-server.md)

* [参照サービス：時間ベースの使用権限](../../multi-drm-workflows/feature-topics/sees-reference-server-time-entitlement.md)
* [参照サービス：デバイスバインディングの使用権限](../../multi-drm-workflows/feature-topics/sees-reference-server-binding-entitlement.md)

## FairPlay のライセンスと再生 {#licensing-and-playback-for-fairplay}

FairPlay で保護されたコンテンツのライセンスと再生には、ビデオマニフェストファイルで使用されるスキーム (skd:) と ExpressPlay トークンリクエストで使用されるスキーム (https:) との間で、URL スキームの入れ替えが必要です。

iOS TVSDK クライアントからのライセンスと再生を実装する手順を以下に示します。 [TVSDK アプリケーションでのApple FairPlay の有効化](../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-apple-fairplay-tvsdk.md). また、FairPlay のオフライン再生とライセンスのローテーションもオプションで実装できます。

## FairPlay での HLS オフライン {#section_047A05D1E3B64883858BC601CFC8F759}

FairPlay で保護されたコンテンツを、Web 上（飛行機上など）から離れているためにライセンスを取得できない場合に、ユーザーが FairPlay で保護されたコンテンツを再生できるようにしたい場合があります。

このタスクを開始する前に、 Appleドキュメントをダウンロードしてお読みください **&quot;FairPlay ストリーミングと HTTP ライブストリーミングを使用したオフライン再生&quot;**. このガイドを読んで、Transport Stream(TS) セグメントをダウンロードし、ローカルマシンに保存する方法を学びます。

次のワークフローで、FairPlay 用のオフライン再生を実装します。

1. HLS TS セグメントをダウンロードします。
1. FairPlay サーバーからの永続的なレンタルライセンスのリクエスト ( **&quot;FairPlay の永続的なレンタルポリシー&quot;**) をクリックします。
1. を保存します。 `persistentContentKey`.
1. FairPlay コンテンツをオフラインで再生します。

>[!NOTE]
>
>永続化されたコンテンツキーの有効期限が切れた場合、クライアント上の FairPlay ストリーミングは復号化を開始しません。 ただし、再生中にコンテンツキーの有効期限が切れた場合、ユーザーエクスペリエンスは継続されます。
>
>詳しくは、 [HTTP ライブストリーミングの操作](https://developer.apple.com/library/content/documentation/AudioVideo/Conceptual/MediaPlaybackGuide/Contents/Resources/en.lproj/HTTPLiveStreaming/HTTPLiveStreaming.html#//apple_ref/doc/uid/TP40016757-CH11-SW3) ドキュメントを参照してください。

### FairPlay ライセンスのローテーション {#section_D32AA08C61474B4F876AC2A5F18CB879}

ライセンスのローテーションは、長時間再生されるコンテンツのライセンスハッキングを防ぐスキームです。

M3U8 マニフェストでは、各キータグは次のキータグまで、またはファイルの最後まで、次の TS セグメントに適用されます。

ライセンスのローテーションを追加するには、次の手順を実行します。

* ライセンスのローテーション時に新しい FairPlay キータグを挿入します。

  任意の数のキータグを追加できます。

  線形コンテンツの場合は、M3U8 ウィンドウで最新のキータグを維持してください。 iOSは、約 2 つの TS セグメントが再生される（約 20 秒）ときに、次の M3U8 をリクエストします。 新しい M3U8 に新しいキータグが含まれている場合、すべてのキーリクエストが直ちに実行されます。 以前の既存のキーは、再度リクエストされません。 iOSは、すべてのキーリクエストが完了するのを待ってから、再生が開始されます。

  ライセンスのローテーションを含む VOD コンテンツの場合、すべてのキーリクエストは再生の開始時に発生します。

  次に、キーの回転を伴う M3U8 の例を示します。

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
