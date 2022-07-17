---
title: Android™向け TVSDK 2.7 リリースノート
description: Android™向け TVSDK 2.7 リリースノートでは、TVSDK Android™ 2.7 の新機能や変更点、解決された既知の問題、およびデバイスの問題について説明します。
products: SG_PRIMETIME
topic-tags: release-notes
exl-id: d64f0ef2-60a9-43a1-b2f9-44764a570538
source-git-commit: 59ea8008c828f3bdf275fea5cc2a59c37b0c4845
workflow-type: tm+mt
source-wordcount: '4037'
ht-degree: 0%

---

# Android™向け TVSDK 2.7 リリースノート {#tvsdk-for-android-release-notes}

Android™向け TVSDK 2.7 リリースノートでは、TVSDK Android™ 2.7 の新機能や変更点、解決された既知の問題、およびデバイスの問題について説明します。

## TVSDK Android™ 2.7 {#tvsdk-android}

Android™リファレンスプレーヤーは、ディストリビューションの samples/ディレクトリに Android™ TVSDK に付属しています。 付属の README&lt;.md ファイルでは、参照プレーヤーの構築方法を説明しています。

>[!NOTE]
>
>リファレンスプレーヤーを正常に構築するには、リリースと共に配布される README.md に記載されているように、必ず次の操作を行ってください。
>
>1. から VideoHeartbeat.jar をダウンロードします。 [https://github.com/Adobe-Marketing-Cloud/media-sdks/releases](https://github.com/Adobe-Marketing-Cloud/media-sdks/releases) (Android™ v2.0.0 用 VideoHeartbeat ライブラリ )
>1. libs/フォルダーに VideoHeartbeat.jar を抽出します。

>


## 新機能 {#new-features}

Android™向け TVSDK 2.7 には、バージョン 1.4 のすべての機能が含まれています。ただし、以下に示すサポート対象外の機能は除きます。 [機能マトリックス](#feature-matrix).

**Android™ TVSDK 2.7**

* **並列広告解決のサポート**

TVSDK 2.7 では、順次解決ではなく、広告の時間内のすべての広告リクエストの同時解決がサポートされます。

### 以前のリリースの新機能 {#new-features-previous-releases}

**バージョン 2.5.6**

* **TVSDK 2.5 は、Android™ P をサポートしています**
* **バックグラウンドオーディオの有効化**

   アプリがフォアグラウンドからバックグラウンドに移動したときにオーディオ再生を有効にするには、プレーヤーが PREPARED 状態のときに、引数として true を使用して MediaPlayer の enableAudioPlaybackInBackground API を呼び出す必要があります。

* **MediaPlayer クラスの alwaysUseAudioOutputLatency(boolean val)**

設定した場合、オーディオタイムスタンプの計算で出力待ち時間を使用します。
ブール型パラメーター val - True は、オーディオタイムスタンプの計算でオーディオ出力待ち時間を使用します。

* **帯域幅の速度が急に低下した場合でも、最高の再生エクスペリエンスを得るために最適化されています。**
TVSDK は、必要に応じて進行中のセグメントのダウンロードをキャンセルし、適切なレンディションに動的に切り替えるようになりました。 これは、中断のないビットレート間をシームレスに切り替えることでおこなわれます。

**バージョン 2.5.5**

* **部分的な広告ブレーク挿入**

   部分的に視聴された広告のトラッキングを実行せずに、広告の途中で参加する TV のようなエクスペリエンス。\
   例：ユーザーは、3 つの 30 秒の広告で構成される 90 秒の広告ブレークの中間（40 秒）に結合します。 ブレークの 2 番目の広告から 10 秒経過します。
   * 2 番目の広告は、残りの期間（20 秒）に続いて 3 番目の広告を再生します。
   * 部分的な広告再生（2 番目の広告）の広告トラッカーは起動されません。 3 番目の広告のトラッカーのみが実行されます。

* **HTTPS を介したセキュアな広告読み込み**

   Adobe Primetimeには、primetime 広告サーバーおよび CRS over https への最初の呼び出しをリクエストするオプションが用意されています。

* **CRS リクエストに AdSystem およびクリエイティブ ID が追加されました**

   * 次を含む： `AdSystem` および `CreativeId` を 1401 リクエストと 1403 リクエストの新しいパラメーターとして追加しました。

* **NetworkConfiguration クラスの API setEncodeUrlForTracking が削除されました** を使用します。

**バージョン 2.5.4**

Android™ TVSDK v2.5.4 では、次の更新と API の変更が提供されています。

* のデフォルト値の変更 `WebViewDebbuging`

   この `WebViewDebbuging` の値は次の値に設定されます。 _False_ デフォルトでは。 有効にするには、 `setWebContentsDebuggingEnabled` から _True_ （アプリケーション内）

* OpenSSL および Curl バージョンのアップグレード更新 `libcurl` を v7.57.0に、OpenSSL を v1.0.2k に変更した場合。
* VAST 応答オブジェクトのアプリレベルアクセス VAST 応答オブジェクトをアプリケーションにアクセスできる新しい API NetworkAdInfo::getVastXml() が導入されました。

**バージョン 2.5.3**

Android™ TVSDK v2.5.3 では、次の更新と API の変更が提供されています。

* CRS を使用する TVSDK のすべてのお客様は、Android™の TVSDK 2.5.3.85（最新）を使用してアプリをアップグレードすることをお勧めします。 これは、既存のアプリケーション実装に対するドロップインの置き換えです。 TVSDK のアップグレード後、プロキシツールで CRS クリエイティブ URL リクエストを確認します ( 例：Charles) を参照し、パス内のホスト名とバージョンが、以下のサンプル URL 構造と同様に反映されていることを確認します。

   `https://primetime-a.akamaihd.net/assets/3p/v3.1/222000/167/d77/167d775d00cbf7fd224b112sf5a4bc7d_0e34cd3ca5177fbc74d66d784 bf3586d.m3u8`

* TVSDK のユーザーエージェントをカスタマイズ可能：ユーザーエージェントをカスタマイズする新しい API が追加されました。

   * `setCustomUserAgent`（文字列値）
   * `getCustomUserAgent`()

* Android™ Application と TVSDK の間で Cookie を共有します。Android™ TVSDK で、(Android™アプリケーションの CookieStore に格納された )Java™レイヤーと C++ TVSDK レイヤーの間の cookie へのアクセスがサポートされるようになりました。 これで、Java™ Cookie ストアに公開される際に、ネイティブの C++層で cookie を設定または変更できるようになりました。
* API の変更点は次のとおりです。

   * 新しいイベント CookiesUpdatedEvent が追加されます。 Cookie が更新されると、メディアプレーヤーによってディスパッチされます。
   * 新しい API が `NetworkConfiguration::set/ getCustomUserAgent()` カスタムユーザーエージェントを使用する場合。
   * 新しい API が `NetworkConfiguration::set/ getEncodedUrlForTracking` 安全でない文字のエンコードを強制的に行う場合。
   * 新しい API が `NetworkConfiguration::getNetworkDownVerificationUrl()` ：フェイルオーバーが発生した場合にネットワーク検証 URL を設定します。
   * キャプションの表示時にスペースを英数字として扱うかどうかを定義する TextFormat::treatSpaceAsAlphaNum に新しいプロパティが追加されました。

* 変更点 `SizeAvailableEvent`:以前は、 `SizeAvailableEvent` 2.5.2 では、フレームの高さとフレーム幅を返します。これはメディア形式で返されます。 現在は、デコーダーから返される出力の高さと出力の幅を返します。
* バッファリング動作の変更：バッファリング動作が変更されました。 バッファが空の場合に何をしたいかに関しては、App 開発者に任せられます。 2.5.3 は、バッファが空の場合に再生バッファのサイズを使用します。

**バージョン 2.5.2**

Android™ TVSDK v2.5.2 では、重要なバグ修正と API の変更がいくつかおこなわれています。

**バージョン 2.5.1**

Android™ 2.5.1 でリリースされた重要な新機能。

* **パフォーマンスの向上**&#x200B;新しい TVSDK 2.5.1 アーキテクチャでは、パフォーマンスがいくつか向上しました。 サードパーティのベンチマーク調査の統計に基づく新しいアーキテクチャでは、起動時間が 5 倍、ドロップフレーム数は業界平均に比べて 3.8 倍も短縮されています。

   * **VOD およびライブの即時オン —** 即時オンを有効にすると、 TVSDK は、再生が開始する前にメディアを初期化し、バッファリングします。 複数の MediaPlayerItemLoader インスタンスをバックグラウンドで同時に起動できるので、複数のストリームをバッファリングできます。 ユーザーがチャネルを変更し、ストリームが適切にバッファリングされると、新しいチャネルでの再生が直ちに開始します。 TVSDK 2.5.1 は、 **live** ストリームも同様です。 ライブストリームは、ライブウィンドウが移動すると再バッファリングされます。

      * **ABR ロジックの改善 —** 新しい ABR ロジックは、バッファ長、バッファ長の変化率、測定された帯域幅に基づいています。 これにより、ABR は帯域幅が変動する際に適切なビットレートを選択し、また、バッファ長の変化率を監視することで、ビットレート切り替えが実際に発生する回数を最適化します。
      * **部分セグメントのダウンロード/サブセグメント化 —** TVSDK は、可能な限り早く再生を開始するために、各フラグメントのサイズをさらに縮小します。 ts フラグメントには、2 秒ごとにキーフレームが必要です。
      * **遅延広告解決 —** TVSDK は、再生を開始する前に、非プリロール広告の解決を待たずに、起動時間を短縮します。 シークやトリック再生などの API は、すべての広告が解決されるまで、引き続き使用できません。 これは、CSAI で使用される VOD ストリームに適用されます。 シークや早送りなどの操作は、広告の解決が完了するまで許可されません。 ライブストリームの場合、この機能は、ライブイベント中の広告の解決に対して有効にすることはできません。
      * **永続的なネットワーク接続 —** この機能を使用すると、 TVSDK は、永続的なネットワーク接続の内部リストを作成して保存できます。 これらの接続は、複数の要求に対して再利用されます。ネットワーク要求ごとに新しい接続を開き、その後破棄する必要はありません。 これにより、効率が向上し、ネットワークコードの待ち時間が短縮され、再生パフォーマンスが向上します。
TVSDK は、接続を開くと、サーバーに *キープアライブ* 接続。 一部のサーバーでは、このタイプの接続がサポートされていない場合があります。その場合、 TVSDK は、リクエストごとに接続を再び確立することにフォールバックします。 また、永続的な接続がデフォルトでオンになっている間、 TVSDK には設定オプションが追加され、アプリで永続的な接続を必要に応じてオフにすることができます。
      * **並列ダウンロード —** ビデオとオーディオをシリーズではなく並行してダウンロードすると、起動時の遅延が軽減されます。 この機能を使用すると、HLS Live ファイルと VOD ファイルの再生、サーバーからの使用可能な帯域幅の使用量の最適化、バッファーの実行中の確率の低下、ダウンロードと再生の間の遅延の最小化が可能です。
      * **並列の広告ダウンロード —** TVSDK は、広告の時間をヒットする前に、コンテンツの再生と並行して広告をプリフェッチするので、広告とコンテンツをシームレスに再生できます。

* **再生**

   * **MP4 コンテンツ再生 —** TVSDK 内で再生するために、MP4 の短いクリップを再変換する必要はありません。
注意：ABR 切り替え、トリック再生、広告挿入、遅延オーディオバインディング、サブセグメント化は、MP4 再生ではサポートされません。
   * **可変ビットレート (ABR) を使用したトリック再生 —** この機能を使用すると、 TVSDK は、トリック再生モード時に iFrame ストリームを切り替えることができます。 iFrame 以外のプロファイルを使用して、低速でトリック再生を実行できます。
   * **よりスムーズなトリック再生 —** 以下の改善により、ユーザーエクスペリエンスが向上します。

          *トリック再生中の適応ビットレートおよびフレームレートの選択（帯域幅とバッファプロファイルに基づく）
          *最大 30 fps の高速再生を実現するには、IDR ストリームの代わりにメインストリームを使用します。
      
* **コンテンツ保護**

   * **解像度ベースの出力保護 —** この機能は、再生の制限を特定の解像度に結び付け、DRM コントロールをより詳細に設定します。

* **ワークフローのサポート**

   * **直接請求の統合 —** これにより、請求指標がAdobe Analyticsバックエンドに送信されます。このバックエンドは、お客様が使用するストリームに関してAdobe Primetimeで認定されています。
TVSDK は、顧客の販売契約に従って自動的に指標を収集し、課金のために必要な定期的な使用状況レポートを生成します。 TVSDK は、すべてのストリーム開始イベントで、Adobe Analytics Data Insertion API を使用して、コンテンツタイプ、広告挿入有効フラグ、drm 有効フラグなどの請求指標を請求可能なストリームの期間に基づいてAdobe Analytics Primetime 所有のレポートスイートに送信します。 これは、お客様独自のAdobe Analyticsレポートスイートやサーバー呼び出しに干渉したり、含まれたりすることはありません。 この請求使用状況レポートは、リクエストに応じて定期的にお客様に送信されます。 これは、使用状況の請求のみをサポートする請求機能の第 1 段階です。 ドキュメントに記載されている API を使用して、販売契約に基づいて設定できます。 この機能は、デフォルトで有効になっています。 この機能をオフにするには、リファレンスプレーヤーのサンプルを参照してください。
   * **フェイルオーバーのサポートの向上 —** ホストサーバー、プレイリストファイル、セグメントに障害が発生した場合でも、再生を中断せずに続行するための追加戦略が実装されました。

* **広告**

   * **Mort 統合 —** Mort からの広告視認性測定のサポート。
   * **コンパニオンバナー —** コンパニオンバナーはリニア広告と一緒に表示され、多くの場合、広告が終了した後もビューに表示され続けます。 これらのバナーのタイプは、html(HTMLスニペット ) または iframe（iframe ページへの URL）です。

* **Analytics**

   * **VHL 2.0 -** これは、Adobe Analyticsの使用状況データを自動収集するための、最新の最適化されたビデオハートビートライブラリ (VHL) 統合です。 API の複雑さが軽減され、実装が簡単になりました。 VHL ライブラリのダウンロード [Android™用 v2.0.0](https://github.com/Adobe-Marketing-Cloud/media-sdks/releases) をクリックし、libs フォルダーに JAR ファイルを抽出します。

* **SizeAvaliableEventListener**
   * SizeAvailableEvent の getHeight() メソッドと getWidth() メソッドは、それぞれ高さと幅で出力を返すようになりました。 表示縦横比は次のように計算できます。

      ```
      SizeAvailableEvent e;
      
      DAR = e.getWidth()/ e.getHeight();
      
      Storage Aspect Ratio in terms of Sar width and Sar height can also be used to calculate Frame width and Frame height:
      
      SAR = e.getSarWidth()/e.getSarHeight();
      
      frameHeight = e.getHeight();
      
      frameWidth = e.getWidth()/SAR;    
      ```

* **Cookie**

   * Android™ TVSDK は、Android™アプリケーションの CookieStore に保存された Java™ Cookie へのアクセスをサポートするようになりました。 新しい Cookie が「Set-Cookie」応答ヘッダーの一部として含まれる場合は常に記録するコールバック API(onCookiesUpdated) が提供されます。 CookieStore を使用して特定の URI/ドメインに対してこれらの cookie の値を設定することで、これらの cookie を別の URI/ドメインで使用する HttpCookie のリストとして使用できます。 同様に、 TVSDK 内の cookie の値は、 CookieStore add API を使用して更新されます。

## 機能マトリックス {#feature-matrix}

Android™向け TVSDK は、ビデオアプリケーションに機能を追加するために実装できる様々な機能をサポートしています。

以下の機能表では、「Y」は、この機能が現在のリリースでサポートされていることを示します。

| 機能 | コンテンツタイプ | HLS |
|---|---|---|
| 一般的な再生（再生、一時停止、シーク） | VOD + Live | Y |
| FER — 一般的な再生（再生、一時停止、シーク） | FER VOD | Y |
| 広告再生中にシーク | VOD + Live | サポートなし |
| AC3 | VOD + Live | サポートなし |
| MP3 | VOD | サポートなし |
| MP4 コンテンツ再生 | VOD | Y |
| 適応ビットレート切り替えロジック | VOD + Live | Y |
| オーディオのみ再生 | VOD + Live | Y |
| マルチ CDN サポート | VOD + Live | サポートなし |
| オーディオ専用メディアを使用した広告の再生 | VOD + Live | サポートなし |
| クローズドキャプション — 608/708 | VOD + Live | Y |
| クローズドキャプション — WebVTT | VOD + Live | Y |
| マニフェストのフェイルオーバー | VOD + Live | Y |
| 高度なフェイルオーバー | VOD + Live | Y |
| QoS とプレーヤーの通知 | VOD + Live | Y |
| cookie ヘッダーのサポート | VOD + Live | Y |
| カスタム HTTP ヘッダーのサポート | VOD + Live | Y（許可リストへの登録が必要） |
| バッファ制御パラメータを設定 | VOD + Live | Y |
| アダプティブビットレートコントロールの設定 | VOD + Live | Y |
| カスタムマニフェストタグ | VOD + Live | Y |
| 遅延オーディオバインディング | VOD + Live | Y |
| 302 リダイレクト | VOD + Live | Y |
| オフセットの再生 | VOD + Live | Y |
| オーディオのみ再生 | VOD + Live | Y |
| トリック再生 | VOD + Live | Y |
| トリック再生でのスローモーション | VOD + Live | サポートなし |
| スムーズなトリック再生（ABR を使用） | VOD + Live | Y |
| ID3 解析 | VOD + Live | Y |
| 広告のブラックアウト | VOD + Live | サポートなし |
| 即時オン | VOD + Live | サポートなし |
| Discontinuity マーカーのサポート | VOD + Live | Y |
| 302 リダイレクトの定着 | VOD + Live | Y |

| 機能 | コンテンツタイプ | HLS |
|---|---|---|
| 一般再生、広告有効 | VOD + Live | Y |
| 広告が有効な FER コンテンツ | VOD | Y |
| デフォルトの広告動作 | VOD + Live | Y |
| VAST 2.0/3.0 | VOD + Live | Y |
| VMAP 1.0 | VOD + Live | Y |
| MP4 広告 | VOD + Live | Y（CRS から） |
| 広告を有効にしたトリック再生 | VOD + Live | Y |
| 広告のみ | VOD | Y |
| ターゲティングパラメーター | VOD + Live | Y |
| カスタムパラメーター | VOD + Live | Y |
| カスタム広告動作 | VOD + Live | Y |
| カスタム広告タグ | ライブ | Y |
| カスタム広告リゾルバー | VOD + Live | Y |
| Freewheel Custom Ad Resolver | VOD | Y |
| C3 | VOD + Live | サポートなし |
| 遅延広告解決 | VOD | Y |
| Discontinuity マーカーのサポート — SSAI | VOD + Live | Y |
| コンパニオン広告、バナー広告、クリック可能な広告 | VOD + Live | Y |
| VPAID 2.0 | VOD + Live | Y(JS) |
| 早期広告出口 | ライブ | Y |
| ルールベースのクリエイティブ優先順位付け | VOD + Live | Y |
| CRS ルール | VOD + Live | Y |
| JSON Ad Resolver | VOD + Live | サポートなし |
| Mort 統合 | VOD + Live | Y |

| 機能 | コンテンツタイプ | HLS |
|---|---|---|
| AES 暗号化 | VOD + Live | Y |
| AES 暗号化の例 | VOD + Live | Y |
| トークン化ストリーム | VOD + Live | Y |
| DRM | VOD + Live | Primetime DRM のみ ( 今後：Widevine) |
| 外部再生 (RBOP) | VOD + Live | Primetime DRM のみ |
| ライセンスのローテーション | VOD + Live | Primetime DRM のみ |
| キーの回転 | VOD + Live | Primetime DRM のみ |

| 機能 | コンテンツタイプ | HLS |
|---|---|---|
| Adobe Analytics VHL 統合 | VOD + Live | Y |
| 請求 | VOD + Live | Y |

## 解決された問題 {#resolved-issues}

解決が報告された問題に関連付けられている場合は、Zendesk 参照が表示されます（例： ZD#xxxxx）。

**Android™ TVSDK 2.7**

この節では、 TVSDK 2.7 のリリースで解決された問題の概要を示します。

* ZD#37166 — 広告が正常に再生された場合でもエラートラッキングコールが実行されます。
* ZD#37134 - VMAP 応答に複数の広告が存在する wrapper(3P) Ad が返される場合、間違った広告 ID が返されます。

**Android™ TVSDK 2.5.6**

* ZD #34992 — クローズドキャプションの言語が空です。
   * TVSDK がメインマニフェストからキャプショントラックの詳細を取得するために#EXT-X-MEDIA:TYPE=CLOSED-CAPTIONS を解析しない問題を修正しました。
* ZD #35078 - Android P の検証。
   * TVSDK 2.5.6 は、最新の Android™ P ベータビルドで検証されました。 新しい Android™ OS により、問題は見つかりませんでした。
* ZD #34149 — エラーが発生した場合でも、プレーヤーは引き続きリクエストのマニフェストを表示します。
   * すべてのプロファイルがダウンした場合（404 エラー）も TVSDK が繰り返し呼び出しをおこなっていた問題を修正しました。
* ZD #31533 — アプリがバックグラウンドに送信された後、Android™でオーディオを再生します。
   * 追加済み `enableAudioPlaybackInBackground` アプリがバックグラウンドになっているときにオーディオの再生を有効にするために、引数として「True」を指定して呼び出す必要がある MediaPlayer の API です（プレーヤーが PREPARED 状態のとき）。

**Android™ TVSDK 2.5.5**

* ZD #21647 — 実際のビデオサイズが 640 x 360 の場合、Android TVSDK は 640 x 368 を通知します。
   * 変数 m_nOutputHeight （AndroidMCVideoDecoder 内）が実際の出力の高さではなくフレームの高さで更新されるので、 m_nOutputHeight を正しく計算するために、関数 getVideoFrame に関連する変更を加えました。
* ZD #26614 — 至急 — サードパーティの広告提供/プログラム — インプレッションを提供できない。
   * 「スペース」が「等しい」記号の前にある場合に問題が再現可能な XML 解析でのケースの処理により、以前の修正を強化しました。 &lt;vast version=&quot;2.0&quot;>
* ZD #29296 - Android:CRS リクエストに AdSystem およびクリエイティブ ID を追加します。
   * 1401 および 1403 リクエストに新しいパラメーターとして「AdSystem」および「CreativeId」を含めるようになりました。
* ZD #33062 - CDATA ノード下の VAST 応答でパイプ文字が発生すると、 TVSDK がクラッシュする
   * NetworkConfiguration クラスの API setEncodeUrlForTracking は、エンコードする URL 内の安全でない文字として削除されました。
* ZD #33063 - CRS ファイル選択ロジックが壊れました。 TVSDK が webm 形式の CRS リクエストを送信せず、代わりに 3gpp ファイル用に送信していました。
   * ロジックを修正しました。 Webm および 3gpp 形式のメディアファイルを使用する場合、CRS リクエストが Webm 用に送信されます。 また、3gpp 形式の両方のメディアファイルを使用する場合、最も高いビットレート 3gpp ファイルに対して送信される CRS リクエストが返されます。
* ZD #33125 - Android アプリが VMAP 内の特定の DoubleClick タグでクラッシュする。
   * クラッシュを回避するためにシナリオを修正しました。
* ZD #32256 — ライセンスのローテーションとキーのローテーションの問題 —Adobeアクセス。
   * SampleAES コンテンツの DRM メタデータを使用してセグメントの初期化を修正しました。 AES128 コンテンツで正常に機能します。
* ZD #33619 — ライブポイント近くのバッファリング状態でスタックした成長中のプレイリストコンテンツの高速転送。
   * トリック再生モードでライブポイントを越える際にケースを処理します。
* ZD #34151 - TimedMetadata オブジェクトが正しくありません。
   * タイムライン内で同じ時刻に属している 2 つの TimedMetadata イベントが、ランダムな順序で表示されていました。 マニフェスト内の元の順序を維持しました。
* ZD #34189 — 広告ブレークの開始をシークする際の問題。
   * この問題は、SSAI 広告が不連続を使用して繋がっている場合に発生しました。 その原因は、このような広告の始まりを目指すときの行動で、キーフレームを検索しても見つからないということです。 この理由は、広告の最小オーディオタイムスタンプが、最小ビデオタイムスタンプの前にあるためです。 したがって、間違った fragmentDump データでキーフレームを検索することになります。 今すぐ修正しました。
* ZD #34528 - FireTV 第 3 世代ドングルで、640x360 以降にアップグレードしないビデオ解像度。
   * 最新のファームウェアアップデートを含むように修正を強化。
* ZD #34793 - TVSDK 2.5.x は、VideoEngine が auditudeSettings が使用可能で、使用されていないと仮定していた場合に、カスタムコンテンツリゾルバーでクラッシュするために使用されていました。
   * Null 共有ポインタ (auditudeSettings) に対する関数呼び出しが原因でクラッシュが発生していました。 VideoEngineTimeline::placeToSourceTimeline() 内に条件付きチェックが追加され、そのオブジェクトに対する何らかの呼び出しをおこなう前に auditudeSettings が使用可能であることを確認できるようになりました。
* ZD #32584 — 内に存在する完全な情報にアクセスできません &lt;extensions> VAST 応答のノード。
   * XML 解析に関する問題を修正し、NetworkAdInfo が &lt;extensions> ノード。
* ZD #35086 — 特定の VMAP 応答がある場合、プレーヤーから完全な拡張データを取得しません。
   * この問題は、属性値内に二重引用符が含まれている拡張 xml の場合、XML 解析が機能しなかったので、拡張 xml に固有でした。 問題を修正しました。

**Android™ TVSDK 2.5.4**

* ZenDesk#33659 - Web ビューリモートデバッグを有効にする再生セッション。
   * WebViewDebugging はデフォルトで False に設定されています。 デバッグを有効にするには、setWebContentsDebuggingEnabled(true) を使用して、アプリケーションから true に設定します。
* ZenDesk#33011 - CRS リクエストに失敗した場合、広告タイムラインは解決されません。
   * 広告に対する CRS リクエストが失敗すると、タイムラインが解決され、残りの広告が再生されます。
* ZenDesk#34528 - FireTV 3 世代ドングルの 640x360 以降では、ビデオの解像度がアップグレードされない。
   * ビデオ解像度は、ビットレートスイッチとして上に切り替わります。
* ZenDesk#33192 - AudioTrack が AudioUpdatedEventListener::onAudioUpdated を介してトラックを取得する場合、AudioTrack に null の名前が付けられます。
   * FireTV Stick のいくつかのシナリオでは、実際のオーディオ更新がない場合に onAudioUpdate イベントが発生していました。 現在は修正されています。

**Android™ TVSDK 2.5.3**

* Zendesk#32216 - TimedMetadata カスタムタグ配信登録が機能していません。
   * 1.4 の戻り文字列では、ID3 データをバイト配列（APIC または汎用データをサポートするため）としてクライアントに返すのに対して、 バイト配列は NULL 終端文字自体を処理しないので、クライアントに特殊文字を表示していた。 この問題は現在修正されています。
* Zendesk#32670 - Player が冗長プレイリストにフェールオーバーしない
   * 現在、正常に動作しており、setNetworkDownVerificationUrl が期待どおりに動作しています。
* Zendesk#32369 — クローズドキャプションは、異なる色のごみ箱やアーティファクトを表示します。
   * 最新のビルドで CC の問題が修正されました
* Zendesk#25590 - Enhance:TVSDK Cookie ストア (C++から Java™)
   * Android™ TVSDK で、(Android™アプリケーションの CookieStore に格納された )Java™レイヤーと C++ TVSDK レイヤーの間の cookie へのアクセスがサポートされるようになりました。
* Zendesk#32252 - TVSDK_Android_2.5.2.12 に PTPLAY-20269の修正がないようです。この問題は修正され、2.5.2 ブランチに統合されました。
* Zendesk#31806 — 応答 xml のタグが空のため、PREPARING Player の Auditude スティックが「準備中」の状態で動かなくなりました。 問題が修正されました。
* Zendesk#31727 - TVSDK 2.5 のクローズドキャプション文字は、ドロップされたり、スペルミスが発生したりします。
   * 問題が修正され、文字をドロップまたはスペルミスすることはありません。
* Zendesk#31485 - 2.5 の DrmManager
   * 新しい DrmManager（コンテキストコンテキスト）を使用した DrmManager の作成で問題が発生しました。 DRMManager を提供する DRMService クラスを実装しました。
* Zendesk#32794- 1080P 解像度ストリームが Android™で再生されない。
   * SizeAvailableEvent が変更されました。 以前は、 `getHeight()` および `getWidth()` 2.5 の SizeAvailableEvent のメソッドは、Frame の高さとフレーム幅を返します。これはメディア形式で返されます。 現在は、デコーダーから返される出力の高さと出力の幅を返します。
* Zendesk #19359Flash Playerは、設定レベルのマニフェスト内の#EXT-X-FAXS-CM属性の位置が原因でクラッシュします。
   * #EXT-X-FAXS-CMタグは、個々のビットレートまたはセグメントがプレイリストに表示される前に、常に最上位のプレイリストに表示される必要があります。

**Android™ TVSDK 2.5.2**

* Zendesk#17305不透明な背景を持つクローズドキャプションのアーティファクト。
TextFormat の setTreatSpaceAsAlphaNum プロパティが公開されます。 既定では、このプロパティは False です。 クライアントでプロパティを True に設定して、ダークスペースの問題を解決します。

* Zendesk#25097 CC ディスプレイには、CC 設定のビジュアルアーティファクトが表示されます。
TextFormat の setTreatSpaceAsAlphaNum プロパティが公開されます。 既定では、このプロパティは False です。 クライアントでプロパティを True に設定して、ダークスペースの問題を解決します。

* Zendesk #31620 TVSDK プレーヤーから出るユーザーエージェント文字列が切り捨てられます。
ユーザーエージェント文字列は、128 文字以下に切り捨てられなくなります。
Adobe Primetimeのバージョン文字列がシステムユーザーエージェントに追加されます。

* Zendesk #30809 SEEK_END イベントが見つからないと、アプリが再生状態に移行しなくなります。
* Zendesk #30415 Closed Caption の「Cyan」の色は、以前の Primetime TVSDK リリースと比較して、より濃い青色（ターコイズ）になりました。

   色が DarkCyan から Cyan に変更されます。

* Zendesk #30727 VOD 広告がダウンロード/解決されていません。

   VMAP XML で、明示的な終了タグ (&#39;&lt;/vast>&#39;) で、その後に改行文字がない場合、VMAP XML は適切に解析されず、広告が再生されない可能性があります。

**Android™ TVSDK 2.5.1**

* デバイス固有 (Samsung Galaxy Tab 4) のクラッシュ。Auditude を使用する VOD DRM LBA で、広告をクリックします。
* VHL — オフセットからコンテンツを開始する際に、誤ったハートビート呼び出しが送信されます。
* VPAID 広告が再生されると、VHL ハートビートはイベントのを呼び出します:type:再生広告が見つかりません。
* プレーヤーは、完了ステータスに移行した後、ポストロール広告の SKIP adBreakPolicy を含む PLAYING ステータスに戻ります。
* 送信広告コールバックに cookie が添付されていません。
* 広告キューポイントが表示されません。
* 別の EAC3 SAP トラックを持つ HLS は読み込まれません。
* メディアプレーヤーが復元された後に TVSDK がスクリーンオンインテントを受け取ると、プレーヤーがクラッシュします。

## 既知の問題と制限事項 {#known-issues-and-limitations}

**Android™ TVSDK 2.7**

* TVSDK 2.7 では、最大 5 つの広告を同時に解決できます。
* VMAP 応答の場合、単一の広告ブレークの Ad 呼び出しは同時に実行され、広告ブレークは順番に解決されます。
* FER の場合、各オポチュニティの Ad 呼び出しは同時に解決されます。

### 以前のリリースの既知の問題と制限事項{#known-issues-limitations-previous-releases}

**Android™ TVSDK 2.5.6**

* 同時に複数の VMAP 広告の時間はサポートされていません。

**Android™ TVSDK 2.5.3**

このバージョンには次の問題があります。

* ライブビデオ再生中に、ローエンドデバイスでのオーディオビデオの同期の問題や、ネットワーク状態の低下が発生する場合があります。
* FER ストリームの場合、virtualTime と localTime は異なる場合があります。 また、オフセット付きの FER は機能しません。
* 遅延バインディングオーディオコンテンツがシークされると、再生が停止する場合があります。
* LIVE コンテンツで、WebVTT キャプションが断続的に同期しなくなる場合があります。
* 断続的に、広告ブレークから出た後に、数個のフレームの高速再生が見られることがあります。
* Ads が再生されている場合でも、Triple Wrapper Ad Breaks に対して 303 エラーがスローされることがあります。

**Android™ TVSDK 2.5.2**

このバージョンには次の問題があります。

* ライブビデオ再生で、ローエンドデバイスでのオーディオビデオ同期の問題が発生する場合があります。
* VOD メディアの終わりまでのシーク時に再生が停止することがあります。
* FER ストリームの場合、virtualTime と localTime は異なる場合があります。 また、オフセット付きの FER は機能しません。

**Android™ TVSDK 2.5.1**

このバージョンの TVSDK には、次の問題があります。

* ライブビデオ再生で、ローエンドデバイスでオーディオビデオの同期の問題が発生する場合があります。
* FER ストリームの場合、virtualTime と localTime は異なる場合があります。 また、オフセット付きの FER は機能しません。
* VMAP XML で、明示的な終了タグ (&lt;/vast>) の後に改行がない場合、VMAP XML は適切に解析されず、広告が再生されない可能性があります。
* VPAID ポストロールはサポートされていません。

## 参考リソース {#helpful-resources}

* [必要システム構成](/help/programming/tvsdk-2.7-for-android/c-psdk-android-2.7-requirements.md)
* [Android™用 TVSDK 2.7 プログラマーガイド](/help/programming/tvsdk-2.7-for-android/overview-prod-audience-guide/c-psdk-android-2.7-overview-prod-audience-guide.md)
* [API リファレンス用 TVSDK Android™ Javadoc](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.7/index.html)
* [TVSDK Android™ C++ API ドキュメント](https://help.adobe.com/en_US/primetime/api/psdk/cpp/namespaces.html)  — 各 Java™クラスには対応する C++クラスがあり、C++ドキュメントには Java™のドキュメントよりも説明的な内容が含まれています。Java™ API の詳細については、C++のドキュメントを参照してください。
* [Android™(Java™) 向け TVSDK 1.4 から 2.5 への移行ガイド](/help/migration-guides/tvsdk-14-25-android.md)
* 画面のオン/オフシナリオの処理については、 `Application_Changes_for_Screen_On_Off.pdf` ファイルがビルドに含まれています。
* 完全なヘルプドキュメントは、 [Adobe Primetimeラーニングとサポート](https://experienceleague.adobe.com/docs/primetime.html) ページ。
