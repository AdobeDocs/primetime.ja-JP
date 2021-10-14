---
title: Android 向け TVSDK 3.14 リリースノート
description: TVSDK 3.14 for Android リリースノートでは、 TVSDK Android 3.14 の新機能と変更点、解決された既知の問題、およびデバイスの問題について説明します。
products: SG_PRIMETIME
topic-tags: release-notes
exl-id: cd2c64ef-dd42-4dc2-805f-eeb64a8a53d9
source-git-commit: 988bcf8cbc0175e15bcc899a6f6954cc31c5e127
workflow-type: tm+mt
source-wordcount: '5480'
ht-degree: 0%

---

# Android 向け TVSDK 3.14 リリースノート {#tvsdk-for-android-release-notes}

TVSDK 3.14 for Android リリースノートでは、 TVSDK Android 3.14 の新機能や変更点、解決された既知の問題、デバイスの問題について説明します。

Android リファレンスプレーヤーは、Android TVSDK と共に、お使いのディストリビューションの samples/ディレクトリに含まれています。 付属の README.md ファイルでは、参照プレーヤーの作成方法を説明しています。

>[!NOTE]
>
>リファレンスプレーヤーを正常に構築するには、リリースと共に配布される README.md に記載されている手順に従い、必ず次の操作を行ってください。
>
>1. [https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/releases](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/releases) から VideoHeartbeat.jar をダウンロードします（Android v2.0.0 用 VideoHeartbeat ライブラリ）。
>1. libs/フォルダーに VideoHeartbeat.jar を抽出します。


Android 向け TVSDK は、以前のバージョンと比べて多くのパフォーマンスを向上させました。 高品質の視聴体験を提供し、マルチ CDN のサポートを除き、バージョン 1.4 のすべての機能を搭載しています。

サポート対象およびサポート対象外の機能の包括的なセットについては、リリースノートの [ 機能マトリックス ](#feature-matrix) の節を参照してください。

## Android TVSDK 3.14

このバージョンでは、VAST 応答の [!UICONTROL ClickTracking]、[!UICONTROL CustomClick] または [!UICONTROL CompanionClickTracking] 要素の [!UICONTROL CDATA] ノードが空の場合にアプリケーションがクラッシュする問題を修正しました。

### 以前のリリースの新機能および機能強化

**Android TVSDK 3.13**

FireTV の第 3 世代ペンダントと Fire TV Cube の第 1 世代と第 2 世代のデバイスを含む FireTV デバイスの ABR スイッチで、Widevine DRM ストリームがフリーズしたり、黒いフレームを表示したりします。

この問題を解決するには、再生を開始する前に、指定した Fire TV デバイスの API `MediaPlayer.flushVideoDecoderOnHeaderChange(true)` を設定します。 デフォルト値は false です。

**Android TVSDK 3.12**

Primetime Reference アプリケーションの gradle バージョンがバージョン 5.6.4 に更新されました。

Android Studio を使用してリファレンスアプリをセットアップして実行するには、`TVSDK_Android_x.x.x.x/samples/PrimetimeReference/src/README.md` にある TVSDK zip で入手できる ReadMe ファイルの手順に従ってください。

現在のリリースで修正された上位のお客様の問題については、[ 解決された問題 ](#resolved-issues) の節で説明しています。

**Android TVSDK 3.11**

* **保護システム固有のヘッダー (PSSH) ボックス取得を許可**  - TVSDK は、現在読み込まれているメディアリソースに関連付けられた保護システム固有のヘッダーボックスを取得できます。新しい API `getPSSH()` が `com.adobe.mediacore.drm.DRMManager` に追加されました。

詳しくは、[Widevine DRM](../programming/tvsdk-3x-android-prog/android-3x-content-security/android-3x-drm-widevine.md) を参照してください。

**Android TVSDK 3.10**

このリリースでは、[ 解決された問題 ](#resolved-issues) の節で説明した、お客様の問題の修正に重点を置いています。

**Android TVSDK 3.9**

* **HTTPS を介したセキュア配信**  - Android TVSDK 3.9 では、比類のないスケールとパフォーマンスで安全にコンテンツを配信するために、HTTPS を介したセキュア配信機能が導入されました。

   HTTPS 経由での安全な配信を可能にするために、`NetworkConfiguration` クラスで新しい API が導入されました。

   `public void setForceHTTPS (boolean value)`

   `public boolean getIsForceHTTPS()`

**Android TVSDK 3.8**

* **部分的な広告ブレーク機能を備えたプリロールのサポート**  — この機能強化により、 TVSDK 3.8 は部分的な広告ブレーク機能 (PABI) を備えたプリロール広告をサポートします。

プリロール広告がある場合は、それを再生し、ライブポイントからコンテンツを再生して、ライブテレビのエクスペリエンスをエミュレートします。

**Android TVSDK 3.7**

* Widevine テストコンテンツの場合、DRMManager クラスの新しい API `setMediaDrmCallback` が公開され、MediaDrmCallback インターフェイスのデフォルト実装を上書きします。

   `public static void setMediaDrmCallback(MediaDrmCallback callback)`

* C++レイヤー（Android 64 ビット）で `MediaPlayerEvent.ITEM_UPDATED` を処理しない AppCrash エラーを修正しました。

**Android TVSDK 3.6**

* **64 ビット要件に合わせてアプリを強化**  — ネイティブライブラリがアップグレードさ `(libAVEAndroid.so)` れ、2 つのバージョンで利用できるようになりました。既存の armeabi（32 ビット）ネイティブライブラリの場所が `/framework/Player to /framework/Player/armeabi` から変更され、追加の arm64-v8a（64 ビット）ライブラリが `/framework/Player/arm64-v8a.` に導入されました。

**バージョン 3.5**

* **Just In Time Ad Resolution**  - TVSDK 3.5 は、再生された広告のサポートをタイムラインから削除します。

* **オフライン再生のサポート**  — オフライン再生を使用すると、ユーザーはデバイスにビデオコンテンツをダウンロードして、接続されていないときにビデオコンテンツを視聴できるようになりました。詳しくは、「[Android でのオフライン再生 ](https://helpx.adobe.com/content/dam/help/en/primetime/programming-guides/psdk_android_3.5.pdf)」を参照してください。

**バージョン 3.4**

* TVSDK は、CBC の暗号化されたプレーンストリームの CMAF ストリーム再生をサポートするようになりました。

**バージョン 3.3**

* **API の変更点**

   * ネットワークエラーとタイムアウトを処理する新しい API が `NetworkConfiguration::setNumOfTimesManifestRetryBeforeError(n)*` に追加されました。
      * (n) は再試行の回数です。

**バージョン 3.2**

* **並列広告の解決とマニフェストのダウンロードのサポート**

   * TVSDK 3.2 では、VMAP を除くすべての広告リクエストと広告の時間に対する順次解決の代わりに、同時解決をサポートしています。

   * 広告ブレーク内のすべての広告マニフェストが同時にダウンロードされます。

* **広告の解決とマニフェストのダウンロードタイムアウトのサポートを有効にしました。**

   * ユーザーは、広告の解決全体とマニフェストのダウンロードのタイムアウト値を設定できるようになりました。  VMAP の場合、すべての広告の時間が連続して解決されるので、個々の広告の時間にタイムアウト値が適用されます。

* **AdvertisingMetadata クラスに新しい API が導入されました。**

   * `void setAdResolutionTimeout(int adResolutionTimeout)`

   * `int getAdResolutionTimeout()`

   * `void setAdManifestTimeout(int adManifestTimeout)`

   * `int getAdManifestTimeout()`

* **AdvertisingMetadata クラスから以下の API を削除しました。**

   * `void setAdRequestTimeout(int adRequestTimeout)`

   * `int getAdRequestTimeout()`

* **AC3/EAC3 オーディオコーデックを使用したストリームの再生を有効にしました**

   * `void alwaysUseAC3OnSupportedDevices(boolean val)` 授業 `MediaPlayer` 中

* **TVSDK は、暗号化された Widevine CTR の CMAF およびプレーンストリーム再生をサポートしています。**

* **4K HEVC ストリームの再生がサポートされるようになりました。**

* **並列広告呼び出しリクエスト**  - TVSDK は、20 件の広告呼び出しリクエストを並行してプリフェッチするようになりました。

**バージョン 3.0**

* **TVSDK 3.0 は、高効率ビデオコーディング (HEVC) ストリームをサポートしています。**

* **Just in Time — 広告マーカーに近い広告の解決遅延広告解**
決は、各広告ブレークを個別に解決するようになりました。以前は、広告解決は 2 段階のアプローチでした。再生開始前にプリロールが解決され、再生開始後にすべてのミッド/ポストロールスロットが組み合わされました。 この強化機能を使用すると、各広告ブレークは、広告キューポイントの前の特定の時間に解決されるようになります。

>[!NOTE]
>
>遅延広告解決は、デフォルトでオフになるように変更され、明示的に有効にする必要があります。

この広告メタデータに関連付けられた遅延広告読み込みの許容値を取得するため、新しい API が `AdvertisingMetadata::setDelayAdLoadingTolerance` に追加されました。\
PREPARATION の直後にシークが可能になり、広告の時間をシークすると、シークが完了する直前に解決されます。\
シグナリングモード `SERVER_MAP` と `MANIFEST_CUES` がサポートされます。

詳しくは、API とイベントの変更に関する [TVSDK 3.0 for Android プログラマーガイド ](../programming/tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/c-lazy-ad-resolving/c-lazy-ad-resolving.md) を参照してください。

* **最新バ `targetSdkVersion` ージョンに更新**

`targetSdkVersion` を 19 から 27 に更新し、スムーズに機能するようにしました。

* **Placement.Type getPlacementType() は、インターフェイス TimelineMarker のメソッドになりました。**

   このメソッドは、Placement.Type.PRE_ROLL、Placement.Type.MID_ROLL または Placement.Type.POST_ROLL の配置タイプを返します。 広告の時間が未解決の場合、 TimelineMarker インターフェイスの getDuration() メソッドは 0 を返します。

**バージョン 2.5.6。**

* **TVSDK 2.5 は、Android P をサポートします。**

* **バックグラウンドオーディオの有効化**

   アプリがフォアグラウンドからバックグラウンドに移動したときにオーディオ再生を有効にするには、アプリは、プレーヤーが PREPARED 状態のときに引数として true を指定して MediaPlayer の `enableAudioPlaybackInBackground` API を呼び出す必要があります。

* **MediaPlayer クラスの alwaysUseAudioOutputLatency(boolean val)**

設定した場合、オーディオタイムスタンプの計算で出力待ち時間を使用します。
ブール型パラメーター val - True を指定すると、オーディオのタイムスタンプの計算にオーディオ出力待ち時間が使用されます。

* **帯域幅の速度が急に低下した場合でも、最高の再生エクスペリエンスを得るために最適化されています。**

TVSDK は、必要に応じて進行中のセグメントのダウンロードをキャンセルし、適切なレンディションに動的に切り替えるようになりました。 これは、途切れることなく、ビットレート間をシームレスに切り替えることでおこなわれます。

**バージョン 2.5.5**

* **部分的な広告ブレーク挿入**

   部分的に視聴された広告のトラッキングを実行せずに、広告の途中で参加する TV のようなエクスペリエンス。\
   例：ユーザーは、3 つの 30 秒の広告で構成される 90 秒の広告ブレークの途中（40 秒）に参加します。 ブレークの 2 番目の広告から 10 秒後です。

   * 2 番目の広告は、残りの期間（20 秒）に続いて 3 番目の広告を再生します。

   * 部分的に再生された広告（2 番目の広告）の広告トラッカーは実行されません。 3 番目の広告のみのトラッカーが実行されます。

* **HTTPS を介した広告の読み込みの保護**

   Adobe Primetimeには、Primetime 広告サーバーおよび CRS over https への最初の呼び出しをリクエストするオプションが用意されています。

* **CRS リクエストに追加された AdSystem およびクリエイティブ ID**

   1401 および 1403 リクエストに新しいパラメーターとして `AdSystem` と `CreativeId` を含めるようになりました。

* **URL 内の安全でない文字として削除さ** れた NetworkConfiguration クラスの API setEncodeUrlForTracking は、エンコードする必要があります。

**バージョン 2.5.4**

Android TVSDK v2.5.4 では、次の更新および API の変更が提供されています。

* `WebViewDebbuging` のデフォルト値の変更

   `WebViewDebbuging` の値はデフォルトで `Fals`e に設定されています。有効にするには、アプリケーションで `setWebContentsDebuggingEnabled(true)` を呼び出します。

* **OpenSSL および Curl バージョンのアップグレード**

   libcurl を v7.57.0に、OpenSSL を v1.0.2k に更新しました。

* VAST 応答オブジェクトのアプリレベルアクセス

   VAST 応答オブジェクトへのアクセスを提供する新しい API `NetworkAdInfo::getVastXml()` が導入されました。

**バージョン 2.5.3**

Android TVSDK v2.5.3 では、次の更新と API の変更がおこなわれました。

* CRS を使用する TVSDK のすべてのお客様は、Android の TVSDK 2.5.3.85 以降を使用してアプリをアップグレードすることをお勧めします。 これは、既存のアプリの実装に代わるドロップインです。 TVSDK のアップグレード後、プロキシツールで CRS クリエイティブ URL リクエストを確認します ( 例：Charles を参照 ) を確認し、パスのホスト名とバージョンが、以下のサンプル URL 構造と同様に反映されていることを確認します。

   `https://primetime-a.akamaihd.net/assets/3p/v3.1/222000/167/d77/167d775d00cbf7fd224b112sf5a4bc7d_0e34cd3ca5177fbc74d66d784 bf3586d.m3u8`

* TVSDK のユーザーエージェントのカスタマイズ可能：ユーザーエージェントをカスタマイズする新しい API が追加されました。

   * `setCustomUserAgent(String value)`
   * `getCustomUserAgent()`

* Android アプリケーションと TVSDK との間で Cookie を共有：Android TVSDK で、（Android アプリケーションの CookieStore に格納された）JAVA レイヤーと C++ TVSDK レイヤーの間の cookie へのアクセスをサポートするようになりました。 これで、Java Cookie Store に公開されるネイティブ C++層の Cookie を設定または変更できます。

* API の変更点：

   * 新しいイベント `CookiesUpdatedEvent` が追加されます。 Cookie が更新されると、メディアプレーヤーによってディスパッチされます。

   * カスタムユーザーエージェントを使用する新しい API が `NetworkConfiguration::set/ getCustomUserAgent()` に追加されました。

   * `NetworkConfiguration::set/ getEncodedUrlForTracking` に新しい API が追加され、安全でない文字のエンコードが強制されます。

   * フェイルオーバー時にネットワーク検証 URL を設定する新しい API が `NetworkConfiguration::getNetworkDownVerificationUrl()` に追加されました。

   * キャプションの表示中にスペースを英数字として扱うかどうかを定義する新しいプロパティが `TextFormat::treatSpaceAsAlphaNum` に追加されます。

* `SizeAvailableEvent` の変更。 以前は、2.5.2 の `getHeight()` および `getWidth()` メソッドは、フレームの高さとフレームの幅を返すのに使用されていましたが、これはメディア形式で返されました。 `SizeAvailableEvent`現在は、デコーダーから返される出力の高さと出力の幅を返します。

* バッファリング動作の変更：バッファリング動作が変更されました。 バッファが空の場合に何をしたいかについては、App 開発者に任せてあります。 2.5.3 はバッファが空の場合に再生バッファサイズを使用します。

**バージョン 2.5.2**

Android TVSDK v2.5.2 では、重要なバグ修正と API の変更がいくつかおこなわれています。

**バージョン 2.5.1**

Android 2.5.1 でリリースされた重要な新機能。

* **パフォーマンスの向上 —** 新しい TVSDK 2.5.1 アーキテクチャにより、多くのパフォーマンスが向上しました。サードパーティのベンチマーク調査の統計に基づき、新しいアーキテクチャでは、起動時間が 5 倍に短縮され、ドロップフレーム数は業界平均に比べて 3.8 倍少なくなります。

* **VOD およびライブの即時オン —** 即時オンを有効にすると、TVSDK は、再生が開始する前にメディアを初期化し、バッファリングします。複数の MediaPlayerItemLoader インスタンスをバックグラウンドで同時に起動できるので、複数のストリームをバッファーできます。 ユーザーがチャネルを変更し、ストリームが正しくバッファリングされると、新しいチャネルでの再生が直ちに開始されます。 TVSDK 2.5.1 では、**ライブ** ストリームのインスタントオンもサポートしています。 ライブウィンドウが移動すると、ライブストリームは再バッファリングされます。

* **ABR ロジックの改善 —** 新しい ABR ロジックは、バッファー長、バッファー長の変化率、測定された帯域幅に基づいています。これにより、帯域幅が変動する際に ABR が適切なビットレートを選択し、バッファ長の変化の速度を監視することで、ビットレート切り替えが実際に発生する回数を最適化します。

* **部分的なセグメントのダウンロード/サブセグメント化 —**  TVSDK は、可能な限り早く再生を開始するために、各フラグメントのサイズをさらに小さくします。ts フラグメントには、2 秒ごとにキーフレームが必要です。

* **遅延広告解決 —**  TVSDK は、再生を開始する前に、非プリロール広告の解決を待たずに、起動時間を短縮します。シークやトリック再生などの API は、すべての広告が解決されるまで、まだ使用できません。 これは、CSAI で使用される VOD ストリームに適用されます。 シークや早送りなどの操作は、広告の解決が完了するまで許可されません。 ライブストリームの場合、この機能は、ライブイベント中の広告の解決に対して有効にすることはできません。

* **永続的なネットワーク接続 —** この機能を使用すると、TVSDK は永続的なネットワーク接続の内部リストを作成して保存できます。これらの接続は、複数の要求に対して再利用されます。各ネットワーク要求に対して新しい接続を開き、その後破棄する必要はありません。 これにより、効率が向上し、ネットワークコードの待ち時間が短縮され、再生パフォーマンスが向上します。
TVSDK が接続を開くと、サーバーに *キープアライブ* 接続を要求します。 一部のサーバーでは、このタイプの接続をサポートしていない場合があります。その場合、 TVSDK は、リクエストごとに接続を再び確立します。 また、永続的な接続はデフォルトでオンになりますが、 TVSDK には設定オプションが追加され、アプリで永続的な接続を必要に応じてオフにできます。

* **並列ダウンロード —** ビデオとオーディオを連続ではなく並行してダウンロードすると、起動時の遅延が軽減されます。この機能を使用すると、HLS Live ファイルと VOD ファイルの再生、サーバーからの使用可能な帯域幅の使用量の最適化、バッファーの実行中の状況に至る確率の低下、ダウンロードと再生の間の遅延の最小化を実現できます。

* **並列の広告ダウンロード —**  TVSDK は、広告の時間をヒットする前に、コンテンツの再生と並行して広告をプリフェッチし、広告とコンテンツのシームレスな再生を可能にします。

* **再生**

* **MP4 コンテンツの再生 —** TVSDK 内で再生するために、MP4 の短いクリップを再トランスコードする必要はありません。

   >[!NOTE]
   >
   >ABR 切り替え、トリック再生、広告挿入、遅延オーディオバインディング、サブセグメント化は、MP4 再生ではサポートされません。

* **可変ビットレート (ABR) を使用したトリック再生 —** この機能を使用すると、TVSDK はトリック再生モード中に iFrame ストリームを切り替えることができます。iFrame 以外のプロファイルを使用して、低速でトリック再生を実行できます。

* **よりスムーズなトリック再生 —** 以下の改善により、ユーザーエクスペリエンスが向上します。

   * 帯域幅とバッファプロファイルに基づく、トリック再生中の可変ビットレートおよびフレームレートの選択

   * 最大 30 fps の高速再生を実現するには、IDR ストリームの代わりにメインストリームを使用します。

* **コンテンツ保護**

   * **解像度ベースの出力保護 —** この機能は、再生制限を特定の解像度に結び付け、よりきめ細かな DRM コントロールを提供します。

* **ワークフローのサポート**

   * **直接請求の統合 —** 請求指標をAdobe Analyticsバックエンドに送信します。バックエンドは、Adobe Primetimeによって顧客が使用するストリームに関して認定されています。

   TVSDK は、顧客販売契約に従って指標を自動的に収集し、課金のために必要な定期的な使用状況レポートを生成します。 TVSDK は、すべてのストリーム開始イベントで、Adobe Analytics Data Insertion API を使用して、請求可能なストリームの期間に基づくコンテンツタイプ、広告挿入有効フラグ、drm 有効フラグなどの請求指標をAdobe Analytics Primetime 所有のレポートスイートに送信します。 これは、お客様独自のAdobe Analyticsレポートスイートやサーバー呼び出しに影響したり、含まれたりすることはありません。 請求に応じて、この請求使用状況レポートは定期的にお客様に送信されます。 これは、使用状況の請求のみをサポートする請求機能の第 1 段階です。 ドキュメントに記載されている API を使用して、販売契約に基づいて設定できます。 この機能はデフォルトで有効になっています。 この機能をオフにするには、リファレンスプレーヤーのサンプルを参照してください。

   * **フェイルオーバーのサポートの向上 —** ホストサーバー、プレイリストファイル、セグメントに障害が発生した場合でも、中断のない再生を継続するための追加の戦略を実装しました。


* **広告**

   * **Morti の統合 —** Morth からの広告視認性測定のサポート。

   * **コンパニオンバナー —** コンパニオンバナーはリニア広告と一緒に表示され、多くの場合、広告が終了しても引き続きビューに表示されます。これらのバナーは、html(HTMLスニペット ) タイプまたは iframe（iframe ページの URL）タイプのバナーです。

* **Analytics**

   * **VHL 2.0 -** Adobe Analyticsの使用状況データを自動収集するための、最新の最適化されたビデオハートビートライブラリ (VHL) 統合です。API の複雑さが軽減され、実装が簡単になりました。 Android 用の VHL ライブラリ [v2.0.0 をダウンロードし、libs フォルダーに JAR ファイルを抽出します。](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/releases)

* **SizeAvaliableEventListener**

   * `getHeight()` とのメ `getWidth()` ソッド `SizeAvailableEvent` は、出力を高さと幅でそれぞれ返すようになりました。表示縦横比は次のように計算できます。

      ```java
      SizeAvailableEvent e;
      DAR = e.getWidth()/ e.getHeight();
      ```

      Sar の幅と Sar の高さに関するストレージの縦横比は、フレームの幅とフレームの高さの計算にも使用できます。

      ```java
      SAR = e.getSarWidth()/e.getSarHeight();
      frameHeight = e.getHeight();
      frameWidth = e.getWidth()/SAR;
      ```

* **Cookie**

   * Android TVSDK は、Android アプリケーションの CookieStore に保存された JAVA Cookie へのアクセスをサポートするようになりました。 新しい Cookie が **Set-Cookie** 応答ヘッダーの一部として含まれるたびに記録するコールバック API(onCookiesUpdated) が提供されます。 CookieStore を使用して特定の URI/ドメインに対してこれらの Cookie 値を設定することで、これらの Cookie を別の URI/ドメインで使用する HttpCookie のリストとして利用できます。 同様に、 TVSDK の cookie 値は、CookieStore add API を使用して更新されます。

## 機能マトリックス {#feature-matrix}

Android 向け TVSDK は、ビデオアプリケーションに機能を追加するために実装できる多数の機能をサポートしています。

以下の表の「Y」は、この機能が現在のリリースでサポートされていることを示します。

| 機能 | コンテンツタイプ | HLS |
|---|---|---|
| 一般的な再生（再生、一時停止、シーク） | VOD + Live | Y |
| FER — 一般的な再生（再生、一時停止、シーク） | FER VOD | Y |
| 広告再生中のシーク | VOD + Live | サポートなし |
| HEVC 再生 | VOD + Live | fMP4 コンテナのみ |
| AC3 および EAC3 | VOD + Live | サポートなし |
| MP3 | VOD | サポートなし |
| MP4 コンテンツ再生 | VOD | Y |
| 可変ビットレート切り替えロジック | VOD + Live | Y |
| オーディオのみの再生 | VOD + Live | Y |
| マルチ CDN のサポート | VOD + Live | サポートなし |
| オーディオのみのメディアを含む広告の再生 | VOD + Live | サポートなし |
| クローズドキャプション — 608/708 | VOD + Live | Y |
| クローズドキャプション — WebVTT | VOD + Live | Y |
| マニフェストフェールオーバー | VOD + Live | Y |
| 高度なフェイルオーバー | VOD + Live | Y |
| QoS とプレーヤーの通知 | VOD + Live | Y |
| cookie ヘッダーのサポート | VOD + Live | Y |
| カスタム HTTP ヘッダーのサポート | VOD + Live | Y（許可リストへの登録が必要） |
| バッファ制御パラメータの設定 | VOD + Live | Y |
| 可変ビットレートコントロールの設定 | VOD + Live | Y |
| カスタムマニフェストタグ | VOD + Live | Y |
| 遅延オーディオバインディング | VOD + Live | Y |
| 302 リダイレクト | VOD + Live | Y |
| オフセットを含む再生 | VOD + Live | Y |
| トリック再生 | VOD + Live | Y |
| トリック再生でのスローモーション | VOD + Live | サポートなし |
| スムーズなトリック再生（ABR 使用） | VOD + Live | Y |
| ID3 解析 | VOD + Live | Y |
| 広告のブラックアウト | VOD + Live | サポートなし |
| 即時オン | VOD + Live | サポートなし |
| 不連続マーカのサポート | VOD + Live | Y |
| 302 リダイレクトの定着率 | VOD + Live | Y |

| 機能 | コンテンツタイプ | HLS |
|---|---|---|
| 一般的な再生、広告有効 | VOD + Live | Y |
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
| Freewheel カスタム広告リゾルバー | VOD | Y |
| C3 | VOD + Live | サポートなし |
| 遅延広告解決 | VOD | Y |
| 不連続マーカーのサポート — SSAI | VOD + Live | Y |
| コンパニオン広告、バナー広告、クリック可能広告 | VOD + Live | Y |
| VPAID 2.0 | VOD + Live | Y(JS) |
| 早期広告終了 | ライブ | Y |
| ルールベースのクリエイティブの優先順位付け | VOD + Live | Y |
| CRS ルール | VOD + Live | Y |
| JSON 広告リゾルバー | VOD + Live | サポートなし |
| Mort 統合 | VOD + Live | Y |
| 部分的な広告ブレーク挿入 | ライブ | Y |

| 機能 | コンテンツタイプ | HLS |
|---|---|---|
| AES 暗号化 | VOD + Live | Y |
| AES 暗号化の例 | VOD + Live | Y |
| トークン化されたストリーム | VOD + Live | Y |
| Widevine DRM | VOD + Live | fMP4 コンテナのみ |
| Primetime DRM | VOD + Live | Y |
| 外部再生 (RBOP) | VOD + Live | Primetime DRM のみ |
| ライセンスローテーション | VOD + Live | Primetime DRM のみ |
| キーの回転 | VOD + Live | Primetime DRM のみ |

| 機能 | コンテンツタイプ | HLS |
|---|---|---|
| Adobe Analytics VHL 統合 | VOD + Live | Y |
| 請求 | VOD + Live | Y |

## 解決された問題 {#resolved-issues}

解決が報告された問題に関連付けられている場合は、Zendesk 参照が表示されます（例：ZD#xxxxxx）。



**Android TVSDK 3.14**

この節では、 TVSDK 3.14 Android リリースで解決された問題の概要を示します。

* ZD#46903 - [!UICONTROL VAST] 応答の [!UICONTROL ClickTracking]、[!UICONTROL CustomClick] または [!UICONTROL CompanionClickTracking] 要素の [!UICONTROL CDATA] ノードが空の場合にアプリケーションがクラッシュします。

### 以前のリリースの問題を解決しました

**Android TVSDK 3.12**

* ZD#40584 - Primetime リファレンスアプリは最新の gradle バージョンでビルドされません。

**Android TVSDK 3.11**

* ZD#41252 - WebVTT の韓国語文字が Android 7.1 以降で破損しています。

**Android TVSDK 3.10**

* ZD#40340 — すべての TS(TypeScript) ファイルをブロックリストに登録した後に再生を試みると、アプリケーションが「App Not Responding」エラーでクラッシュする。

**Android TVSDK 3.8**

* 新しい問題は追加されませんでした。

**Android TVSDK 3.7**

* 新しい問題は追加されませんでした。

**Android TVSDK 3.6**

* 新しい問題は追加されませんでした。

**バージョン 3.5**

* ZD#37503 - CRS ルールの JSON 応答は、重複する要求を避けるためにキャッシュされます。

**バージョン 3.4**

* ZD#37996 — リニアストリームと VOD CMAF HEVC ストリームで再生が途切れる問題を修正しました。
* ZD#37706 — 文字化けしたキャプションに関する問題を修正しました。
* ZD#37622 — 特定の広告での致命的な URISyntaxErrors の問題を修正しました。
* ZD#36938 — ビットレートを中間のビットレートに切り替えてから、トリック再生を終了した後で最も高いビットレートに切り替える問題を修正しました。

**バージョン 3.3**

* ZD#37394 - CMAF アセットの早送りにより、速度が変わった後にアーティファクトが発生します。
   * トリック再生中にプロファイルの変更で発生する問題を修正しました。
* ZD#37396 — 一部のミッドロールおよびポストロールで広告トラッキングイベントが見つかりません。
   * 広告トラッキングイベントに関する特定のケースを修正しました。
* ZD#37491 — エラーメタを含む HTTP ステータスコードが存在しません。
   * スタック内のネットワークエラーの伝播を行いました。
* ZD#37808 — 新しいカスタム許可リスト。
   * SSAI_TAG のサポートがこの修正の一部として追加されました。
* ZD#37622 — 特定の広告ポッドからの URISyntax エラー。
   * エンコードされていない%を含む顧客 Android アプリが提供されると、ストリーム再生がクラッシュする問題を修正しました
* ZD#37631 - Android TVSDK のマスターマニフェストの再試行メカニズム。
   * この機能強化を処理するために、ネットワーク設定に新しい API を追加しました。 この API を使用しない場合、マニフェストは再試行されません。 使用すると、マニフェストはネットワークエラーとタイムアウトの処理を再試行します。

**バージョン 3.2**

* ZD#37493 — ライブ再生用のビーコンの追跡が、シーケンス内の最初の広告に対して断続的に実行されません。
* ZD#36985- VMAP 応答の空の広告ブレークに対してトラッキングビーコンが送信されません。
* ZD#37134 - TVSDK が VMAP 応答に対して間違った ID を断続的にスローする。

**バージョン 3.0**

* ZD#33740 - TVSDK は、 MediaPlayer オブジェクトを作成し、 replaceCurrentResource() を呼び出した直後に不要な警告をスローします

   * プレーヤーが休止状態の場合にのみ復元を呼び出すことで、以前の修正を改善しました。

* ZD#36442 — 新しい再生のたびにリモートデバッグセッションが切断され、デバッグができなくなります。

   * デフォルトではデバッグが有効になっていないので、Web ビューではデフォルトでデバッグはできません。 必要に応じて、 MediaPlayer.getCustomAdView() から返されたオブジェクトに対して setWebContentsDebuggingEnabled(true) を呼び出すことで、デバッグを有効にする必要があります。

* ZD#33688 — ジャストインタイムのサポートと解決

   * 広告の時間は、広告の時間の位置より前に、指定した間隔で解決されます。

* ZD#36441 — ライブ期間が 5 分を超えて長くなり続け、複数の問題が発生しています。

   * 仮想ライブポイントの計算中に virtualStartTime が 2 回追加され、この問題が発生していた問題を修正しました。

**Android TVSDK 2.5.6**

* ZD #34992 — クローズドキャプションの言語が空です。

   * TVSDK がメインマニフェストからキャプショントラックの詳細を取得するために#EXT-X-MEDIA:TYPE=CLOSED-CAPTIONS を解析しない問題を修正しました。

* ZD #35078 - Android P の検証。

   * TVSDK 2.5.6 は、最新の Android P ベータビルドで検証されました。 新しい Android OS が原因で問題は見つかりません。

* ZD #34149 — エラーが発生しても、プレーヤーが引き続きリクエストをマニフェストに含めます。

   * すべてのプロファイルがダウンした場合（404 エラー）も TVSDK が繰り返し呼び出しをおこなっていた問題を修正しました。

* ZD #31533 — アプリがバックグラウンドに送信された後、Android でオーディオを再生します。

   * アプリがバックグラウンドになっているときにオーディオを再生できるように、引数として「True」を指定して（プレーヤーが PREPARED 状態の場合）呼び出す必要がある MediaPlayer の `enableAudioPlaybackInBackground` API を追加しました。

**Android TVSDK 2.5.5**

* ZD #21647 — 実際のビデオサイズが 640 x 360 の場合、Android TVSDK が 640 x 368 を通知します。

   * 変数 m_nOutputHeight （AndroidMCVideoDecoder 内）が、実際の出力高さではなくフレーム高で更新されるためです。 m_nOutputHeight を正しく計算するために、関数 getVideoFrame に関連する変更を加えました。

* ZD #26614 — 緊急 — サードパーティの広告提供/プログラム — インプレッションを提供できない。

   * 以前の修正を強化し、&lt;VAST version =&quot;2.0&quot;> のように、「スペース」が「等しい」記号の前にある場合に問題が再現可能な XML 解析のケースを処理しました。

* ZD #29296 - Android:CRS リクエストに AdSystem およびクリエイティブ ID を追加します。

   * 1401 および 1403 リクエストに新しいパラメーターとして「AdSystem」および「CreativeId」が含まれるようになりました。

* ZD #33062 - CDATA ノード下の VAST 応答でパイプ文字が発生すると TVSDK がクラッシュする

   * NetworkConfiguration クラスの API setEncodeUrlForTracking が、エンコードする URL 内の安全でない文字として削除されました

* ZD #33063 - CRS ファイル選択ロジックが壊れていました — TVSDK は、Web 形式の CRS リクエストを送信せず、代わりに 3gpp ファイルに対して CRS リクエストを送信していました。

   * ロジックを修正しました。 Webm および 3gpp 形式のメディアファイルを使用する場合、CRS リクエストを Web に送信します。 また、3gpp 形式の両方のメディアファイルを使用すると、最も高いビットレート 3gpp ファイルに対して CRS リクエストが送信されます。

* ZD #33125 - VMAP 内の特定の DoubleClick タグで Android アプリがクラッシュする。

   * クラッシュを回避するために、シナリオを修正しました。

* ZD #32256 — ライセンスのローテーションとキーのローテーションの問題 —Adobeアクセス

   * SampleAES コンテンツの DRM メタデータを使用したセグメントの初期化を修正しました。 AES128 コンテンツで正常に機能します。

* ZD #33619 — ライブポイント近くでバッファリング状態でスタックした拡大中のプレイリストコンテンツの高速転送。

   * トリック再生モードでライブポイントを越える場合にケースを処理

* ZD #34151 - TimedMetadata オブジェクトが正しくありません。

   * 2 つの TimedMetadata イベントが、タイムラインで同じ時間に属していた場合、ランダムな順序で表示されていました。 マニフェストの元の順序を維持。

* ZD #34189 — 広告ブレークの開始をシークする際の問題。

   * この問題は、SSAI 広告が不連続を使用して繋ぎ合わされていた問題でした。 その原因は、このような広告の始まりを探すときの行動で、キーフレームを検索し、見つかりません。 この理由は、広告の最小オーディオタイムスタンプが最小ビデオタイムスタンプより前にあるためです。 したがって、間違った fragmentDump データでキーフレームを検索することになります。 修正されました。

* ZD #34528 - FireTV 3 G ドングルの 640 x 360 以上にアップグレードしないビデオ解像度。

   * 最新のファームウェアアップデートを含む修正を強化

* ZD #34793 - VideoEngine で auditudeSettings が使用可能で、使用されていないと仮定していた場合に、カスタムコンテンツリゾルバーでクラッシュするために使用された TVSDK 2.5.x。

   * Null 共有ポインタ (auditudeSettings) に対する関数呼び出しが原因で、クラッシュが発生していました。 VideoEngineTimeline::placeToSourceTimeline() 内に条件付きチェックを追加し、そのオブジェクトに対して何かを呼び出す前に auditudeSettings が使用可能であることを確認しました。

* ZD #32584 - VAST 応答の &lt;Extensions> ノードに存在する完全な情報にアクセスできません。

   * XML 解析に関する問題を修正し、現在は NetworkAdInfo が &lt;Extensions> ノードに存在する完全な情報を提供する

* ZD #35086 — 特定の VMAP 応答の場合、プレーヤーから完全な拡張データを取得しません。

   * この問題は、属性値内に二重引用符が含まれている拡張 XML の解析が機能しなかったので、拡張 XML に固有でした。 問題を修正しました。

**Android TVSDK 2.5.4**

* ZenDesk#33659 - Web ビューのリモートデバッグを有効にする再生セッション。

WebViewDebbugging は、デフォルトで False に設定されています。 デバッグを有効にするには、setWebContentsDebuggingEnabled(true) を使用して、アプリケーションを介して true に設定します。

* ZenDesk#33011 - CRS リクエストが失敗した場合、広告タイムラインは解決されません。

   広告に対する CRS リクエストが失敗すると、タイムラインが解決され、残りの広告が再生されます。

* ZenDesk#34528 - FireTV の第 3 世代ドングルで、ビデオ解像度が 640x360 を超えてアップグレードされない。

   ビデオ解像度は、ビットレートスイッチとして切り替わります。

* ZenDesk#33192 - AudioUpdatedEventListener::onAudioUpdated を介してトラックを取得すると、AudioTrack の名前が NULL になります。

   FireTV Stick のシナリオでは、実際のオーディオアップデートがない場合に onAudioUpdate イベントが発生していました。 現在は修正されています。

**Android TVSDK 2.5.3**

* Zendesk#32216 - TimedMetadata カスタムタグサブスクリプションが機能していません。

   1.4 の戻り文字列では、（APIC または汎用データをサポートするために）バイト配列として ID3 データを返しますが、 バイト配列は、NULL 終端文字自体を処理しないので、クライアントに特殊文字を表示していました。 この問題は修正されました。
* Zendesk#32670 — プレーヤーが冗長プレイリストにフェイルオーバーしない

   現在、正常に動作し、setNetworkDownVerificationUrl が期待どおりに動作しています。
* Zendesk#32369 — クローズドキャプションは、異なる色のごみやアーティファクトを表示します。

   最新のビルドで CC の問題が修正されました
* Zendesk#25590 — 拡張機能：TVSDK Cookie ストア ( C++から JAVA へ )

   Android TVSDK で、（Android アプリケーションの CookieStore に格納された）JAVA レイヤーと C++ TVSDK レイヤーの間の cookie へのアクセスをサポートするようになりました。
* Zendesk#32252 - TVSDK_Android_2.5.2.12 には PTPLAY-20269の修正がないようです

   この問題は修正され、2.5.2 ブランチに統合されました。
* Zendesk#31806 - PREPARING での Auditude スティック

   応答 xml に空のタグが含まれていたので、プレーヤーが準備状態で停止していました。 問題が修正されました。
* Zendesk#31727 - TVSDK 2.5 のクローズドキャプション文字がドロップまたはスペルミスの対象となる。

   問題が修正され、文字のスペルを誤って削除したりすることはありません。
* Zendesk#31485 - DrmManager 2.5

   新しい DrmManager(Context context) を使用した DrmManager の作成で問題が発生しました。 DRMManager を提供する DRMService クラスを実装しました。
* Zendesk#32794- 1080P 解像度のストリームが Android で再生されない

   SizeAvailableEvent と、以前は、2.5 の SizeAvailableEvent の getHeight() および getWidth() メソッドを変更し、Frame の高さとフレームの幅を返しました。これはメディア形式で返されます。 デコーダーが返す出力の高さと出力の幅を返すようになりました。
* Zendesk #19359Flash Playerは、設定レベルのマニフェスト内の#EXT-X-FAXS-CM属性の位置が原因でクラッシュします。

   #EXT-X-FAXS-CMタグは、個々のビットレートまたはセグメントがプレイリストに表示される前に、常に最上位のプレイリストに表示される必要があります。

**Android TVSDK 2.5.2**

* Zendesk#17305背景が不透明でないクローズドキャプションのアーティファクト。

   TextFormat の setTreatSpaceAsAlphaNum プロパティが公開されます。 デフォルトでは、このプロパティは False です。 クライアントでプロパティを True に設定して、ダークスペースの問題を解決します。

* Zendesk#25097 CC ディスプレイには、CC 設定のビジュアルアーティファクトが表示されます。

   TextFormat の setTreatSpaceAsAlphaNum プロパティが公開されます。 デフォルトでは、このプロパティは False です。 クライアントでプロパティを True に設定して、ダークスペースの問題を解決します。

* Zendesk #31620 TVSDK Player から出るユーザーエージェント文字列が切り捨てられます。

   ユーザーエージェント文字列は、128 文字以下で切り捨てられなくなります。

   Adobe Primetimeのバージョン文字列がシステムユーザーエージェントに追加されます。

* Zendesk #30809 Missing SEEK_END イベントは、アプリが再生状態に移行するのを防ぎます。
* Zendesk #30415 Closed Caption の「Cyan」の色は、以前の Primetime TVSDK リリースと比較して、より濃い色合いの青（ターコイズ）になりました。

   色が DarkCyan から Cyan に変更されます。

* Zendesk #30727 VOD 広告がダウンロード/解決されていません。

   VMAP XML で、明示的な終了タグ (&#39;&lt;/VAST>&#39;) を持たず、その後に改行文字を持たない空の VAST タグがある場合、VMAP XML は正しく解析されず、広告が再生されない可能性があります。

**Android TVSDK 2.5.1**

* デバイス固有 (Samsung Galaxy Tab 4) のクラッシュ；Auditude を含む VOD DRM LBA を開き、広告をクリックします。
* VHL — オフセットからコンテンツを開始する際に、誤ったハートビート呼び出しが送信されます。
* VPAID 広告が再生されると、event:type:play 広告の VHL ハートビート呼び出しが見つかりません。
* プレーヤーは、完了ステータスに移行した後、ポストロール広告の SKIP adBreakPolicy を含む PLAYING ステータスに戻ります。
* Cookie が送信広告コールバックに添付されていません。
* 広告キューポイントが表示されません。
* EAC3 SAP トラックが別々にある HLS が読み込まれません。
* メディアプレーヤーの復元後に TVSDK がスクリーンオンインテントを受け取ると、プレーヤーがクラッシュします。

## 既知の問題と制限事項 {#known-issues-and-limitations}

**Android TVSDK 3.11**

* 新しい制限は追加されません。

### 以前のリリースの既知の問題と制限事項

**Android TVSDK 3.10**

* 新しい制限は追加されません。

**Android TVSDK 3.8**

* 新しい制限は追加されません。

**Android TVSDK 3.7**

* 新しい制限は追加されません。

**Android TVSDK 3.6**

* 新しい制限は追加されません。

**Android TVSDK 3.5**

* 新しい制限は追加されませんでした。

**Android TVSDK 3.4**

* ID3、クローズドキャプション、遅延バインディングオーディオのサポートは、CMAF(CBC) ストリームに対して検証されていません。
* 一部のデバイスでは、CMAF ストリームでのトリック再生中にビデオの歪みが上部に現れることが原因で、再現性の低い問題が発生します。

**Android TVSDK 3.3**

* clcp:c608 キャプションは、CMAF ストリーム再生ではサポートされていません。

**Android TVSDK 3.2**

* TVSDK 3.2 は、CMAF サンプル AES および AES128 ストリームの再生をサポートしていません。
* HEVC CMAF ストリームには、クローズドキャプション再生のサポートは含まれていません。
* 非暗号化セグメントの周りでシークが実行されると、WV 暗号化ストリームに緑色の色が表示されます。
* CMAF ストリームは ID3 イベントをサポートしません。
* HLS ストリームは、TTML キャプション形式をサポートしていません。

**Android TVSDK 3.0**

* HEVC のサポートには、このリリースで次の制限があります

   * DRM はサポートされていません
   * CC(CEA 608/708) のサポートが検証されていない
   * 4K サポートはまだ存在しません
   * ID3 タグのサポートが検証されていない

* 広告の進行状況イベントの場合、タイムラインバーに広告の再生時間 100%が反映されないことがあります。 回避策として、`adcompleteevent` を使用して広告の再生完了を知り、タイムラインバーの更新、広告関連の UI の削除など、様々な目的で UI を更新できます。
* VMAP から返された Vast 広告呼び出しは、ジャストインタイムのルックアヘッド位置を受け入れません。

**Android TVSDK 2.5.6**

* 複数の VMAP 広告の時間が同時にサポートされません。

**Android TVSDK 2.5.3**

このバージョンには次の問題があります。

* ライブビデオ再生で、ローエンドデバイスでのオーディオビデオの同期の問題や、ネットワーク状態の低下が発生する場合があります。
* FER ストリームの場合、virtualTime と localTime は異なる場合があります。 また、オフセット付きの FER は機能しません。
* 遅延バインディングオーディオコンテンツがシークされると、再生が停止する場合があります。
* LIVE コンテンツで、WebVTT キャプションが断続的に同期しなくなる場合があります。
* 広告の時間から出た後、数フレームの高速再生が断続的に見られる場合があります。
* Ads が再生されている場合でも、Tripple Wrapper 広告の時間に 303 エラーが発生することがあります。

**Android TVSDK 2.5.2**

このバージョンには次の問題があります。

* ライブビデオ再生で、ローエンドデバイスでのオーディオビデオの同期の問題が発生する場合があります。
* VOD メディアの終わりまでシークすると、再生が停止する場合があります。
* FER ストリームの場合、virtualTime と localTime は異なる場合があります。 また、オフセット付き FER は機能しません。

**Android TVSDK 2.5.1**

このバージョンの TVSDK には、次の問題があります。

* ライブビデオ再生で、ローエンドデバイスでのオーディオビデオの同期の問題が発生する場合があります。
* FER ストリームの場合、virtualTime と localTime は異なる場合があります。 また、オフセット付き FER は機能しません。
* VMAP XML で、明示的な終了タグ (&lt;/VAST>) のない空の VAST タグがあり、その後に改行がない場合、VMAP XML は正しく解析されず、広告が再生されない可能性があります。
* VPAID ポストロールはサポートされていません。

## 参考リソース {#helpful-resources}

* [必要システム構成](https://docs.adobe.com/content/help/en/primetime/programming/tvsdk-3x-android-prog/introduction/android-3x-requirements.html)
* [Android 向け TVSDK 3.10 プログラマーガイド](https://docs.adobe.com/content/help/en/primetime/programming/tvsdk-3x-android-prog/introduction/android-3x-overview-prod-audience-guide.html)
* [API 用 TVSDK Android Javadoc リファレンス](https://help.adobe.com/en_US/primetime/api/psdk/javadoc3.5/index.html)
* [TVSDK Android C++ API ドキュメント](https://help.adobe.com/en_US/primetime/api/psdk/cpp_3.5/namespaces.html)  — 各 Java クラスには対応する C++クラスがあり、C++ドキュメントには Javadoc よりも詳細な説明が含まれています。Java API の詳細については、C++のドキュメントを参照してください。
* [TVSDK 1.4 から 2.5 for Android(Java) への移行ガイド](https://helpx.adobe.com/primetime/migration-guides/tvsdk-14-25-android.html)
* 画面のオン/オフのシナリオの処理については、ビルドに含まれている `Application_Changes_for_Screen_On_Off.pdf` ファイルを参照してください。
* [Adobe Primetimeのラーニングとサポート ](https://helpx.adobe.com/support/primetime.html) ページで、完全なヘルプドキュメントを参照してください。
