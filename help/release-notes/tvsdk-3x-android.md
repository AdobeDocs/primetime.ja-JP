---
title: TVSDK 3.12 for Androidリリースノート
seo-title: TVSDK 3.12 for Androidリリースノート
description: Android向けTVSDK 3.12リリースノートでは、TVSDK Android 3.12の新機能や変更点、解決済みおよび既知の問題、デバイスの問題について説明します。
seo-description: Android向けTVSDK 3.12リリースノートでは、TVSDK Android 3.12の新機能や変更点、解決済みおよび既知の問題、デバイスの問題について説明します。
uuid: 685d46f5-5a02-4741-af5c-91e91babd6f7
products: SG_PRIMETIME
topic-tags: release-notes
discoiquuid: 3a27379f-3cef-4ea3-bcae-21382dc1e9fd
translation-type: tm+mt
source-git-commit: d1881d1fe97d416ee0f69f62828aef46c5ad21bb
workflow-type: tm+mt
source-wordcount: '5415'
ht-degree: 0%

---


# TVSDK 3.12 for Androidリリースノート {#tvsdk-for-android-release-notes}

Android向けTVSDK 3.12リリースノートでは、TVSDK Android 3.12の新機能や変更点、解決済みおよび既知の問題、デバイスの問題について説明します。

Androidリファレンスプレイヤーは、Android TVSDKと共に、配布物のsamples/ディレクトリに含まれています。 付属のREADME.mdファイルでは、リファレンスプレイヤーの構築方法が説明されています。

>[!NOTE]
>
>リファレンスプレーヤーを正常に構築するには、リリースと共に配布されているREADME.mdに記載されているとおり、次の操作を行います。
>
>1. https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/releases [からVideoHeartbeat.jarをダウンロードします](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/releases) （Android v2.0.0用のVideoHeartbeatライブラリ）
>1. libs/フォルダーにVideoHeartbeat.jarを抽出します。
>



Android向けTVSDKは、以前のバージョンと比べて多くのパフォーマンスが向上しています。 高品質な視聴環境を提供し、マルチCDNのサポートを除き、バージョン1.4のすべての機能を搭載しています。

サポートされる機能とサポートされない機能の包括的なセットは、リリースノートの [機能マトリクス](#feature-matrix) セクションに表示されます。

## Android TVSDK 3.12

Primetime Referenceアプリケーションのグレードバージョンがバージョン5.6.4に更新されました。

Android Studioを使用してReference Appをセットアップして実行するには、TVSDKのzipファイル()に記載されているReadMeファイルの指示に従ってく `TVSDK_Android_x.x.x.x/samples/PrimetimeReference/src/README.md`ださい。

現在のリリースで修正されたトップのお客様の問題は、 [解決された問題の節で説明しています](#resolved-issues) 。

### 以前のリリースの新機能および機能強化

**Android TVSDK 3.11**

* **保護システム固有のヘッダー(PSSH)ボックスのフェッチが許可されました** - TVSDKは、現在読み込まれているメディアリソースに関連付けられた保護システム固有のヘッダーボックスを取得できます。 に新しいAPI `getPSSH()` が追加され `com.adobe.mediacore.drm.DRMManager`ました。

詳しくは、Widevine DRM [を参照してください](../programming/tvsdk-3x-android-prog/android-3x-content-security/android-3x-drm-widevine.md)。

**Android TVSDK 3.10**

このリリースでは、「 [解決された問題](#resolved-issues) 」セクションで説明されている、お客様の主な問題の修正に重点を置いています。

**Android TVSDK 3.9**

* **HTTPSを介した安全な配信** - Android TVSDK 3.9では、HTTPSを介した安全な配信機能を導入し、比類のない拡張性とパフォーマンスで安全にコンテンツを配信します。

   HTTPS経由の安全な配信を有効にするため、クラスで新しいAPIが導入され `NetworkConfiguration` ました。

   `public void setForceHTTPS (boolean value)`

   `public boolean getIsForceHTTPS()`

**Android TVSDK 3.8**

* **部分的な広告ブレーク機能を伴うプリロールのサポート** — この機能強化により、TVSDK 3.8は、部分的な広告ブレーク機能(PABI)を伴うプリロール広告をサポートします。

プリロール広告がある場合は、その広告が再生され、ライブポイントからコンテンツが再生され、ライブテレビのエクスペリエンスがエミュレートされます。

**Android TVSDK 3.7**

* Widevineテストコンテンツの場合、DRMManagerクラス `setMediaDrmCallback` の新しいAPIが公開され、MediaDrmCallbackインターフェイスのデフォルト実装が上書きされます。

   `public static void setMediaDrmCallback(MediaDrmCallback callback)`

* C++レイヤー（Android 64ビット） `MediaPlayerEvent.ITEM_UPDATED` でAppCrashエラーが処理されない問題を修正しました。

**Android TVSDK 3.6**

* **64ビット要件のアプリケーションの強化** — ネイティブライブラリ `(libAVEAndroid.so)` がアップグレードされ、2つのバージョンで利用できるようになりました。 既存のarmeabi（32ビット）ネイティブライブラリの場所がから変更され `/framework/Player to /framework/Player/armeabi` 、 `/framework/Player/arm64-v8a.`

**バージョン3.5**

* **Just In Time Ad Resolution** - TVSDK 3.5は、再生された広告のサポートをタイムラインから削除します。

* **オフライン再生のサポートを有効にしました** — オフライン再生を使用すると、ビデオコンテンツをデバイスにダウンロードして、接続されていないときに視聴できるようになりました。 詳しくは、「[Androidでの](https://helpx.adobe.com/content/dam/help/en/primetime/programming-guides/psdk_android_3.5.pdf)オフライン再生」を参照してください。

**バージョン3.4**

* TVSDKは、CBCで暗号化されたプレーンストリームに対して、CMAFストリーム再生をサポートするようになりました。

**バージョン3.3**

* **APIの変更**

   * ネットワークエラーとタイムアウトを処理す `NetworkConfiguration::setNumOfTimesManifestRetryBeforeError(n)*` るための新しいAPIが追加されました。
      * (n)は再試行数です。

**バージョン3.2**

* **並行広告解決とマニフェストのダウンロードのサポート**

   * TVSDK 3.2は、VMAPを除くすべての広告リクエストと広告の時間に対して順次解決ではなく、同時解決をサポートしています。

   * 広告の時間内のすべての広告マニフェストが同時にダウンロードされます。

* **広告の解決とマニフェストのダウンロードタイムアウトのサポートを有効にしました。**

   * 広告の解決とマニフェストのダウンロード全体に対してタイムアウト値を設定できるようになりました。  VMAPの場合、すべての広告の時間が順番に解決されるので、タイムアウト値は個々の広告の時間に適用されます。

* **AdvertisingMetadataクラスに新しいAPIが追加されました。**

   * `void setAdResolutionTimeout(int adResolutionTimeout)`

   * `int getAdResolutionTimeout()`

   * `void setAdManifestTimeout(int adManifestTimeout)`

   * `int getAdManifestTimeout()`

* **以下のAPIをAdvertisingMetadataクラスから削除しました。**

   * `void setAdRequestTimeout(int adRequestTimeout)`

   * `int getAdRequestTimeout()`

* **AC3/EAC3オーディオコーデックを使用したストリームの再生を有効にする**

   * `void alwaysUseAC3OnSupportedDevices(boolean val)` 授 `MediaPlayer` 業中

* **TVSDKは、暗号化されたWidevine CTRに対して、CMAFおよびプレーンストリームの再生をサポートしています。**

* **4K HEVCストリームの再生がサポートされるようになりました。**

* **並行広告呼び出しリクエスト** - TVSDKは、20件の広告呼び出しリクエストを並行してプリフェッチするようになりました。

**バージョン3.0**

* **TVSDK 3.0は、High Efficiency Video Coding(HEVC)ストリームをサポートしています。**

* **ジャストインタイム — 広告マーカーに近い広告を解決する遅延広告**&#x200B;解決は、各広告の時間を個別に解決するようになりました。 以前は、広告の解決は2段階のアプローチでした。 プリロールは、再生開始の前に解決され、再生開始後に組み合わされたすべてのミッド/ポストロールスロットが解決されました。 この強化された機能を使用すると、広告キューポイントの前の特定の時間に各広告の時間が解決されるようになりました。

> [!NOTE]
>
> 遅延広告の解決は、デフォルトでオフになるように変更され、明示的に有効にする必要があります。

この広告メタデータに関連付けられ `AdvertisingMetadata::setDelayAdLoadingTolerance` ている遅延広告読み込みの許容値を取得するための新しいAPIが追加されました。\
PREPARATIONの直後にシークが可能になり、広告の時間をシークすると、シークが完了する直前に解決されます。\
シグナリングモード `SERVER_MAP` とがサポート `MANIFEST_CUES` されています。

詳しくは、APIとイベントの変更に関するAndroid向け [TVSDK 3.0プログラマーガイド](../programming/tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/c-lazy-ad-resolving/c-lazy-ad-resolving.md) （英語）を参照してください。

* **最新バージョン`targetSdkVersion`に更新**

19 `targetSdkVersion` から27に更新され、スムーズに機能するようになりました。

* **Placement.Type getPlacementType()は、インターフェイスTimelineMarkerのメソッドになりました**

   このメソッドは、配置タイプPlacement.Type.PRE_ROLL、Placement.Type.MID_ROLLまたはPlacement.Type.POST_ROLLを返します。 広告の時間が未解決の場合、TimelineMarkerインターフェイスのgetDuration()メソッドは0を返します。

**バージョン2.5.6。**

* **TVSDK 2.5は、Android Pをサポートします。**

* **バックグラウンドオーディオの有効化**

   アプリがフォアグラウンドからバックグラウンドに移動したときのオーディオ再生を有効にするには、プレイヤーがPREPARED状態のときに、アプリはMediaPlayerの `enableAudioPlaybackInBackground` APIを引数としてtrueで呼び出す必要があります。

* **alwaysUseAudioOutputLatency(boolean val) in MediaPlayerクラス**

設定する場合、オーディオタイムスタンプの計算に出力待ち時間を使用します。
ブール型パラメーターval - trueを指定すると、オーディオのタイムスタンプの計算にオーディオ出力遅延が使用されます。

* **帯域幅の速度が急に低下した場合でも、最高の再生エクスペリエンスを得るように最適化。**

TVSDKは、必要に応じて、継続中のセグメントのダウンロードをキャンセルし、適切なレンディションに動的に切り替えるようになりました。 これは、割り込みなくビットレートをシームレスに切り替えることで行われます。

**バージョン2.5.5**

* **部分的な広告ブレークの挿入**

   部分的に視聴された広告のトラッキングを実行せずに、広告の途中に参加するTVのようなエクスペリエンス。\
   例： 30秒の広告を3つ含む90秒の広告の時間の途中（40秒）にユーザーが参加します。 時間の2番目の広告から10秒経過します。

   * 2番目の広告は残りの時間（20秒）再生され、次に3番目の広告が続きます。

   * 部分的な広告再生（2番目の広告）用の広告トラッカーは起動されません。 3番目の広告のみのトラッカーが起動されます。

* **HTTPS経由のセキュアな広告読み込み**

   Adobe Primetimeには、Primetime広告サーバーおよびCRS over httpsへの最初の呼び出しをリクエストするオプションが用意されています。

* **CRSリクエストに追加されたAdSystemおよびCreative ID**

   1401リクエスト `AdSystem``CreativeId` と1403リクエストに、およびを新しいパラメーターとして含めるようになりました。

* **NetworkConfigurationクラスのAPI setEncodeUrlForTrackingは、URL内の安全でない文字をエンコードする必要があるため** 、削除されました。

**バージョン2.5.4**

Android TVSDK v2.5.4オファーには、次の更新とAPIの変更が含まれています。

* デフォルト値の変更 `WebViewDebbuging`

   `WebViewDebbuging` の値はデフォルトで `Fals`eに設定されています。 有効にするには、アプリケーション `setWebContentsDebuggingEnabled(true)` でを呼び出します。

* **OpenSSLおよびCurlバージョンのアップグレード**

   libcurlをv7.57.0に、OpenSSLをv1.0.2kに更新しました。

* VAST応答オブジェクトのアプリレベルアクセス

   VAST応答オブジェクト `NetworkAdInfo::getVastXml()` へのアクセスを提供する新しいAPIが導入されました。

**バージョン2.5.3**

Android TVSDK v2.5.3オファーには、次の更新とAPIの変更が含まれています。

* CRSを使用するTVSDKユーザーは、すべて、AndroidのTVSDK 2.5.3.85または最新のバージョンを使用して、アプリをアップグレードすることをお勧めします。 これは、既存のアプリの実装に対するドロップインの置き換えとなります。 TVSDKのアップグレード後、プロキシツールでCRSクリエイティブURLリクエストを確認します(例： Charlesを参照)、パス内のホスト名とバージョンが、以下のサンプルURL構造のように反映されていることを確認します。

   `https://primetime-a.akamaihd.net/assets/3p/v3.1/222000/167/d77/167d775d00cbf7fd224b112sf5a4bc7d_0e34cd3ca5177fbc74d66d784 bf3586d.m3u8`

* TVSDKのユーザーエージェントのカスタマイズ可能： ユーザーエージェントをカスタマイズする新しいAPIが追加されました。

   * `setCustomUserAgent(String value)`
   * `getCustomUserAgent()`

* AndroidアプリケーションとTVSDK間でCookieを共有する： Android TVSDKは、（AndroidアプリケーションのCookieStoreに保存される）JAVAレイヤーとC++ TVSDKレイヤーの間のcookieへのアクセスをサポートするようになりました。 これで、ネイティブC++レイヤーのcookieがJava Cookie Storeに公開されるので、cookieの設定や変更が可能になりました。

* APIの変更：

   * 新しいイベント `CookiesUpdatedEvent` が追加されます。 Cookieが更新されると、メディアプレイヤーによってディスパッチされます。

   * カスタムユーザーエージェントを使用す `NetworkConfiguration::set/ getCustomUserAgent()` るための新しいAPIが追加されました。

   * 安全でない文字のエンコードを強制す `NetworkConfiguration::set/ getEncodedUrlForTracking` るために、に新しいAPIが追加されました。

   * フェイルオーバー時にネットワーク検証URL `NetworkConfiguration::getNetworkDownVerificationUrl()` を設定するための新しいAPIが追加されました。

   * キャプションの表示時にスペースを英数字として扱うかどうかを定義する新しいプロパティが追加されました。 `TextFormat::treatSpaceAsAlphaNum`

* 変更点 `SizeAvailableEvent`。 以前は、2.5.2の `getHeight()` および `getWidth()``SizeAvailableEvent` メソッドは、メディア形式で返されたフレームの高さとフレームの幅を返すのに使用されていました。 現在は、デコーダーが返す出力の高さと出力の幅を返します。

* バッファリング動作の変更： バッファリング動作が変更されました。 バッファーが空の場合の処理をアプリケーション開発者に任せます。 2.5.3は、バッファーが空の場合に再生バッファーサイズを使用します。

**バージョン2.5.2**

Android TVSDK v2.5.2オファーの重要なバグ修正とAPIの変更点です。

**バージョン2.5.1**

Android 2.5.1でリリースされた重要な新機能。

* **パフォーマンスの向上 —** 新しいTVSDK 2.5.1アーキテクチャにより、パフォーマンスが多数改善されました。 サードパーティのベンチマーク調査による統計に基づき、新しいアーキテクチャは、起動時間を5分の1に短縮し、ドロップフレーム数を業界平均よりも3.8分の1に削減します。

* **VODおよびライブの即時オン — 即時オンを有効にすると** 、TVSDKは、再生開始の前にメディアを初期化し、バッファリングします。 複数のMediaPlayerItemLoaderインスタンスをバックグラウンドで同時に起動できるので、複数のストリームをバッファリングできます。 ユーザーがチャネルを変更し、ストリームが正しくバッファリングされた場合、新しいチャネル開始で直ちに再生されます。 TVSDK 2.5.1は、 **ライブストリームに対してもインスタントオンをサポートし** ます。 ライブストリームは、ライブ時間が移動すると再バッファリングされます。

* **ABRロジックの強化 —** 新しいABRロジックは、バッファー長、バッファー長の変化率、測定された帯域幅に基づいています。 これにより、ABRは帯域幅が変動する場合に適切なビットレートを選択し、バッファー長が変化するレートを監視することで、ビットレートの切り替えが実際に発生する回数を最適化します。

* **部分セグメントのダウンロード/サブセグメント —** TVSDKは、各フラグメントのサイズをさらに小さくして、可能な限り早く開始を再生します。 tsフラグメントには、2秒ごとにキーフレームが必要です。

* **遅延広告の解決 —** TVSDKは、非プリロール広告の解決を待たずに再生を開始するので、起動時間が短くなります。 シークやトリック再生などのAPIは、すべての広告が解決されるまで許可されません。 これは、CSAIで使用されるVODストリームに適用されます。 シークや早送りなどの操作は、広告の解決が完了するまで許可されません。 ライブストリームの場合、ライブイベント中は、この機能を広告解決に対して有効にすることはできません。

* **永続的なネットワーク接続 —** この機能を使用すると、TVSDKは永続的なネットワーク接続の内部リストを作成および保存できます。 これらの接続は、複数の要求に対して再利用され、各ネットワーク要求に対して新しい接続を開き、その後破棄するのではなくなります。 これにより、効率が向上し、ネットワークコードの遅延が減少し、再生パフォーマンスが向上します。
TVSDKは、接続を開くと、サーバーに *キープアライブ接続を要求します* 。 一部のサーバーでは、このタイプの接続がサポートされない場合があります。サポートされない場合、TVSDKは、再度リクエストごとに接続を行うことにフォールバックします。 また、永続的な接続はデフォルトでオンになりますが、TVSDKには、アプリが必要に応じて永続的な接続をオフにできるように設定オプションが追加されました。

* **並行ダウンロード —** ビデオとオーディオをシリーズではなく並行してダウンロードすると、起動の遅延が減少します。 この機能を使用すると、HLS LiveファイルとVODファイルの再生、サーバーからの使用可能な帯域幅の使用の最適化、バッファーの実行不足状況に陥る確率の低下、ダウンロードと再生の間の遅延の最小化を行うことができます。

* **並行的な広告ダウンロード —** TVSDKは、広告の時間をヒットする前に、コンテンツ再生と並行して広告をプリフェッチするので、広告とコンテンツのシームレスな再生を可能にします。

* **再生**

* **MP4コンテンツ再生 —** MP4短いクリップは、TVSDK内で再生するために再トランスコードする必要はありません。

   > [!NOTE]
   >
   > ABRの切り替え、トリック再生、広告挿入、遅延オーディオバインディングおよびサブセグメントは、MP4再生ではサポートされません。

* **可変ビットレート(ABR)を使用したトリック再生 —** この機能を使用すると、トリック再生モード中にTVSDKがiFrameストリームを切り替えることができます。 iFrame以外のプロファイルを使用して、低速でトリック再生を行うことができます。

* **トリックの再生がスムーズになりました —** 以下の改善により、ユーザーエクスペリエンスが向上します。

   * 帯域幅とバッファーのプロファイルに基づく、トリック再生中の可変ビットレートとフレームレートの選択

   * 最大30 fpsの高速再生を行うには、IDRストリームの代わりにメインストリームを使用します。

* **コンテンツ保護**

   * **解像度ベースの出力保護 —** この機能は、再生制限を特定の解像度に関連付け、DRMコントロールをきめ細かく指定します。

* **ワークフローのサポート**

   * **直接請求の統合 —** これは、請求指標をAdobe Analyticsバックエンドに送信します。バックエンドは、Adobe Primetimeによって、顧客が使用するストリームに対して認証されます。
   TVSDKは、顧客の販売契約に従って自動的に指標を収集し、課金の目的で必要な定期的な使用状況レポートを生成します。 TVSDKは、各ストリーム開始イベントでAdobe Analytics Data Insertion APIを使用して、請求対象ストリームの長さに基づくコンテンツタイプ、広告挿入有効フラグ、drm有効フラグなどの請求指標をAdobe Analytics Primetime所有のレポートスイートに送信します。 これは、お客様のAdobe Analyticsレポートスイートやサーバー呼び出しに影響したり、含められたりすることはありません。 リクエストに応じて、この請求の使用状況レポートが定期的に顧客に送信されます。 これは、利用状況の請求のみをサポートする請求機能の最初のフェーズです。 ドキュメントで説明されているAPIを使用して、販売契約に基づいて設定できます。 この機能はデフォルトで有効になっています。 この機能をオフにするには、リファレンスプレイヤーのサンプルを参照してください。

   * **フェイルオーバーのサポートの強化 —** ホストサーバー、プレイリストファイル、セグメントに障害が発生した場合でも中断されない再生を継続するために実装された追加の戦略。


* **広告**

   * **Morth統合 —** Morthからの広告視聴率測定のサポート。

   * **コンパニオンバナー —** Companion Bannerはリニア広告と共に表示され、多くの場合、広告が終了しても表示に引き続き表示されます。 これらのバナーは、html（HTMLスニペット）またはiframe（iframeページのURL）のタイプにすることができます。

* **解析**

   * **VHL 2.0 -** Adobe Analyticsの使用データの自動収集のための、最新の最適化されたビデオハートビートライブラリ(VHL)統合です。 APIの複雑さが減少し、導入が容易になりました。 Android用VHLライブラリ [v2.0.0をダウンロードし](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/releases) 、libsフォルダーにJARファイルを抽出します。

* **SizeAvalableEventListener**

   * `getHeight()` の `getWidth()``SizeAvailableEvent` メソッドは、それぞれ高さと幅で出力を返すようになりました。 表示縦横比は次のように計算できます。

      ```java
      SizeAvailableEvent e;
      DAR = e.getWidth()/ e.getHeight();
      ```

      Sarの幅とSarの高さに関するストレージの縦横比は、フレームの幅とフレームの高さの計算にも使用できます。

      ```java
      SAR = e.getSarWidth()/e.getSarHeight();
      frameHeight = e.getHeight();
      frameWidth = e.getWidth()/SAR;
      ```

* **Cookie**

   * Android TVSDKは、AndroidアプリケーションのCookieStoreに保存されたJAVA cookieへのアクセスをサポートするようになりました。 新しいCookieが **セット —Cookie** 応答ヘッダーの一部として提供されるたびに記録するコールバックAPI(onCookiesUpdated)が提供されます。 これらのcookieは、CookieStoreを使用して特定のURI/ドメインに対してこれらのcookie値を設定することで、別のURI/ドメインに使用されるHttpCookieのリストとして使用できます。 同様に、TVSDKのcookieの値も、CookieStore追加APIを使用して更新されます。

## 機能のマトリックス {#feature-matrix}

Android向けTVSDKは、ビデオアプリケーションに機能を追加するために実装できる多数の機能をサポートしています。

以下の機能の表では、「Y」はこの機能が現在のリリースでサポートされていることを示しています。

| 機能 | コンテンツタイプ | HLS |
|---|---|---|
| 一般再生（再生、一時停止、シーク） | VOD + Live | Y |
| FER — 一般再生（再生、一時停止、シーク） | FER VOD | Y |
| 広告の再生中にシークする | VOD + Live | 非対応 |
| HEVC再生 | VOD + Live | fMP4コンテナのみ |
| AC3およびEAC3 | VOD + Live | 非対応 |
| MP3 | VOD | 非対応 |
| MP4コンテンツ再生 | VOD | Y |
| 可変ビットレート切り替えロジック | VOD + Live | Y |
| オーディオのみの再生 | VOD + Live | Y |
| マルチCDNのサポート | VOD + Live | 非対応 |
| オーディオ専用メディアを含む広告の再生 | VOD + Live | 非対応 |
| クローズドキャプション — 608/708 | VOD + Live | Y |
| クローズドキャプション — WebVTT | VOD + Live | Y |
| マニフェストのフェイルオーバー | VOD + Live | Y |
| 高度なフェイルオーバー | VOD + Live | Y |
| QoSおよびプレイヤー通知 | VOD + Live | Y |
| cookieヘッダーのサポート | VOD + Live | Y |
| カスタムHTTPヘッダーのサポート | VOD + Live | Y（ホワイトリストを必要とします） |
| バッファ制御パラメータの設定 | VOD + Live | Y |
| 可変ビットレートコントロールの設定 | VOD + Live | Y |
| カスタムマニフェストタグ | VOD + Live | Y |
| 遅延オーディオバインディング | VOD + Live | Y |
| 302リダイレクト | VOD + Live | Y |
| オフセットのある再生 | VOD + Live | Y |
| トリック再生 | VOD + Live | Y |
| トリック再生でのスローモーション | VOD + Live | 非対応 |
| スムーズなトリック再生（ABRを使用） | VOD + Live | Y |
| ID3の解析 | VOD + Live | Y |
| 広告のブラックアウト | VOD + Live | 非対応 |
| 即時オン | VOD + Live | 非対応 |
| 不連続マーカのサポート | VOD + Live | Y |
| 302リダイレクトの定着度 | VOD + Live | Y |

| 機能 | コンテンツタイプ | HLS |
|---|---|---|
| 一般的な再生、有効な広告 | VOD + Live | Y |
| 広告が有効なFERコンテンツ | VOD | Y |
| デフォルトの広告動作 | VOD + Live | Y |
| VAST 2.0/3.0 | VOD + Live | Y |
| VMAP 1.0 | VOD + Live | Y |
| MP4広告 | VOD + Live | Y（CRSから） |
| 広告を有効にしたトリック再生 | VOD + Live | Y |
| 広告のみ | VOD | Y |
| ターゲット設定パラメーター | VOD + Live | Y |
| カスタムパラメーター | VOD + Live | Y |
| カスタム広告動作 | VOD + Live | Y |
| カスタム広告タグ | ライブ | Y |
| カスタム広告リゾルバー | VOD + Live | Y |
| フリーホイールカスタム広告リゾルバー | VOD | Y |
| C3 | VOD + Live | 非対応 |
| 遅延広告の解決 | VOD | Y |
| 不連続マーカのサポート — SSAI | VOD + Live | Y |
| コンパニオン広告、バナー広告、クリック可能広告 | VOD + Live | Y |
| VPAID 2.0 | VOD + Live | Y(JS) |
| 早期広告出口 | ライブ | Y |
| ルールベースのクリエイティブの優先順位付け | VOD + Live | Y |
| CRSルール | VOD + Live | Y |
| JSON広告リゾルバー | VOD + Live | 非対応 |
| 堀の統合 | VOD + Live | Y |
| 広告の時間の部分挿入 | ライブ | Y |

| 機能 | コンテンツタイプ | HLS |
|---|---|---|
| AES暗号化 | VOD + Live | Y |
| AES暗号化の例 | VOD + Live | Y |
| トークン化されたストリーム | VOD + Live | Y |
| Widevine DRM | VOD + Live | fMP4コンテナのみ |
| Primetime DRM | VOD + Live | Y |
| 外部再生(RBOP) | VOD + Live | Primetime DRMのみ |
| ライセンスのローテーション | VOD + Live | Primetime DRMのみ |
| キーの回転 | VOD + Live | Primetime DRMのみ |

| 機能 | コンテンツタイプ | HLS |
|---|---|---|
| Adobe Analytics VHLの統合 | VOD + Live | Y |
| 請求 | VOD + Live | Y |

## 解決された問題 {#resolved-issues}

解決が報告された問題に関連付けられている場合、Zendesk参照（ZD#xxxxなど）が表示されます。

**Android TVSDK 3.12**

この節では、TVSDK 3.12 Androidリリースで解決された問題の概要を示します。

* ZD#40584 - Primetime Referenceアプリケーションは、最新バージョンではビルドされません。

### 以前のリリースで解決された問題

**Android TVSDK 3.11**

* ZD#41252 - WebVTT内の韓国語文字が、Android 7.1の後で機能しなくなりました。

**Android TVSDK 3.10**

* ZD#40340 — すべてのTS(TypeScript)ファイルをブラックリストに含めた後に再生を試みると、「App Not Responding」エラーが発生してアプリケーションがクラッシュする。

**Android TVSDK 3.8**

* 新しい雑誌号は追加されませんでした。

**Android TVSDK 3.7**

* 新しい雑誌号は追加されませんでした。

**Android TVSDK 3.6**

* 新しい雑誌号は追加されませんでした。

**バージョン3.5**

* ZD#37503 - CRSルールに対するJSON応答は、重複要求を避けるためにキャッシュされます。

**バージョン3.4**

* ZD#37996 — リニアストリームおよびVOD CMAF HEVCストリームの再生が途切れる問題を修正しました。
* ZD#37706 — 文字化けしたキャプションに関する問題を修正しました。
* ZD#37622 — 特定の広告に対する致命的なURISyntaxErrorsに関する問題を修正しました。
* ZD#36938 — トリック再生を終了した後で、ビットレートを中間のビットレートに切り替え、最も高いビットレートに切り替える問題を修正しました。

**バージョン3.3**

* ZD#37394 - CMAFアセットは、速度が変化した後にアーティファクトを早送りします。
   * トリック再生中にプロファイルの変更が発生する問題を修正しました。
* ZD#37396 — 一部のミッドロールおよびポストロールに広告トラッキングイベントがありません。
   * 広告トラッキングイベントに関する特定のケースを修正しました。
* ZD#37491 — エラーメタを含むHTTPステータスコードが存在しません。
   * スタック内のネットワークエラーの伝播を進めていました。
* ZD#37808 — ホワイトリストの新しいカスタムヘッダー。
   * この修正の一部としてSSAI_TAGのサポートが追加されました。
* ZD#37622 — 特定の広告ポッドからのURI構文エラー。
   * エンコードされていない%を含む広告を顧客のAndroidアプリに配信した場合のストリーム再生のクラッシュに関する問題を修正しました
* ZD#37631 - Android TVSDK用のマスターマニフェストの再試行メカニズム。
   * この機能強化に対処するために、ネットワーク設定に新しいAPIを追加しました。 このAPIを使用しない場合、マニフェストは再試行されません。 この値を使用すると、ネットワークエラーとタイムアウトの処理でマニフェストが再試行されます。

**バージョン3.2**

* ZD#37493 — ライブ再生用のトラッキングビーコンが、シーケンス内の最初の広告で断続的に呼び出されません。
* ZD#36985- VMAP応答の空の広告の時間に対してトラッキングビーコンが送信されません。
* ZD#37134 - TVSDKが、VMAP応答に対して誤ったIDを断続的にスローします。

**バージョン3.0**

* ZD#33740 - TVSDKが、MediaPlayerオブジェクトを作成してreplaceCurrentResource()を呼び出した直後に、不要な警告をスローします。

   * プレイヤーが中断状態の場合にのみrestoreを呼び出すことで、以前の修正を改善しました

* ZD#36442 — 新しい再生が行われるたびに、リモートデバッグセッションが切断され、デバッグができなくなります。

   * デバッグはデフォルトで有効になっていないため、Web表示ーではデフォルトでデバッグはできません。 MediaPlayer.getCustomAdView()から返されたオブジェクトでsetWebContentsDebuggingEnabled(true)を呼び出すことで、必要に応じてアプリケーションがデバッグを有効にする必要があります。

* ZD#33688 — ジャストインタイムのサポートと解決

   * 広告の時間は、広告の時間の位置より前に、指定した間隔で解決されます。

* ZD#36441 — ライブ時間が5分を超えて長くなり続け、複数の問題が発生します。

   * 仮想ライブポイントの計算中にvirtualStartTimeが2回追加され、この問題が発生する問題を修正しました。

**Android TVSDK 2.5.6**

* ZD #34992 — クローズドキャプションの言語が空です。

   * TVSDKが、キャプショントラックの詳細を取得するために、メインマニフェストから#EXT-X-MEDIA:TYPE=CLOSED-CAPTIONSを解析していなかった問題を修正しました。

* ZD #35078 - Android P検証。

   * TVSDK 2.5.6は、最新のAndroid Pベータ版ビルドで検証されています。 新しいAndroid OSが原因で問題は見つかりませんでした。

* ZD #34149 — エラーが発生した場合でも、プレイヤーは引き続き要求を表示します。

   * すべてのプロファイルがダウンした場合（404エラー）も、TVSDKが繰り返し呼び出しを行っていた問題を修正しました。

* ZD #31533 — アプリがバックグラウンドに送信された後、Androidでオーディオを再生します。

   * アプリがバックグラウンドにある場合にオーディオを再生できるように、引数として「True」を指定して（プレイヤーがPREPARED状態の場合）呼び出す必要があるMediaPlayerの `enableAudioPlaybackInBackground` APIを追加しました。

**Android TVSDK 2.5.5**

* ZD #21647 — 実際のビデオサイズが640x360の場合、Android TVSDKは640x368と通知します。

   * 変数m_nOutputHeight （AndroidMCVideoDecoder内）が原因で、実際の出力高さではなくフレーム高さで更新されています。 m_nOutputHeightを正しく計算するために、関数getVideoFrameに関連する変更を行いました。

* ZD #26614 — 緊急、サードパーティの広告提供/プログラム — インプレッションを提供できません。

   * &lt;VAST version =&quot;2.0&quot;>のように「等号」記号の前に「スペース」がある場合に問題が再現される、XML解析での問題の処理により、以前の修正を強化しました。

* ZD #29296 - Android: CRS追加リクエストに対するAdSystemおよびクリエイティブID。

   * 1401および1403のリクエストに、新しいパラメーターとして「AdSystem」および「CreativeId」が追加されました。

* ZD #33062 - CDATAノード下のVAST応答でパイプ文字が発生すると、TVSDKがクラッシュします。

   * NetworkConfigurationクラスのAPI setEncodeUrlForTrackingは、エンコードするURL内の安全でない文字として削除されました

* ZD #33063 - CRSファイル選択ロジックが壊れていました。TVSDKは、CRSリクエストをwebm形式で送信せず、3gppファイルで送信していました。

   * ロジックを修正しました。 webmおよび3gpp形式のメディアファイルを使用する場合、Web用に送信するCRSリクエスト。 また、3gpp形式の両方のメディアファイルを使用する場合、最も高いビットレートの3gppファイルに対してCRSリクエストが送信されます。

* ZD #33125 - VMAP内で特定のDoubleClickタグが使用されると、Androidアプリがクラッシュします。

   * クラッシュが発生しないようにシナリオを修正しました。

* ZD #32256 — ライセンスのローテーションとキーのローテーションに関する問題 — Adobe Access

   * SampleAESコンテンツのDRMメタデータを使用したセグメントの初期化を修正しました。 AES128コンテンツで正常に機能します。

* ZD #33619 — ライブポイントの近くでバッファリング状態に留まって増加するプレイリストコンテンツの高速転送。

   * トリック再生モードでライブポイントを越える場合に、ケースを処理しました。

* ZD #34151 - TimedMetadataオブジェクトが正しくありません。

   * 2つのTimedMetadataイベントが、タイムライン内で同じ時間に属している場合、ランダムな順序で現れていました。 マニフェスト内で元の順序を維持。

* ZD #34189 — 広告の時間の開始をシークする場合に発生します。

   * この問題は、不連続性を使用して繋ぎ合わされるSSAI広告に関するものでした。 その原因は、このような広告の始まりを探すとき、キーフレームを探しても見つからないときの行動でした。 その理由は、広告の最小オーディオタイムスタンプが、最小ビデオタイムスタンプの前にあったためです。 したがって、間違ったfragmentDumpデータでキーフレームを検索することになります。 修正されました。

* ZD #34528 - FireTV 3rd genドングルの640 x 360以上のビデオ解像度はアップグレードできません。

   * 最新のファームウェアの更新を含む修正が強化されました

* ZD #34793 - VideoEngineでauditudeSettingsが使用可能であり、使用されていないと想定していた場合に、カスタムコンテンツリゾルバーでクラッシュするために使用されるTVSDK 2.5.x。

   * Null共有ポインタ(auditudeSettings)に対する関数呼び出しが原因でクラッシュが発生していました。 VideoEngineTimeline::placeToSourceTimeline()に条件付きチェックを追加し、そのオブジェクトに対する何も呼び出す前にauditudeSettingsが使用可能であることを確認しました。

* ZD #32584 - VAST応答の&lt;拡張子>ノードにある完全な情報にアクセスできません。

   * XML解析に関する問題を修正し、現在NetworkAdInfoでは、&lt;拡張子>ノードに存在する完全な情報が提供されます

* ZD #35086 — 特定のVMAP応答の場合、プレーヤーから拡張データを完全に取得できません。

   * 拡張XMLの属性値内に重複引用符が含まれている場合、XMLの解析が機能しなかったため、拡張XMLに固有の問題でした。 問題を修正しました。

**Android TVSDK 2.5.4**

* ZenDesk#33659 - Webビューのリモートデバッグを有効にする再生セッション。

WebViewDebuggingはデフォルトでFalseに設定されています。 デバッグを有効にするには、setWebContentsDebuggingEnabled(true)を使用して、アプリケーションを介してtrueに設定します。

* ZenDesk#33011 - CRS要求が失敗した場合、広告タイムラインは解決されません。

   広告に対するCRSリクエストが失敗すると、タイムラインが解決され、残りの広告が再生されます。

* ZenDesk#34528 - FireTV第3世代ドングルのビデオ解像度が640 x 360以上にアップグレードされない。

   ビデオ解像度はビットレートスイッチとして切り替わります。

* ZenDesk#33192 - AudioUpdatedEventListener::onAudioUpdatedを使用してトラックを取得すると、AudioTrackにNULLの名前が付けられます。

   FireTV Stickのいくつかのシナリオでは、実際のオーディオ更新がない場合にonAudioUpdateイベントが発生していました。 この問題は修正されました。

**Android TVSDK 2.5.3**

* Zendesk#32216 - TimedMetadataカスタムタグ購読が機能しません。

   1.4では文字列を返すのに対して、ID3データをバイト配列（APICまたは汎用データをサポート）としてクライアントに返します。 バイト配列は、ヌル終了文字自体を処理しないので、クライアントに特殊文字を表示していました。 この問題は修正されました。
* Zendesk#32670 — プレイヤーが冗長プレイリストにフェイルオーバーしない

   これは正常に動作するようになり、setNetworkDownVerificationUrlは期待どおりに動作します。
* Zendesk#32369 — クローズドキャプションに、異なる色のガベージまたは加工品が表示されます。

   最新のビルドで、CCの問題が修正されました
* Zendesk#25590 - Enhance: TVSDKのCookieストア（C++からJAVA）

   Android TVSDKは、（AndroidアプリケーションのCookieStoreに保存される）JAVAレイヤーとC++ TVSDKレイヤーの間のcookieへのアクセスをサポートするようになりました。
* Zendesk#32252 - TVSDK_Android_2.5.2.12には、PTPLAY-20269の修正がないようです。

   この問題は修正され、2.5.2ブランチに統合されました。
* Zendesk#31806 - PREPARINGでオーディチュードが表示されます。

   応答xmlに空のタグが含まれていたので、プレイヤーは「準備中」の状態で停止していました。 問題が修正されました。
* Zendesk#31727 - TVSDK 2.5のクローズドキャプション文字がドロップされるか、スペルミスになる。

   問題が修正され、どの文字もスペルを落としたりスペルを間違えたりすることはありません。
* Zendesk#31485 - DrmManager 2.5（日本未発売）

   新しいDrmManager（コンテキストコンテキスト）を使用したDrmManagerの作成で問題が発生しました。 DRMManagerを提供するDRMServiceクラスを実装しました。
* Zendesk#32794- 1080P解像度ストリームがAndroidで再生されない

   2.5では、SizeAvailableEventメソッドとPreviouslyメソッドが変更され、フレームの高さとフレームの幅を返すために使用されるSizeAvailableEventのgetHeight()メソッドとgetWidth()メソッドが変更されました。これはメディア形式で返されます。 デコーダーが返す出力の高さと出力の幅を返すようになりました。
* Zendesk #19359セットレベルマニフェスト内での#EXT-X-FAXS-CM属性の位置が原因でFlash Playerがクラッシュする。

   #EXT-X-FAXS-CMタグは、個々のビットレートまたはセグメントがプレイリストに表示される前に、常に最上位のプレイリストに表示される必要があります。

**Android TVSDK 2.5.2**

* Zendesk#17305背景が不透明でないクローズドキャプションのアーティファクト。

   TextFormatのsetTreatSpaceAsAlphaNumプロパティが公開されます。 デフォルトでは、このプロパティはFalseです。 クライアントでこのプロパティをTrueに設定すると、暗い領域の問題が解決します。

* Zendesk#25097 CCディスプレイには、CC設定で視覚的なアーティファクトが表示されます。

   TextFormatのsetTreatSpaceAsAlphaNumプロパティが公開されます。 デフォルトでは、このプロパティはFalseです。 クライアントでこのプロパティをTrueに設定すると、暗い領域の問題が解決します。

* Zendesk #31620 TVSDKプレイヤーから出るユーザーエージェント文字列が切り捨てられます。

   ユーザーエージェント文字列は、128文字以降で切り捨てられなくなります。

   Adobe Primetimeバージョン文字列がシステムユーザーエージェントに追加されます。

* Zendesk #30809 SEEK_ENDイベントが見つからないため、アプリは再生中の状態に移行できません。
* Zendesk #30415クローズドキャプションの「シアン」カラーが、以前のPrimetime TVSDKリリースと比較して、より濃い青（青緑色）になりました。

   色がDarkCyanからCyanに変更されます。

* Zendesk #30727 VOD広告がダウンロード/解決されていません。

   VMAP XMLで、明示的な終了タグ(‘&lt;/VAST>&#39;)のない空のVASTタグがあり、その後に改行文字がない場合、VMAP XMLは正しく解析されず、広告が再生されない場合があります。

**Android TVSDK 2.5.1**

* デバイス固有(Samsung Galaxy Tab 4)のクラッシュ。 AuditudeのVOD DRM LBAを使用し、広告をクリックします。
* VHL — オフセットからコンテンツを開始する際に、正しくないハートビート呼び出しが送信されます。
* VPAID広告が再生されるとき、イベント:type:play広告に対するVHLハートビート呼び出しが見つかりません。
* プレイヤーは、完了ステータスになった後、ポストロール広告に対してはSKIP adBreakPolicyを使用してPLAYINGステータスに戻ります。
* Cookieが送信広告コールバックに添付されていません。
* 広告キューポイントは表示されません。
* EAC3 SAPトラックが別々に割り当てられたHLSが読み込まれません。
* メディアプレイヤーが復元された後に、TVSDKが画面オンインテントを受け取ると、プレイヤーがクラッシュする。

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

* ID3、クローズドキャプション、遅延バインディングオーディオのサポートは、CMAF(CBC)ストリームに対して検証されていません。
* 一部のデバイスでは、CMAFストリームでのトリック再生中にビデオの歪みが上部に表示されることが原因で、再現性の低い問題が発生します。

**Android TVSDK 3.3**

* clcp:c608キャプションは、CMAFストリーム再生ではサポートされていません。

**Android TVSDK 3.2**

* TVSDK 3.2は、CMAFサンプルAESおよびAES128ストリーム再生をサポートしていません。
* HEVC CMAFストリームには、クローズドキャプション再生のサポートは含まれません。
* 非暗号化セグメントの周りでシークが実行されると、WV暗号化ストリームに緑色の色が表示されます。
* CMAFストリームはID3イベントをサポートしません。
* HLSストリームは、HTMLキャプション形式をサポートしていません。

**Android TVSDK 3.0**

* HEVCのサポートには、このリリースで次の制限があります

   * DRMはサポートされていません
   * CC(CEA 608/708)のサポートは確認されていません
   * 4Kのサポートはまだ存在しません
   * ID3タグのサポートが検証されていません

* 広告の進行状況イベントの場合、タイムラインバーに100%正確な広告再生時間が反映されない場合があります。 回避策として、広告の再生の完了を知り、タイムラインバー `adcompleteevent` の更新、広告に関連するUIの削除など、様々な目的でUIを更新できます。
* VMAPから返される広告呼び出しは、ジャストインタイムルックアヘッド位置を受け入れません。

**Android TVSDK 2.5.6**

* 複数のVMAP広告の時間が同時にサポートされません。

**Android TVSDK 2.5.3**

このバージョンには次の問題があります。

* ライブビデオ再生時に、ローエンドデバイスでオーディオビデオの同期の問題が発生したり、ネットワークの状態が低下したりする場合があります。
* FERストリームの場合、virtualTimeとlocalTimeは異なる場合があります。 また、オフセット付きのFERは機能しません。
* 遅延バインディングオーディオのコンテンツがシークされると、再生が停止する場合があります。
* WebVTTのキャプションが断続的に、LIVEコンテンツで同期されない場合があります。
* 断続的に、広告の時間から外れた後に、少数のフレームの高速再生が見られる場合があります。
* 広告が再生されているにもかかわらず、303エラーが3つのラッパー広告の時間に発生することがあります。

**Android TVSDK 2.5.2**

このバージョンには次の問題があります。

* ライブビデオ再生で、ローエンドデバイスでのオーディオビデオの同期の問題が発生する場合があります。
* VODメディアの終わりまでシークすると、再生が停止する場合があります。
* FERストリームの場合、virtualTimeとlocalTimeは異なる場合があります。 また、オフセット付きのFERは機能しません。

**Android TVSDK 2.5.1**

このバージョンのTVSDKには、次の問題があります。

* ライブビデオ再生で、ローエンドデバイスでオーディオビデオの同期の問題が発生する場合があります。
* FERストリームの場合、virtualTimeとlocalTimeは異なる場合があります。 また、オフセット付きのFERは機能しません。
* VMAP XMLで、明示的な終了タグ(&lt;/VAST>)のない空のVASTタグがあり、その後に改行がない場合、VMAP XMLは正しく解析されず、広告が再生されない場合があります。
* VPAIDポストロールはサポートされていません。

## 役立つリソース {#helpful-resources}

* [必要システム構成](https://docs.adobe.com/content/help/en/primetime/programming/tvsdk-3x-android-prog/introduction/android-3x-requirements.html)
* [Android向けTVSDK 3.10プログラマーガイド](https://docs.adobe.com/content/help/en/primetime/programming/tvsdk-3x-android-prog/introduction/android-3x-overview-prod-audience-guide.html)
* [APIリファレンス用のTVSDK Android Javadoc](https://help.adobe.com/en_US/primetime/api/psdk/javadoc3.5/index.html)
* [TVSDK Android C++ APIドキュメント](https://help.adobe.com/en_US/primetime/api/psdk/cpp_3.5/namespaces.html) — 各Javaクラスには対応するC++クラスがあり、C++ドキュメントにはJavadocsよりも詳しい説明が記載されています。Java APIについて詳しくは、C++のドキュメントを参照してください。
* [Android向けTVSDK 1.4から2.5(Java)への移行ガイド](https://helpx.adobe.com/primetime/migration-guides/tvsdk-14-25-android.html)
* 画面のオン/オフシナリオの処理については、ビルドに含まれる `Application_Changes_for_Screen_On_Off.pdf` ファイルを参照してください。
* Adobe Primetimeのラーニングとサポートの [ページで、完全なヘルプドキュメントを参照してください](https://helpx.adobe.com/support/primetime.html) 。
