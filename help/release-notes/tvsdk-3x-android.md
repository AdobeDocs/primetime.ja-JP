---
title: TVSDK 3.11 for Androidリリースノート
seo-title: TVSDK 3.11 for Androidリリースノート
description: TVSDK 3.11 for Androidリリースノートでは、TVSDK Android 3.11の新機能や変更点、解決済みで既知の問題、デバイスの問題について説明します。
seo-description: TVSDK 3.11 for Androidリリースノートでは、TVSDK Android 3.11の新機能や変更点、解決済みで既知の問題、デバイスの問題について説明します。
uuid: 685d46f5-5a02-4741-af5c-91e91babd6f7
products: SG_PRIMETIME
topic-tags: release-notes
discoiquuid: 3a27379f-3cef-4ea3-bcae-21382dc1e9fd
translation-type: tm+mt
source-git-commit: dbb4aceaea1f3db2fcc5a2aa2168ee8a1cd4c785

---


# TVSDK 3.11 for Androidリリースノート {#tvsdk-for-android-release-notes}

TVSDK 3.11 for Androidリリースノートでは、TVSDK Android 3.11の新機能や変更点、解決済みで既知の問題、およびデバイスの問題について説明します。

Androidリファレンスプレイヤーは、配布物のsamples/ディレクトリにAndroid TVSDKに含まれています。 付属のREADME.mdファイルでは、リファレンスプレーヤーの構築方法が説明されています。

>[!NOTE]
>
>リファレンスプレーヤーを正常に構築するには、リリースと共に配布されているREADME.mdで説明されているように、次の手順を実行します。
>
>1. https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/releasesからVideoHeartbeat.jar [をダウンロード](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/releases) （Android v2.0.0用のVideoHeartbeatライブラリ）
>1. VideoHeartbeat.jarをlibs/フォルダーに抽出します。
>



Android向けTVSDKは、以前のバージョンと比べて多くのパフォーマンスが向上しました。 マルチCDNのサポートを除き、高品質な表示エクスペリエンスを提供し、バージョン1.4のすべての機能を搭載しています。

サポートされる機能とサポートされない機能の包括的なセットは、リリースノ [ートの「機能のマトリ](#feature-matrix) ックス」セクションに表示されます。

## Android TVSDK 3.11

**保護システム固有ヘッダー(PSSH)ボックスのフェッチが許可されました**

TVSDKで、現在読み込まれているメディアリソースに関連付けられた保護システム固有のヘッダーボックスを取得できるようになりました。 に新しいAPI `getPSSH()` が追加されまし `com.adobe.mediacore.drm.DRMManager`た。
詳しくは、Widevine DRMを参照し [てください](../programming/tvsdk-3x-android-prog/android-3x-content-security/android-3x-drm-widevine.md)。

現在のリリースで修正されたトップのお客様の問題は、「解決された問題」セクシ [ョンで説明し](#resolved-issues) ます。

### 以前のリリースの新機能と機能強化

**Android TVSDK 3.10**

このリリースでは、「解決された問題」の節で説明した、お客様の主な問題の修 [正に焦点を当て](#resolved-issues) ました。

**Android TVSDK 3.9**

* **HTTPS経由のセキュア配信** - Android TVSDK 3.9では、HTTPS経由のセキュア配信機能が導入され、比類のない規模とパフォーマンスでコンテンツを安全に配信できます。

   HTTPS経由の安全な配信を有効にするため、新しいAPIがクラスに導入さ `NetworkConfiguration` れました。

   `public void setForceHTTPS (boolean value)`

   `public boolean getIsForceHTTPS()`

**Android TVSDK 3.8**

* **部分的な広告ブレーク機能を使用したプリロールのサポート** — この機能強化により、TVSDK 3.8は、部分的な広告ブレーク機能(PABI)を使用したプリロール広告をサポートします。

   プリロール広告がある場合は、再生され、ライブポイントからコンテンツが再生され、ライブテレビのエクスペリエンスがエミュレートされます。

**Android TVSDK 3.7**

* Widevineテストコンテンツの場合、DRMManagerクラスの新しいAPIが公 `setMediaDrmCallback` 開され、MediaDrmCallbackインターフェイスのデフォルト実装を上書きします。

   `public static void setMediaDrmCallback(MediaDrmCallback callback)`

* C++レイヤー（Android 64ビット） `MediaPlayerEvent.ITEM_UPDATED` で処理されなかったAppCrashエラーを修正しました。

**Android TVSDK 3.6**

* **64ビット要件のためのアプリの強化** — ネイティブライブラリがアップグレードさ `(libAVEAndroid.so)` れ、2つのバージョンで使用できるようになりました。 既存のArmeabi(32 bit)ネイティブライブラリの場所がから変更され、 `/framework/Player to /framework/Player/armeabi` 追加のarm64-v8a(64 bit)ライブラリが `/framework/Player/arm64-v8a.`

**バージョン3.5**

* **Just In Time Ad Resolution** - TVSDK 3.5は、再生された広告のサポートをタイムラインから削除します。
* **オフライン再生のサポートを有効にしました** — オフライン再生を使用すると、ビデオコンテンツをデバイスにダウンロードし、接続されていないときに視聴できるようになりました。 詳しくは、「Androidでのオフライン再[生」を参照してください](https://helpx.adobe.com/content/dam/help/en/primetime/programming-guides/psdk_android_3.5.pdf)。

**バージョン3.4**

* TVSDKは、CBCで暗号化されたプレーンストリームのCMAFストリーム再生をサポートするようになりました。

**バージョン3.3**

* **APIの変更**

   * ネットワークエラーとタイムアウトを処理す `NetworkConfiguration::setNumOfTimesManifestRetryBeforeError(n)*` るための新しいAPIが追加されました。
      * (n)は再試行数

**バージョン3.2**

* **並行広告解決とマニフェストのダウンロードのサポート**

   * TVSDK 3.2は、VMAPを除くすべての広告リクエストと広告の時間に対する順次解決の代わりに、同時解決をサポートしています。

   * 広告の時間内のすべての広告マニフェストが同時にダウンロードされます。

* **広告の解決とマニフェストのダウンロードタイムアウトのサポートを有効にしました。**

   * 広告の全体的な解像度とマニフェストのダウンロードのタイムアウト値を設定できるようになりました。  VMAPの場合、すべての広告の時間が連続して解決されるので、タイムアウト値は個々の広告の時間に適用されます。

* **AdvertisingMetadataクラスに新しいAPIが導入されました。**

   * `void setAdResolutionTimeout(int adResolutionTimeout)`

   * `int getAdResolutionTimeout()`

   * `void setAdManifestTimeout(int adManifestTimeout)`

   * `int getAdManifestTimeout()`

* **以下のAPIがAdvertisingMetadataクラスから削除されました。**

   * `void setAdRequestTimeout(int adRequestTimeout)`

   * `int getAdRequestTimeout()`

* **AC3/EAC3オーディオコーデックを使用したストリームの再生の有効化**

   * `void alwaysUseAC3OnSupportedDevices(boolean val)` 授業中 `MediaPlayer` に

* **TVSDKは、暗号化されたWidevine CTRのCMAFおよびプレーンストリーム再生をサポートしています。**

* **4K HEVCストリームの再生がサポートされるようになりました。**

* **並行広告呼び出し要求** - TVSDKは、20個の広告呼び出し要求を並行してプリフェッチするようになりました。

**バージョン3.0**

* **TVSDK 3.0は、High Efficiency Video Coding(HEVC)ストリームをサポートします。**

* **ジャストインタイム — 広告マーカーに近い広告を解決する遅延**&#x200B;広告解決は、各広告の時間を個別に解決するようになりました。 以前は、広告の解決は2段階のアプローチでした。再生開始後に組み合わされた、再生開始およびすべてのミッド/ポストロールスロットの前に、プリロールが解決されました。 この機能が強化され、各広告の時間が広告キューポイントの前の特定の時間に解決されるようになりました。

> [!NOTE]
>
> 遅延広告解決がデフォルトでオフになるように変更され、明示的に有効にする必要があります。

この広告メタデータに関連付けられ `AdvertisingMetadata::setDelayAdLoadingTolerance` た遅延広告読み込みの許容値を取得するための新しいAPIが追加されました。\
PREPARATIONの直後にシークが許可されるようになりました。広告の時間をシークすると、シークが完了する前に即座に解決されます。\
シグナリングモード `SERVER_MAP` とがサポ `MANIFEST_CUES` ートされています。

詳しくは、 [TVSDK 3.0 for Android Programmer&#39;s Guide](../programming/tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/c-lazy-ad-resolving/c-lazy-ad-resolving.md) on APIとイベントの変更を参照してください。

* **最新バージ`targetSdkVersion`ョンに更新しました**

スムーズな `targetSdkVersion` 機能を実現するために、19から27に更新されました。

* **Placement.Type getPlacementType()は、インターフェイスのTimelineMarkerのメソッドになりました**

   このメソッドは、配置タイプがPlacement.Type.PRE_ROLL、Placement.Type.MID_ROLLまたはPlacement.Type.POST_ROLLであることを返します。 広告の時間が未解決の場合、TimelineMarkerインターフェイスのgetDuration()メソッドは0を返します。

**バージョン2.5.6。**

* **TVSDK 2.5は、Android P.**

* **バックグラウンドオーディオの有効化**

   アプリが前景から背景に移動したときのオーディオ再生を有効にするには、プレイヤーがPREPARED状態のときに、引数がtrueのMediaPlayerの `enableAudioPlaybackInBackground` APIを呼び出す必要があります。

* **alwaysUseAudioOutputLatency(boolean val) in MediaPlayerクラス**

設定する場合、オーディオタイムスタンプの計算に出力待ち時間を使用します。
Booleanパラメーターval - Trueを指定すると、オーディオの出力待ち時間がオーディオタイムスタンプの計算に使用されます。

* **帯域幅の速度が急速に低下した場合でも、最高の再生エクスペリエンスを得るために最適化されました。**

TVSDKは、必要に応じて、進行中のセグメントのダウンロードをキャンセルし、適切なレンディションに動的に切り替えるようになりました。 これは、割り込みなくビットレートをシームレスに切り替えることで行われます。

**バージョン2.5.5**

* **部分的な広告ブレークの挿入**

   部分的に視聴された広告の追跡を実行せずに、広告の途中で参加するテレビのようなエクスペリエンス。\
   例：3つの30秒の広告で構成される90秒の広告の時間の途中（40秒）にユーザーが参加します。 時間の2番目の広告から10秒後。

   * 2番目の広告が残りの時間（20秒）再生され、次に3番目の広告が再生されます。

   * 部分的な広告再生（2番目の広告）の広告トラッカーは実行されません。 3つ目の広告のトラッカーのみが起動されます。

* **HTTPS経由のセキュアな広告読み込み**

   Adobe Primetimeには、Primetime広告サーバーとCRSへの最初の呼び出しをhttps経由でリクエストするオプションが用意されています。

* **CRSリクエストに追加されたAdSystemおよびCreative ID**

   1401および1403 `AdSystem` のリクエ `CreativeId` ストにおよびを新しいパラメーターとして含めるようになりました。

* **URL内の安全でない文字はエンコードされる必要があるので** 、NetworkConfigurationクラスのAPI setEncodeUrlForTrackingは削除されました。

**バージョン2.5.4**

Android TVSDK v2.5.4では、次の更新とAPIの変更がオファーされました。

* デフォルト値の変更 `WebViewDebbuging`

   `WebViewDebbuging` の値はデフォルトで `Fals`eに設定されます。 これを有効にするには、アプリケーシ `setWebContentsDebuggingEnabled(true)` ョンを呼び出します。

* **OpenSSLおよびCurlバージョンのアップグレード**

   libcurlをv7.57.0に、OpenSSLをv1.0.2kに更新しました。

* VAST応答オブジェクトのアプリレベルのアクセス

   VAST応答オブジェクトのア `NetworkAdInfo::getVastXml()` クセスをアプリケーションに提供する新しいAPIが導入されました。

**バージョン2.5.3**

Android TVSDK v2.5.3では、次の更新とAPIの変更がオファーされています。

* CRSを使用するすべてのTVSDKユーザーは、Android上のTVSDK 2.5.3.85または最新のバージョンを使用して、アプリをアップグレードすることをお勧めします。 これは、既存のアプリの実装に代わるドロップインです。 TVSDKのアップグレード後、プロキシツールでCRSクリエイティブURLリクエストを確認します(例：Charles)を参照し、パス内のホスト名とバージョンが、以下のサンプルURL構造と同じように反映されていることを確認します。

   `https://primetime-a.akamaihd.net/assets/3p/v3.1/222000/167/d77/167d775d00cbf7fd224b112sf5a4bc7d_0e34cd3ca5177fbc74d66d784 bf3586d.m3u8`

* TVSDKのユーザーエージェントのカスタマイズ可能：ユーザーエージェントをカスタマイズする新しいAPIが追加されました。

   * `setCustomUserAgent(String value)`
   * `getCustomUserAgent()`

* AndroidアプリケーションとTVSDK間でCookieを共有する：Android TVSDKは、（AndroidアプリケーションのCookieStoreに保存される）JAVAレイヤーとC++ TVSDKレイヤーの間のcookieへのアクセスをサポートするようになりました。 これで、ネイティブC++層のcookieがJava Cookie Storeに公開されるので、cookieの設定や変更が可能になりました。

* APIの変更：

   * 新しいイベント `CookiesUpdatedEvent` が追加されます。 Cookieが更新されると、メディアプレイヤーによってディスパッチされます。

   * カスタムユーザーエージェントを使用す `NetworkConfiguration::set/ getCustomUserAgent()` るための新しいAPIが追加されました。

   * 安全でない文字を強制的にエンコ `NetworkConfiguration::set/ getEncodedUrlForTracking` ードするための新しいAPIが追加されました。

   * フェイルオーバー時にネットワーク `NetworkConfiguration::getNetworkDownVerificationUrl()` 検証URLを設定するための新しいAPIが追加されました。

   * キャプションの表示時にスペースを英数字と `TextFormat::treatSpaceAsAlphaNum` して処理するかどうかを定義する新しいプロパティが追加されました。

* の変更 `SizeAvailableEvent`。 以前は、2. `getHeight()` 5.2 `getWidth()` のメソッドは、フ `SizeAvailableEvent` レームの高さとフレームの幅を返すために使用されていましたが、これはメディア形式で返されていました。 現在は、デコーダーが返す出力の高さと出力の幅がそれぞれ返されます。

* バッファリング動作の変更：バッファリング動作が変更されました。 バッファーが空の場合の処理をアプリの開発者に任せます。 2.5.3は、バッファが空の場合に再生バッファサイズを使用します。

**バージョン2.5.2**

Android TVSDK v2.5.2のオファーに関する重要なバグ修正とAPIの変更点です。

**バージョン2.5.1**

Android 2.5.1でリリースされた重要な新機能。

* **パフォーマンスの向上** — 新しいTVSDK 2.5.1アーキテクチャにより、パフォーマンスが多数改善されました。 サードパーティのベンチマーク調査の統計に基づき、新しいアーキテクチャは、業界平均に比べて起動時間を5分の1に短縮し、ドロップフレーム数を3.8分の1に削減します。

* **VODとライブの即時オン — 即時オンを有効にすると** 、TVSDKは再生開始の前にメディアを初期化し、バッファリングします。 複数のMediaPlayerItemLoaderインスタンスをバックグラウンドで同時に起動できるので、複数のストリームをバッファーできます。 ユーザーがチャネルを変更し、ストリームが正しくバッファリングされた場合、新しいチャネル開始で直ちに再生されます。 TVSDK 2.5.1は、ライブストリームのインスタントオンもサ **ポート** します。 ライブストリームは、ライブウィンドウの移動時に再バッファリングされます。

* **ABRロジックの強化** — 新しいABRロジックは、バッファー長、バッファー長の変化率、測定された帯域幅に基づいています。 これにより、ABRは帯域幅が変動する場合に適切なビットレートを選択し、バッファー長が変化するレートを監視することで、ビットレート切り替えが実際に発生する回数を最適化します。

* **部分的なセグメントのダウンロード/サブセグメント化** - TVSDKは、可能な限り早く開始を再生するために、各フラグメントのサイズをさらに縮小します。 tsフラグメントには、2秒ごとにキーフレームが必要です。

* **遅延広告の解決 —** TVSDKは、再生を開始する前に、非プリロール広告の解決を待たずに、起動時間を短縮します。 シークやトリック再生などのAPIは、すべての広告が解決されるまで使用できません。 これは、CSAIで使用されるVODストリームに適用されます。 シークや早送りなどの操作は、広告の解決が完了するまで許可されません。 ライブストリームの場合、この機能はライブストリーム中は広告の解決に対して有効にできません。イベント

* **永続的なネットワーク接続 —** TVSDKは、永続的なネットワーク接続の内部リストを作成し、保存できます。 これらの接続は、各ネットワーク要求の新しい接続を開き、その後破棄するのではなく、複数の要求に対して再利用されます。 これにより、ネットワークコードの効率が向上し、遅延が減少し、再生パフォーマンスが向上します。
TVSDKは、接続を開くと、キープアライブ接続をサー *バーに要求します* 。 一部のサーバーでは、この種類の接続がサポートされていない場合があります。サポートされていない場合、TVSDKは、再度要求ごとに接続を確立します。 また、永続的な接続はデフォルトでオンになりますが、TVSDKには、アプリが必要に応じて永続的な接続をオフにできるように、設定オプションが追加されました。

* **並列ダウンロード** — ビデオとオーディオを連続ではなく並行してダウンロードすると、起動の遅延が減少します。 この機能を使用すると、HLS LiveファイルとVODファイルの再生、サーバーからの使用可能な帯域幅の使用最適化、バッファーの実行不足状況に陥る確率の低下、ダウンロードと再生の間の遅延を最小限に抑えることができます。

* **並行広告ダウンロード —** TVSDKは、広告の時間をヒットする前に、コンテンツの再生と並行して広告をプリフェッチするので、広告とコンテンツのシームレスな再生を可能にします。

* **再生**

* **MP4コンテンツ再生 —** MP4短いクリップは、TVSDK内で再生するために再トランスコードする必要はありません。

   > [!NOTE]
   >
   > ABRの切り替え、トリック再生、広告挿入、遅延オーディオバインディング、サブセグメント化は、MP4再生ではサポートされていません。

* **可変ビットレート(ABR)を使用したトリック再生** — この機能を使用すると、TVSDKはトリック再生モードでiFrameストリームを切り替えることができます。 iFrame以外のプロファイルを使用して、低速でトリック再生を行うことができます。

* **よりスムーズなトリック再生** — 以下の改善により、ユーザ体験が向上します。

   * トリック再生中の可変ビットレートとフレームレートの選択(帯域幅とバッファーのプロファイルに基づく)

   * 最大30 fpsの高速再生を行うには、IDRストリームの代わりにメインストリームを使用します。

* **コンテンツ保護**

   * **解像度ベースの出力保護 — この機能は** 、再生の制限を特定の解像度に関連付け、DRMコントロールをより詳細に設定できるようにします。

* **ワークフローのサポート**

   * **直接請求の統合 —** Adobe Analyticsバックエンドに請求指標を送信します。バックエンドは、顧客が使用するストリームに対してAdobe Primetimeによって認証されています。
   TVSDKは、顧客の販売契約に従って指標を自動的に収集し、課金の目的で必要な定期的な使用状況レポートを生成します。 TVSDKは、各ストリーム開始イベントで、Adobe Analyticsデータ挿入APIを使用して、コンテンツタイプ、広告挿入が有効なフラグ、および請求可能なストリームの継続時間に基づくdrm有効なフラグなどの請求指標をAdobe Analytics Primetimeが所有するレポートスイートに送信します。 これは、お客様のAdobe Analyticsレポートスイートやサーバー呼び出しに影響を及ぼしたり、含まれたりすることはありません。 リクエストに応じて、この請求の使用状況レポートが定期的に顧客に送信されます。 これは、利用状況の請求のみをサポートする請求機能の最初のフェーズです。 ドキュメントで説明されているAPIを使用して、販売契約に基づいて設定できます。 この機能はデフォルトで有効になっています。 この機能をオフにするには、リファレンスプレイヤーのサンプルを参照してください。

   * **フェイルオーバーのサポートの強化** — ホストサーバー、プレイリストファイル、セグメントに障害が発生した場合でも、中断されない再生を継続するための追加の戦略が実装されました。


* **広告**

   * **Morth統合 —** Morthからの広告視聴率測定のサポート。

   * **コンパニオンバナー** — コンパニオンバナーはリニア広告と共に表示され、多くの場合、広告の終了後も表示に引き続き表示されます。 これらのバナーは、html（HTMLスニペット）またはiframe（iframeページのURL）のタイプのいずれかです。

* **解析**

   * **VHL 2.0 -** Adobe Analyticsの使用データを自動収集するための、最新の最適化されたVideo Heartbeats Library(VHL)統合です。 APIの複雑さが減り、実装が容易になりました。 Android用のVHLライブラリ [v2.0.0をダウンロードし](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/releases) 、libsフォルダー内のJARファイルを抽出します。

* **SizeAvailableEventListener**

   * `getHeight()` とのメ `getWidth()` ソッドは、 `SizeAvailableEvent` それぞれ高さと幅で出力を返すようになりました。 表示縦横比は、次のように計算できます。

      ```java
      SizeAvailableEvent e;
      DAR = e.getWidth()/ e.getHeight();
      ```

      ストレージの幅とSarの高さに関する縦横比は、フレームの幅とフレームの高さの計算にも使用できます。

      ```java
      SAR = e.getSarWidth()/e.getSarHeight();
      frameHeight = e.getHeight();
      frameWidth = e.getWidth()/SAR;
      ```

* **Cookie**

   * Android TVSDKは、AndroidアプリケーションのCookieStoreに保存されたJAVA cookieへのアクセスをサポートするようになりました。 新しいCookieが **Set-Cookie** Responseヘッダーの一部として提供されるたびに記録するコールバックAPI(onCookiesUpdated)が提供されます。 これらのcookieは、CookieStoreを使用して特定のURI/ドメインに対してこれらのcookie値を設定することで、異なるURI/ドメインに対して使用されるHttpCookieのリストとして使用できます。 同様に、TVSDKのcookie値もCookieStore追加APIを使用して更新されます。

## 機能のマトリックス {#feature-matrix}

Android向けTVSDKは、ビデオアプリケーションに機能を追加するために実装できる多数の機能をサポートしています。

次の機能の表では、「Y」はこの機能が現在のリリースでサポートされていることを示しています。

| 機能 | コンテンツタイプ | HLS |
|---|---|---|
| 一般再生（再生、一時停止、シーク） | VOD + Live | Y |
| FER — 一般再生（再生、一時停止、シーク） | FER VOD | Y |
| 広告の再生中のシーク | ライブ | 未サポート |
| AC3 | VOD + Live | 未サポート |
| MP3 | VOD | 未サポート |
| MP4コンテンツ再生 | VOD | Y |
| 可変ビットレート切り替えロジック | VOD + Live | Y |
| オーディオのみ再生 | VOD + Live | Y |
| マルチCDNのサポート | VOD + Live | 未サポート |
| オーディオ専用メディアを含む広告の再生 | VOD + Live | 未サポート |
| クローズドキャプション — 608/708 | VOD + Live | Y |
| クローズドキャプション — WebVTT | VOD + Live | Y |
| マニフェストのフェイルオーバー | VOD + Live | Y |
| 高度なフェイルオーバー | VOD + Live | Y |
| QoSとプレイヤー通知 | VOD + Live | Y |
| cookieヘッダーのサポート | VOD + Live | Y |
| カスタムHTTPヘッダーのサポート | VOD + Live | Y（ホワイトリストが必要） |
| バッファ制御パラメータの設定 | VOD + Live | Y |
| 可変ビットレートコントロールの設定 | VOD + Live | Y |
| カスタムマニフェストタグ | VOD + Live | Y |
| 遅延オーディオバインディング | VOD + Live | Y |
| 302リダイレクト | VOD + Live | Y |
| オフセットのある再生 | VOD + Live | Y |
| オーディオのみ再生 | VOD + Live | Y |
| トリック再生 | VOD + Live | Y |
| トリック再生でのスローモーション | VOD + Live | 未サポート |
| スムーズトリック再生（ABRを使用） | VOD + Live | Y |
| ID3の解析 | VOD + Live | Y |
| 広告のブラックアウト | VOD + Live | 未サポート |
| 即時オン | VOD + Live | 未サポート |
| 不連続マーカのサポート | VOD + Live | Y |
| 302リダイレクト定着性 | VOD + Live | Y |

| 機能 | コンテンツタイプ | HLS |
|---|---|---|
| 一般再生、広告有効 | VOD + Live | Y |
| 広告が有効なFERコンテンツ | VOD | Y |
| デフォルトの広告動作 | VOD + Live | Y |
| VAST 2.0/3.0 | VOD + Live | Y |
| VMAP 1.0 | VOD + Live | Y |
| MP4広告 | VOD + Live | Y（CRSから） |
| 広告を有効にしたトリック再生 | VOD + Live | Y |
| 広告のみ | VOD | Y |
| ターゲット設定パラメーター | VOD + Live | Y |
| カスタムパラメータ | VOD + Live | Y |
| カスタム広告動作 | VOD + Live | Y |
| カスタム広告タグ | ライブ | Y |
| カスタム広告リゾルバー | VOD + Live | Y |
| フリーホイールカスタム広告リゾルバー | VOD | Y |
| C3 | VOD + Live | 未サポート |
| 遅延広告解決 | VOD | Y |
| 不連続マーカのサポート — SSAI | VOD + Live | Y |
| コンパニオン広告、バナー広告、クリック可能広告 | VOD + Live | Y |
| VPAID 2.0 | VOD + Live | Y(JS) |
| 早期広告出口 | ライブ | Y |
| ルールベースのクリエイティブの優先順位付け | VOD + Live | Y |
| CRSルール | VOD + Live | Y |
| JSON広告リゾルバー | VOD + Live | 未サポート |
| 環濠集積 | VOD + Live | Y |

| 機能 | コンテンツタイプ | HLS |
|---|---|---|
| AES暗号化 | VOD + Live | Y |
| AES暗号化の例 | VOD + Live | Y |
| トークン化ストリーム | VOD + Live | Y |
| DRM | VOD + Live | Primetime DRMのみ(将来：Widevine) |
| 外部再生(RBOP) | VOD + Live | Primetime DRMのみ |
| ライセンスローテーション | VOD + Live | Primetime DRMのみ |
| キーの回転 | VOD + Live | Primetime DRMおよびWidevine DRM |

| 機能 | コンテンツタイプ | HLS |
|---|---|---|
| Adobe Analytics VHLの統合 | VOD + Live | Y |
| 請求 | VOD + Live | Y |

## 解決された問題 {#resolved-issues}

レポートされた問題に解決が関連付けられている場合は、Zendesk参照（ZD#xxxxxなど）が表示されます。

**Android TVSDK 3.11**

この節では、TVSDK 3.11 Androidリリースで解決された問題の概要を示します。

* ZD#41252 - Android TVSDK参照アプリで、WebVTTを使用したHLSマニフェストのグリフ記号が見つからない場合に、韓国語の文字が表示されます。

### 以前のリリースで解決された問題

**Android TVSDK 3.10**

* ZD#40340：すべてのTS(TypeScript)ファイルをブラックリストにした後で再生を試みると、「App Not Responding」エラーが発生してアプリケーションがクラッシュする。

**Android TVSDK 3.8**

* 新しい雑誌号は追加されませんでした。

**Android TVSDK 3.7**

* 新しい雑誌号は追加されませんでした。

**Android TVSDK 3.6**

* 新しい雑誌号は追加されませんでした。

**バージョン3.5**

* ZD#37503 - CRSルールのJSON応答は、重複要求を避けるためにキャッシュされます。

**バージョン3.4**

* ZD#37996 — リニアストリームおよびVOD CMAF HEVCストリームの再生が途切れる問題を修正しました。
* ZD#37706 — 文字化けしたキャプションに関する問題を修正しました。
* ZD#37622 — 特定の広告に対する致命的なURISyntaxErrorsに関する問題を修正しました。
* ZD#36938 — ビットレートを中間のビットレートに切り替えてから、トリック再生を終了した後で最も高いビットレートに切り替える問題を修正しました。

**バージョン3.3**

* ZD#37394:CMAFアセットは、速度が変化した後にアーティファクトを発生させます。
   * トリック再生中にプロファイルの変更が発生する問題を修正しました。
* ZD#37396 — 一部のミッドロールおよびポストロールに広告追跡イベントがありません。
   * 広告追跡イベントの特定のケースを修正。
* ZD#37491 — エラーメタを含むHTTPステータスコードが存在しません。
   * スタック内の上位のネットワークエラーの伝播に対処。
* ZD#37808 — 新しいカスタムヘッダーをホワイトリストに登録しました。
   * この修正の一環としてSSAI_TAGのサポートが追加されました。
* ZD#37622 — 特定の広告ポッドからのURI構文エラー。
   * エンコードされていない%を含む広告を顧客のAndroidアプリに配信した場合のストリーム再生のクラッシュに関する問題を修正しました
* ZD#37631 - Android TVSDKのマスターマニフェストの再試行メカニズム。
   * この機能強化を処理するための新しいAPIをネットワーク設定に追加しました。 このAPIを使用しない場合、マニフェストは再試行されません。 これを使用すると、マニフェストはネットワークエラーとタイムアウトの処理を再試行します。

**バージョン3.2**

* ZD#37493 — ライブ再生用のトラッキングビーコンが、シーケンス内の最初の広告に対して断続的に呼び出されません。
* ZD#36985- VMAP応答の空の広告の時間に対してトラッキングビーコンが送信されない。
* ZD#37134 - TVSDKがVMAP応答に対して間違ったIDを断続的にスローします。

**バージョン3.0**

* ZD#33740 - TVSDKは、MediaPlayerオブジェクトを作成し、replaceCurrentResource()を呼び出した直後に、不要な警告をスローします。

   * プレーヤーが中断状態の場合にのみrestoreを呼び出すことで、以前の修正を改善しました。

* ZD#36442 — 新しい再生が行われるたびに、リモートデバッグセッションが切断され、デバッグができなくなります。

   * デバッグはデフォルトで有効になっていないので、Web表示ではデフォルトでデバッグはできません。 MediaPlayer.getCustomAdView()から返されたオブジェクトでsetWebContentsDebuggingEnabled(true)を呼び出すことで、必要に応じてデバッグを有効にする必要があります。

* ZD#33688 — ジャストインタイムのサポートと解決

   * 広告の時間は、広告の時間の位置より前に、指定した間隔で解決されます。

* ZD#36441 — ライブウィンドウの長さが5分を超えて増加し続け、複数の問題が発生しています。

   * 仮想ライブポイントの計算中にvirtualStartTimeが2回追加され、その結果この問題が発生する問題を修正しました。

**Android TVSDK 2.5.6**

* ZD #34992 — クローズドキャプションの言語が空です。

   * TVSDKが、キャプショントラックの詳細を取得するために、メインマニフェストから#EXT-X-MEDIA:TYPE=CLOSED-CAPTIONSを解析していなかった問題を修正しました。

* ZD #35078 - Android Pの検証。

   * TVSDK 2.5.6は、最新のAndroid Pベータ版ビルドで検証されました。 新しいAndroid OSが原因で問題は見つかりませんでした。

* ZD #34149 — エラーが発生しても、プレーヤーは引き続き要求を表示します。

   * すべてのプロファイルがダウンした場合（404エラー）も、TVSDKが繰り返し呼び出しを行う問題を修正しました。

* ZD #31533 — アプリがバックグラウンドに送信された後、Androidでオーディオを再生します。

   * アプリケーションがバックグラウンドの場合にオーディオの再生を有効にするために、引数として「True」を指定して（プレーヤーがPREPARED状態の場合に）呼び出す必要があるMediaPlayerのAPIを追加しました。 `enableAudioPlaybackInBackground`

**Android TVSDK 2.5.5**

* ZD #21647 — 実際のビデオサイズが640 x 360の場合、Android TVSDKは640 x 368と通知します。

   * 変数m_nOutputHeight （AndroidMCVideoDecoder内）が、実際の出力高さではなくフレーム高さで更新されるため。 m_nOutputHeightを正しく計算するために、関数getVideoFrameに関連する変更を行いました。

* ZD #26614 — 緊急、サードパーティの広告提供/プログラム — インプレッションの提供に失敗。

   * &lt;VAST version =&quot;2.0&quot;>のように「スペース」が「等しい」記号の前にある場合に問題が再現される、XML解析での問題の処理により、以前の修正を強化しました。

* ZD #29296 - Android:CRS追加リクエストに対するAdSystemおよびCreative ID。

   * 1401および1403のリクエストに、新しいパラメーターとして「AdSystem」および「CreativeId」を含めるようになりました。

* ZD #33062 - CDATAノードの下のVAST応答でパイプ文字が発生すると、TVSDKがクラッシュします。

   * NetworkConfigurationクラスのAPI setEncodeUrlForTrackingは、エンコードするURL内の安全でない文字として削除されました

* ZD #33063 - CRSファイル選択ロジックが壊れました。TVSDKがwebm形式のCRSリクエストを送信せず、3gppファイル用に送信していました。

   * ロジックを修正しました。 webmおよび3gpp形式のメディアファイルを使用する場合、Web用に送信するCRSリクエスト。 また、3gpp形式の両方のメディアファイルを使用する場合、最も高いビットレートの3gppファイルに対してCRSリクエストが送信されます。

* ZD #33125 - VMAP内で特定のDoubleClickタグを使用すると、Androidアプリがクラッシュします。

   * クラッシュを回避するためにシナリオを修正しました。

* ZD #32256 — ライセンスのローテーションとキーのローテーションの問題 — Adobe Access

   * SampleAESコンテンツのDRMメタデータを使用したセグメントの初期化を修正しました。 AES128コンテンツで正常に機能します。

* ZD #33619 — 増加中のプレイリストコンテンツが、ライブポイントの近くでバッファリング状態で停止した場合の早送り。

   * トリック再生モードでライブポイントを越える場合の処理

* ZD #34151 - TimedMetadataオブジェクトが正しくありません。

   * 2つのTimedMetadataイベントが、タイムラインで同じ時間に属していた場合、ランダムな順序で表示されていました。 マニフェスト内で元の順序を維持。

* ZD #34189 — 広告の時間の開始をシークする場合の問題。

   * この問題は、不連続性を使用して繋ぎ合わされるSSAI広告に関するものでした。 その原因は、このような広告の始まりを探すとき、キーフレームを検索しても見つからないときの行動でした。 その理由は、広告の最小オーディオタイムスタンプが、最小ビデオタイムスタンプより前にあったためです。 したがって、間違ったfragmentDumpデータでキーフレームを検索することになります。 今すぐ修正。

* ZD #34528 - FireTV 3rd genドングルで、ビデオ解像度が640 x 360以上にアップグレードされない。

   * 最新のファームウェアアップデートを含む修正の強化

* ZD #34793 - VideoEngineがauditudeSettingsが使用可能で、使用できなかったと仮定していた場合に、カスタムコンテンツリゾルバーでのクラッシュに使用されるTVSDK 2.5.x。

   * Null共有ポインタ(auditudeSettings)の関数呼び出しが原因でクラッシュが発生していました。 VideoEngineTimeline::placeToSourceTimeline()内に条件付きチェックを追加し、そのオブジェクトに対して何も呼び出す前にauditudeSettingsが使用可能であることを確認しました。

* ZD #32584 - VAST応答の&lt;拡張子>ノードに存在する完全な情報にアクセスできません。

   * XML解析に関する問題を修正し、現在NetworkAdInfoが&lt;拡張子>ノードにある完全な情報を提供するようになりました。

* ZD #35086 — 特定のVMAP応答の場合、プレーヤーから完全な拡張データを取得できません。

   * 拡張XMLの属性値に重複引用符が含まれている場合、XMLの解析が機能しなかったので、拡張XMLに固有の問題が発生していました。 問題を修正しました。

**Android TVSDK 2.5.4**

* ZenDesk#33659 - Webビューのリモートデバッグを有効にする再生セッション。

WebViewDebugingは、デフォルトでFalseに設定されています。 デバッグを有効にするには、setWebContentsDebuggingEnabled(true)を使用して、アプリケーションを介してtrueに設定します。

* ZenDesk#33011:CRS要求が失敗した場合、広告のタイムラインが解決されません。

   広告に対するCRSリクエストが失敗すると、タイムラインが解決され、残りの広告が再生されます。

* ZenDesk#34528 - FireTV第3世代ドングルのビデオ解像度が640 x 360以上にアップグレードされない。

   ビデオ解像度はビットレートスイッチとして上に切り替わります。

* ZenDesk#33192 - AudioUpdatedEventListener::onAudioUpdatedを使用してトラックを取得すると、AudioTrackの名前がNULLになります。

   FireTV Stickのいくつかのシナリオでは、実際にオーディオの更新が行われなかったときにonAudioUpdateイベントが実行されていました。 これは修正されました。

**Android TVSDK 2.5.3**

* Zendesk#32216 - TimedMetadataカスタムタグ購読が機能しません。

   1.4ではID3データをバイト配列（APICまたは汎用データをサポート）としてクライアントに返しますが、1.4では文字列が返されます。 バイト配列は、ヌル終端文字自体を処理しないので、クライアントに特殊文字を表示していました。 この問題は現在修正されています。
* Zendesk#32670 — プレーヤーが冗長プレイリストにフェイルオーバーしない

   これは正常に動作し、setNetworkDownVerificationUrlは期待どおりに動作しています。
* Zendesk#32369 — クローズドキャプションに、異なる色のガベージまたはアーティファクトが表示されます。

   最新のビルドでCCの問題が修正されました。
* Zendesk#25590 — 画質調整：TVSDK cookieストア（C++からJAVA）

   Android TVSDKは、（AndroidアプリケーションのCookieStoreに保存される）JAVAレイヤーとC++ TVSDKレイヤーの間のcookieへのアクセスをサポートするようになりました。
* Zendesk#32252 - TVSDK_Android_2.5.2.12にPTPLAY-20269の修正がないようです。

   この問題は修正され、2.5.2ブランチに統合されました。
* Zendesk#31806 - PREPARINGでのオーディチュードスティック

   応答XMLに空のタグが含まれていたため、プレイヤーが準備中の状態で停止していました。 問題が修正されました。
* Zendesk#31727 - TVSDK 2.5のクローズドキャプション文字がドロップされるか、スペルミスがある。

   問題が修正され、文字の削除やスペルミスは発生しません。
* Zendesk#31485 - 2.5のDrmManager

   新しいDrmManager（コンテキストコンテキスト）を使用したDrmManagerの作成で問題が発生しました。 DRMManagerを提供するDRMServiceクラスを実装しました。
* Zendesk#32794- 1080P解像度のストリームがAndroidで再生されない

   2.5では、SizeAvailableEventおよびPreviously、SizeAvailableEventのgetHeight()およびgetWidth()メソッドを変更し、メディア形式で返されたフレームの高さとフレームの幅を返すのに使用されていました。 デコーダーが返す出力の高さと出力の幅をそれぞれ返すようになりました。
* Zendesk #19359セットレベルマニフェストでの#EXT-X-FAXS-CM属性の位置が原因でFlash Playerがクラッシュする。

   #EXT-X-FAXS-CMタグは、個々のビットレートまたはセグメントがプレイリストに表示される前に、常に最上位のプレイリストに表示される必要があります。

**Android TVSDK 2.5.2**

* Zendesk#17305背景が不透明でないクローズドキャプションのアーティファクト。

   TextFormatのsetTreatSpaceAsAlphaNumプロパティが公開されます。 デフォルトでは、このプロパティはFalseです。 クライアントでプロパティをTrueに設定して、暗い領域の問題を解決します。

* Zendesk#25097 CCディスプレイには、CCの設定で視覚的なアーティファクトが表示されます。

   TextFormatのsetTreatSpaceAsAlphaNumプロパティが公開されます。 デフォルトでは、このプロパティはFalseです。 クライアントでプロパティをTrueに設定して、暗い領域の問題を解決します。

* Zendesk #31620 TVSDKプレーヤーから送信するユーザーエージェント文字列が切り捨てられます。

   ユーザーエージェント文字列は、128文字を超えて切り捨てられることはなくなりました。

   Adobe Primetimeバージョン文字列がシステムユーザーエージェントに追加されます。

* Zendesk #30809 SEEK_ENDイベントが見つからない場合、アプリは再生状態に移行しません。
* Zendesk #30415クローズドキャプションの「シアン」の色が、以前のPrimetime TVSDKリリースと比較して、濃い青色（青色）になりました。

   色が濃いシアンからシアンに変更されます。

* Zendesk #30727 VOD広告がダウンロード/解決されない。

   VMAP XMLで、明示的な終了タグ(‘&lt;/VAST>&#39;)のない空のVASTタグがあり、その後に改行文字がない場合、VMAP XMLは正しく解析されず、広告が再生されない場合があります。

**Android TVSDK 2.5.1**

* デバイス固有(Samsung Galaxy Tab 4)のクラッシュ。Auditudeを使用するVOD DRM LBAを選択し、広告をクリックします。
* VHL — オフセットからコンテンツを開始する際に、正しくないハートビート呼び出しが送信されます。
* VPAID広告が再生されると、イベント:type:play広告に対するVHLハートビート呼び出しが見つかりません。
* プレイヤーは、完了ステータスになった後、ポストロール広告のSKIP adBreakPolicyを持つPLAYINGステータスに戻ります。
* cookieが送信広告コールバックに添付されていない。
* 広告キューポイントは表示されません。
* EAC3 SAPトラックが別々のHLSが読み込まれません。
* メディアプレイヤーが復元された後、TVSDKが画面オンインテントを受け取ると、プレイヤーがクラッシュします。

## 既知の問題と制限 {#known-issues-and-limitations}

**Android TVSDK 3.11**

* 新しい制限は追加されません。

### 以前のリリースの既知の問題と制限

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

* ID3、クローズドキャプション、遅延バインディングオーディオのサポートは、CMAF(CBC)ストリームに対して検証されていません。
* 一部のデバイスでは、CMAFストリームでのトリック再生中にビデオの歪みが上に表示されることが原因で、再現性の低い問題が発生します。

**Android TVSDK 3.3**

* clcp:c608キャプションは、CMAFストリーム再生に対してはサポートされていません。

**Android TVSDK 3.2**

* TVSDK 3.2は、CMAFサンプルAESおよびAES128ストリーム再生をサポートしていません。
* HEVC CMAFストリームには、クローズドキャプション再生のサポートは含まれていません。
* 非暗号化セグメントの周りでシークが実行されると、WV暗号化ストリームに緑色の色が表示されます。
* CMAFストリームはID3イベントをサポートしません。
* HLSストリームはTTMLキャプション形式をサポートしていません。

**Android TVSDK 3.0**

* HEVCのサポートには、このリリースで次の制限があります

   * DRMはサポートされていません
   * CC(CEA 608/708)のサポートは確認されていません
   * 4Kのサポートはまだ存在しません
   * ID3タグのサポートが検証されていません

* 広告の進行状況イベントの場合、タイムラインバーに100%正確な広告の再生時間が反映されないことがあります。 回避策として、を使用して、広告の再生 `adcompleteevent` の完了を知り、タイムラインバーの更新、広告関連のUIの削除など、様々な目的でUIを更新できます。
* VMAPから返された広告呼び出しは、ジャストインタイムルックアヘッドの位置を受け入れません。

**Android TVSDK 2.5.6**

* 複数のVMAP広告の時間を同時に使用することはできません。

**Android TVSDK 2.5.3**

このバージョンには次の問題があります。

* ライブビデオの再生時に、ローエンドデバイスでオーディオビデオの同期の問題が発生したり、ネットワークの状態が悪かったりする場合があります。
* FERストリームの場合、virtualTimeとlocalTimeは異なる場合があります。 また、オフセットを持つFERも機能しません。
* 遅延バインディングオーディオのコンテンツがシークされると、再生が停止する場合があります。
* WebVTTのキャプションが断続的に、LIVEコンテンツで同期されない場合があります。
* 広告の時間から離れた後、数個のフレームの高速再生が断続的に表示されます。
* 広告が再生されている場合でも、303エラーが3つのラッパー広告の時間に対してスローされることがあります。

**Android TVSDK 2.5.2**

このバージョンには次の問題があります。

* ライブビデオの再生で、ローエンドデバイスでのオーディオビデオの同期の問題が発生する場合があります。
* VODメディアの最後までシークすると、再生が停止する場合があります。
* FERストリームの場合、virtualTimeとlocalTimeは異なる場合があります。 また、オフセットを持つFERは機能しません。

**Android TVSDK 2.5.1**

このバージョンのTVSDKには、次の問題があります。

* ライブビデオの再生で、ローエンドデバイスでのオーディオビデオの同期の問題が発生する場合があります。
* FERストリームの場合、virtualTimeとlocalTimeは異なる場合があります。 また、オフセットを持つFERは機能しません。
* VMAP XMLで、明示的な終了タグ(&lt;/VAST>)のない空のVASTタグがあり、その後に改行がない場合、VMAP XMLは正しく解析されず、広告が再生されない可能性があります。
* VPAIDポストロールはサポートされていません。

## 役立つリソース {#helpful-resources}

* [必要システム構成](https://docs.adobe.com/content/help/en/primetime/programming/tvsdk-3x-android-prog/introduction/android-3x-requirements.html)
* [TVSDK 3.10 for Androidプログラマーガイド](https://docs.adobe.com/content/help/en/primetime/programming/tvsdk-3x-android-prog/introduction/android-3x-overview-prod-audience-guide.html)
* [APIリファレンス用のTVSDK Android Javadoc](https://help.adobe.com/en_US/primetime/api/psdk/javadoc3.5/index.html)
* [TVSDK Android C++ APIドキュメント](https://help.adobe.com/en_US/primetime/api/psdk/cpp_3.5/namespaces.html) — 各Javaクラスには対応するC++クラスがあり、C++ドキュメントにはJavadocよりも詳しい説明が含まれています。Java APIの詳細については、C++のドキュメントを参照してください。
* [Android(Java)用TVSDK 1.4 ～ 2.5移行ガイド](https://helpx.adobe.com/primetime/migration-guides/tvsdk-14-25-android.html)
* 画面のオン/オフシナリオの処理については、ビルドに含ま `Application_Changes_for_Screen_On_Off.pdf` れるファイルを参照してください。
* 完全なヘルプドキュメントは、 [Adobe Primetimeのラーニングとサポートページで参照してください](https://helpx.adobe.com/support/primetime.html) 。
