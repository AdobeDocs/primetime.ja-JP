---
title: Android 向け TVSDK 1.4 リリースノート
description: TVSDK 1.4 for Android リリースノートでは、 TVSDK Android 1.4 の新機能や変更点、解決された既知の問題、およびデバイスの問題について説明します。
contentOwner: asgupta
products: SG_PRIMETIME
topic-tags: release-notes
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '7802'
ht-degree: 0%

---

# Android 向け TVSDK 1.4 リリースノート {#tvsdk-for-android-release-notes}

TVSDK 1.4 for Android リリースノートでは、 TVSDK Android 1.4 の新機能や変更点、解決された既知の問題、およびデバイスの問題について説明します。

## 新機能 {#new-features}

**バージョン 1.4.43**

**HTTPS を介したセキュアな広告読み込み**

Adobe Primetimeには、Primetime 広告サーバーへの最初の呼び出しと、CRS over HTTPS をリクエストするオプションが用意されています。

**MediaPlayer クラスの alwaysUseAudioOutputLatency(boolean val)**

このパラメーターを設定した場合、オーディオタイムスタンプの計算でオーディオ出力待ち時間を使用します。

ブール型のパラメーター val を受け付けます。 値が `True`を指定しない場合、クライアントはオーディオ出力遅延をオーディオタイムスタンプの計算に使用します。

**バージョン 1.4.42**

**部分的な広告ブレーク挿入：**
部分的に視聴された広告のトラッキングを実行せずに、広告の途中で参加する TV のようなエクスペリエンス。
例：3 つの 30 秒の広告で構成される 90 秒の広告ブレークの途中（40 秒）にユーザーが結合します。 ブレークの 2 番目の広告から 10 秒経過します。
* 2 番目の広告は、残りの期間（20 秒）に続いて 3 番目の広告を再生します。
* 部分的な広告再生（2 番目の広告）の広告トラッカーは起動されません。 3 番目の広告のトラッカーのみが実行されます。

**バージョン 1.4.41**

新機能はありません。

**バージョン 1.4.40**

新機能はありません。

>[!NOTE]
>
>1.4.39 より前のバージョンを使用している場合、API の変更は必要ありません。

**バージョン 1.4.39**

* TVSDK は、VHL 2.0.1 および Nielsen を使用した VHL 2.0.1 で認定されています。
* Android TVSDK が更新され、新しい Akamai ホストから CRS リクエストをおこなえるようになりました。 `primetime-a.akamaihd.net`.
* 新しいホスト名設定では、HTTP と HTTPS(SSL) の両方を介した CRS アセット配信がより大規模に提供されます。
* TVSDK は、Android Oreo リリースをサポートしています。
* に新しい関数が追加されました。 `AdClientFactory` 複数のオポチュニティディテクターの登録をサポートするクラス：

  ```
  public List<PlacementOpportunityDetector> createOpportunityDetectors(MediaPlayerItem item);
  ```

  これは、PlacementOpportunityDetector の配列を返す必要があります。 これで、複数のオポチュニティディテクターを登録できます。 例えば、早期広告出口機能の場合、2 つのオポチュニティディテクターが必要でした。1 つは広告挿入用、もう 1 つは広告からの早期出口用です。 この新しい関数は、独自の AdvertisingFactory を実装している（DefaultAdvertisingfactory を使用していない）場合にのみ、影響を与えるように実装する必要があります。 既存の動作を取得するには、 createOpportunityDetector() 関数と同様に 1 つのオポチュニティディテクターを作成し、配列に格納して返す必要があります。

  ```
  public class MyAdvertisingFactory extends AdvertisingFactory {  
  …  
  @Override  
  public List&lt;PlacementOpportunityDetector&gt; createOpportunityDetectors(MediaPlayerItem mediaPlayerItem) {  
  List&lt;PlacementOpportunityDetector&gt; opportunityDetectors = new ArrayList&lt;PlacementOpportunityDetector&gt;();  
  opportunityDetectors.add(createOpportunityDetector(mediaPlayerItem));  
  return opportunityDetectors;  
  } }
  ```

>[!NOTE]
>
>1.4.39 より前のバージョンを使用している場合、API の変更は必要ありません。

**バージョン 1.4.36**

Android での Content Skip のバグ修正。

**バージョン 1.4.35**

* **ネットワーク広告情報**

  TVSDK API が、サードパーティの VAST 応答に関する追加情報を提供するようになりました。 広告 ID、Ad System、VAST Ad Extensions は、広告アセットの networkAdInfo プロパティを通じてアクセスできる NetworkAdInfo クラスで提供されます。 この情報は、他の Ad Analytics プラットフォーム ( **堀の分析**.

**バージョン 1.4.31**

**CRS 広告のマルチ CDN サポート**
* デフォルトでは、すべてのトランスコードされたアセットは、Akamai 上のAdobe所有の CDN でホストされます。 最新リリースのAdobeクリエイティブ再パッケージ化サービス (CRS) では、トランスコードされたクリエイティブを、お客様が指定した複数の CDN にアップロードできます。
* 新しい API が TVSDK に追加され、デフォルト URL が使用されていない場合に最終的な CRS クリエイティブ URL を指定できるようになりました。 これらの新しい API の使用方法については、ドキュメントを参照してください。

**バージョン 1.4.18**
Primetime Android TVSDK で、VPAID 2.0 Javascript クリエイティブがサポートされ、リッチなインタラクティブなインストリーム広告エクスペリエンスが可能になりました。 VPAID 2.0 の詳細については、 [VPAID 広告のサポート](../programming/tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/vpaid-ads/android-3x-vpaid-ads.md).

**バージョン 1.4.17**

AC-3 5.1 は、Amazon FireTV でのみサポートされています。

**バージョン 1.4.11**

* **広告フォールバック、広告選択ロジックのデイジーチェイン (Zendesk #3103** フォールバックルールが有効になっている VAST 広告（クリエイティブ）の場合、 TVSDK は無効な MIME タイプを持つ広告を空の広告として扱い、その代わりにフォールバック広告を使用しようとします。 フォールバック動作のいくつかの側面を設定できます。

詳しくは、 [VAST および VMAP 広告の広告フォールバック](../programming/tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/ad-fallback/android-3x-ad-fallback.md).

* **ビデオハートビートライブラリ (VHL) がバージョン 1.5 に更新されました。**
   * ビデオ開始やビデオ/広告/チャプター開始をコンテキストデータとして使用し、メタデータを送信する機能
   * ネットワークトラフィックの削減 — ハートビートは、平均的に少なく、サイズも小さくなります

**バージョン 1.4.7**

* **オンプレミスの個別化のサポート**&#x200B;別のエンドポイントに移動するためのクライアントの個別化リクエストをカスタマイズするAdobeの個別化サーバーのオンプレミスインストールのサポート。

**バージョン 1.4.6**

* **サンプル AES 暗号化 (Flash Playerバージョン 17.0.0.134 が必要 )**サンプルベースの AES 暗号化がサポートされるようになりました。

**バージョン 1.4.2**

* **ビデオハートビートライブラリ (VHL) をバージョン 1.4.0.1 に更新しました。**

   * Adobe Analytics Video Essentials に、他の SDK やプレーヤーから様々な Analytics ユースケースをバンドルする機能が追加されました。
   * trackAdBreakStart メソッドと trackAdBreakComplete メソッドを削除することで、広告トラッキングを最適化しました。 広告ブレークは、 trackAdStart および trackAdComplete メソッドの呼び出しから推論されます。
   * 広告を追跡する際に、再生ヘッドプロパティは不要になりました。

* **Nielsen SDK の統合** TVSDK で、カスタム統合をおこなわずに Nielsen SDK へのユーザートラッキング情報の送信がサポートされるようになりました。

**バージョン 1.4.0**

* **代替コンテンツ置換によるブラックアウトシグナリング** TVSDK は、1.4 の TVSDK の更新の一環として、リニアコンテンツに対する地域ブラックアウトへの切り替えとリピートをサポートするようになりました。 TVSDK は、2 つのマニフェストファイルを並行して、メインと代替で処理できるようになり、元のプログラミングの代わりに代替プログラミングが表示されている場合でも、ブラックアウト信号を監視できます。

* **C3 広告の削除/置換** 現在は、C3 ウィンドウから出てくる Video-on-demand(VOD) アセットに新しい広告を動的に挿入するための準備作業は追加で必要ありません。 TVSDK は、カスタムコンテンツ範囲を削除し、新しい広告を動的に挿入する API を提供するようになりました。 この強力な新機能は、放送中にライブ/リニアコンテンツの放送が発生し、アセットを「クリーンアップ」する適切な時間をかけずに、オンデマンドコンテンツとして即座にプルダウンして使用する場合にも便利です。

* インターフェイス PlaybackEventListener には、新しいイベントをリッスンするために使用できる onReplaceMediaPlayerItem という新しいメソッドがあります。 `ITEM_REPLACED`. このイベントは、MediaPlayeritem インスタンスが MediaPlayer で置き換えられるたびにディスパッチされます。 この PlaybackEventListener を実装するクライアントアプリケーションは、この新しいメソッドを実装するか、上書きする必要があります。
* AdClientFactory には、複数のオポチュニティディテクターを登録するための新しい関数がクラスに追加されました。

  ```
  public List&lt;PlacementOpportunityDetector&gt; createOpportunityDetectors(MediaPlayerItem item);
  
  For example for early ad exit feature, you need two Opportunity Detectors - one for ad insertion and another for  early  exit from  `ad`.
  
  To override this new function create a single Opportunity Detector, and put into an array and return:
  
  @Override
  
  public List&lt;PlacementOpportunityDetector&gt; createOpportunityDetectors(MediaPlayerItem mediaPlayerItem) {
  
  List&lt;PlacementOpportunityDetector&gt; opportunityDetectors = new ArrayList&lt;PlacementOpportunityDetector&gt;();
  
  opportunityDetectors.add(createOpportunityDetector(mediaPlayerItem));
  
  return opportunityDetectors;
  }
  
  }
  ```

## TVSDK 1.4 の変更点 {#tvsdk-changes}

* インターフェイス PlaybackEventListener には、新しいイベント ITEM_REPLACED をリッスンするために使用できる onReplaceMediaPlayerItem という新しいメソッドがあります。 このイベントは、MediaPlayeritem インスタンスが MediaPlayer で置き換えられるたびにディスパッチされます。 この PlaybackEventListener を実装するクライアントアプリケーションは、この新しいメソッドを実装するか、上書きする必要があります。

* AdClientFactory には、複数のオポチュニティディテクターを登録するための新しい関数がクラスに追加されました。

```
public List`<PlacementOpportunityDetector>` createOpportunityDetectors(MediaPlayerItem item);
```

例えば、早期広告出口機能の場合、2 つのオポチュニティディテクターが必要です。1 つは広告挿入用、もう 1 つは広告から早期に出口するためです。

この新しい関数を上書きするには、単一のオポチュニティディテクターを作成し、配列に配置してを返します。

```
@Override

public List`<PlacementOpportunityDetector>` createOpportunityDetectors(MediaPlayerItem mediaPlayerItem) {

List`<PlacementOpportunityDetector>` opportunityDetectors = new ArrayList`<PlacementOpportunityDetector>`();

opportunityDetectors.add(createOpportunityDetector(mediaPlayerItem));

return opportunityDetectors;

}

}
```

## 1.4 でのデバイス認定とサポート {#device-certification-and-support-in}

>[!NOTE]
>
>次の機能があります。 **not** TVSDK でサポートされます。
>
>* どのプラットフォームやバージョンでも、スローモーション。
>* ライブトリック再生。

**バージョン 1.4.43**

TVSDK 1.4.43 は、Android 6.0.1/7.0 および 8.1(Oreo) の Android デバイスで認定されています。

* **バージョン 1.4.23:**

   * TVSDK 1.4.23 は、Android N を搭載した Android デバイス向けに認定されています。

* **バージョン 1.4.18:**

   * Primetime は、Amazon Fire TV の認定を受けています。
   * VPAID 2.0 は、Android 4.0 以降を搭載したデバイスでのみサポートされます。

## 1.4 で解決された問題 {#resolved-issues-in}

>[!NOTE]
>
>CRS を使用するすべての TVSDK ユーザーは、iOSおよび Android で TVSDK 1.4.39（最新）にアップグレードすることを強くお勧めします。 このアップグレードは、既存のアプリケーション実装に代わるものです。 アップグレード後、プロキシツール（Charles など）で CRS クリエイティブ URL リクエストをチェックして、パス内のバージョンがバージョン 3.1 を反映していることを確認します。例：
>
>`https://primetime-a.akamaihd.net/assets/3p/v3.1/222000/167/d77/ 167d775d00cbf7fd224b112sf5a4bc7d_0e34cd3ca5177fbc74d66d784bf3586d.m3u8`

**バージョン 1.4.43**

* チケット#27143 - FireTV デバイスで 5.1 オーディオトラックを再生できません

   * TVSDK が FireTV デバイスで AC3 オーディオを再生できるようになりました。 再生は常にステレオです。

* チケット#33902 - HTTPS 経由でのセキュアな広告配信

   * Adobe Primetimeには、primetime 広告サーバーおよび CRS over https への最初の呼び出しをリクエストするオプションが用意されています。

* チケット#34493 - Bluetooth オーディオ遅延

   * 追加済み `alwaysUseAudioOutputLatency` MediaPlayer クラスで設定すると、オーディオタイムスタンプの計算にオーディオ出力待ち時間を使用します。

* チケット#34949 — ビデオハートビートライブラリ (VHL) の新しいバージョンが統合されました。

**バージョン 1.4.42 (1791)**

* Zendesk #33719: FireTV 4k アダプティブビットレートのスケールが遅くなります。 FireTV 4K デバイス用の ABR のサポートを追加しました。
* Zendesk #33338: resetDRM を実行すると、アプリケーションのすべてのデータが消去されます。  非 TVSDK スレッドでの例外が原因で TVSDK 操作キューがいっぱいになる追加のケースを処理しました。

**バージョン 1.4.41 (1776)**

* Zendesk #33002 - Fire TV の TVSDK からのコンパニオンアセットデータ。 コンパニオンデータをリストとして返す新しいクラス AdBannerAsset を実装しました。 &lt;adbannerasset> と AdAsset::id は、長さではなく文字列になりました。
* Zendesk #32821 - Android Primetime プレーヤーは、WWE 用のプレゼンテーションタイムスタンプ (PTS) を検出するとフリーズします。 この問題は、このリリースで修正されました。
* Zendesk #33572 - VideoAnalyticsProvider 広告開始がクラッシュする。 VideoHeartbeat.jar の VHL と Nielsen 結合 SDK バージョンの適切な組み合わせを使用して、この問題を修正しました。
* Zendesk #33355 - Fire TV: 15 秒の問題を取り戻します。 TVSDK 側およびお客様からの修正は、エンドパーティおよびサードパーティで検証されていません。

**バージョン 1.4.40 (1764)**

* Zendesk #33068 — 新しいデバイスでのAmazonのリップ同期の問題。 リップ同期の問題は、このリリースで修正されました。
* Zendesk #32215 - Android TVSDK 1.4.38 セキュリティの問題 `[Hotlist]`. 最新の OpenSSL-1.1.0 および curl-7.55.1に更新しました。
* Zendesk #32920 — 広告ブレーク内の空白の画面で、広告ブレークが完了しない。 VPAID コンテナがハング状態になり、Facebook VPAID 広告が 1 つの\&amp;lt;AdParameters\&amp;gt; VAST ノードで複数の CDATA ブロックを返すことが多い問題を修正しました。

**バージョン 1.4.39 (1744)**

* Zendesk #28976 — ライセンスリクエストに 1 秒以上かかります。 POSTを使用する DRM ライセンスリクエストの呼び出しが実行されている間、Curl は余分な「Expect: 100-continue」ヘッダーを追加します。 TVSDK の「Expect:」ヘッダーを削除しました。
* Zendesk #27707 - CSAI 環境は、早期に戻る、またはコンテンツに戻るための CUE IN マーカーを遵守していません。 複数のオポチュニティジェネレーターのサポートを提供。

**バージョン 1.4.38 (1722)**

* Zendesk #21590 — 最新のオリジンビルドでのビデオパフォーマンスと追跡

TVSDK で VHL 2.0 を統合および認定し、API の複雑さを減らすことで、VideoHeartbeatsLibrary 実装のバリアを減らします。

* Zendesk #29688 - Android O Beta のお客様向けのサポート。

新しい Android ベータ版リリースの TVSDK のサポート。

**バージョン 1.4.36 (1713)**

* Zendesk #27392 - Android でのコンテンツスキップ

復号化に対応するために、Android TVSDK は、iframe 以外のコンテンツのバイト範囲を誤って 16 バイト拡大していました。 Iframe ストリームには拡幅区間が必要ですが、非 iframe ストリームには必要ありません。

**バージョン 1.4.34 (1702)**

* Zendesk #27638 - cURL INet オブジェクトでのリーク

Posix cURL INet オブジェクトは、cURL 接続で使用された共有マネージャと DNS キャッシュを保持している間に漏れ出していました。

この問題は、INet デスコンストラクタから Posix cURL INet オブジェクトを削除することで解決されました。

**バージョン 1.4.33 (1694)**

* **OpenSSL ライブラリ**

OpenSSL ライブラリが OpenSSL バージョン 1.0.2j で更新されました。

* Zendesk #21701 — 正規化された URL ではなく、1401 CRS リクエストの元のクリエイティブ URL を送信します。
この問題は、元のクリエイティブ URL を送信することで解決されます。

* Zendesk #25023 — 長時間ビデオ再生：ビデオのフリーズ、画面のちらつきこの問題は、CenturyLink のセットトップボックスデバイスの最大ビデオ形式のサイズを設定することで解決されました。

* Zendesk #27460 — 新しい Akamai アカウントがPOSTcdn リクエストを処理できません。
コードを更新して `cdn.auditude.com` 広告リクエストをPOSTではなくGETにする。

* Zendesk #28245 — アプリがバックグラウンドからフォアグラウンドに移行した場合、再生状態が正しく通知されません。この問題は、アプリケーションがフォアグラウンドに戻ったときに再生状態を正しく復元することで解決されました。

**バージョン 1.4.32 (1682)**

* Zendesk #25779 - WebView で JavaScript が有効になっている場合、 TVSDK Android 4.2 以降で検出されたセキュリティ脆弱性には、セキュリティ脆弱性があります。 OS 4.2 以前を実行しているデバイスでは、 TVSDK による WebView の使用が無効になっています。 これにより、これらのデバイスでの TVSDK での VPAID 広告の使用が無効になります。

* Zendesk #26890 - SCREEN 状態（オン/オフ）での問題の処理参照。 プレーヤーAdobeビデオエンジン (AVE) が SUSPENDED 状態から再開されても、DefaultMediaPlayer はそのステータスを更新しません。 その結果、AVE が PLAYING 状態になっている場合でも、DefaultMediaPlayer は SUSPENDED 状態のままになります。 この問題は、DefaultMediaPlayer の現在のステータスが SUSPENDED であっても、AVE から PLAY ステータスを受け取ったときに、 DefaultMediaPlayer の状態を PLAYING に設定することで解決されました。

**バージョン 1.4.31 (1675)**

* Zendesk #21974 - null オブジェクトによる例外
   * AdIndex が null の場合、ほとんど増加しません。 これは、プリロール adBreak に対して受け取った API 呼び出しが正しくないためです。 このような例外を避けるために、データタイプを修正しました。

* Zendesk #24714 — 不要なログをオフにする
   * TVSDK が更新され、不要なログをオフにしました。

* Zendesk #24488 - Fire TV での AV 同期の問題
   * AV デコーダースレッドの処理を改善して修正しました。 特に、入力または出力フレームのキューが変更されるたびに、フレームのコンテンツタイプに固有のデコーダースレッドが実行されます。

* Zendesk #26551 - CRS エラーを修正します。
   * リクエストがHEAD(http head) の場合、コンテンツは空なので、コンテンツを読み取る必要はありません。 読んでも構いませんが、古い Android(4.0.x) は、read() を呼び出すとハングし、新しい Android は read() を呼び出すと正しい値 (-1) を返します。 これに基づいて、「head」のコンテンツを読まないようにコードを変更しました。

* TrickPlayManager にアクセスする際の Zendesk #26696 Null Pointer 例外
   * TrickPlayManager オブジェクトを使用する前に Null でないかどうかを確認することで修正しました。

**バージョン 1.4.30 (1659)**

* Zendesk #22675 Asset duration does not get updated for Live/Linear streams この問題は、ライブストリームおよびリニアストリームのアセットデュレーションを提供する新しい API、assetDuration を PTVideoAnalyticsTrackingMetadata に提供することで解決されました。

* チャネル切り替え時の Zendesk #25853 TVSDK のメモリリーク MediaPlayer のリセット時またはダウンロード時にリリースされた時にファイル読み取りバッファリークが発生する問題が解決されました。

**バージョン 1.4.29 (1653)**

* Zendesk #21200 — アプリがバックグラウンドにあると、休止状態から回復しません。ストリームの切り替えが通知された後にプレーヤーが停止した場合、解決により、プレーヤーは、以前の位置に戻す代わりに、休止状態からストリームの切り替えを実行できます。

* Zendesk #23412 — 広告の時間の最後の 3 秒以内に広告をクリックした場合、プレーヤーは黒いボックスで動かなくなります。この問題は、Zendesk #21200と同じ問題です。

* Zendesk #23616 - Skipped ad break seeks to of future 広告挿入タイプ（挿入/置換）に応じて、 TVSDK は広告の時間の終了ポイントを決定するために、広告期間を計算で使用するかどうかを決定します。

* Zendesk #25078 - TVSDK DRM Android TV STB でのメモリリーク DRM アダプタオブジェクトのメモリリークが見つかり、修正されました。

* Zendesk #25067 - Crash in VideoEngineTimeline これは、オブジェクトが正しくクリーンアップされず、オブジェクトが破棄された後にイベントが呼び出されたために起こっています。 この問題は、null 例外を防ぐためのチェックを追加することで解決されました。

* Zendesk #25352 - Set custom HTTP header この問題は、TVSDK 上の許可リストに新しいカスタムヘッダーを追加することで解決されました。

* Zendesk #25617 - Live stream PTS rollover 引き起こすプレーヤーの不連続性とメモリクラッシュこの問題は、セグメントの途中でロールオーバーが発生した場合に FragmentedHTTPStreamer で PTS ロールオーバー処理を追加することで解決されました。

**バージョン 1.4.28 (1637)**

* Zendesk #23618 — 広告ポリシーが問い合わせられる前に発生する広告ブレークイベントこの問題は、adLoxype が原因で広告がスキップされた場合に AD_BREAK_START および AD_START イベントが発生しないことで解決されました。 代わりに、 AD_BREAK_SKIPPED イベントが送信されます。

**バージョン 1.4.27 (1631)**

* Zendesk #23174 — ビデオのサイズ変更時のパフォーマンスの問題この問題は、TVSDK が MediaPlayerView から SurfaceHolder.setFixedSize() にアクセスできる新しい API MediaPlayerView.setSurfaceFixedSize を提供することで解決されました。

* Zendesk #24450 - TVSDK が重複広告リクエストを行うこの問題は、経過時間が 2 倍ではなく長い時間に変換されたときに発生し、この問題が修正されました。

**バージョン 1.4.26 (1627)**

* Zendesk #21436 - OpenSSL ライブラリをバージョン 1.0.2h に更新 OpenSSL ライブラリを OpenSSL バージョン 1.0.2h に更新しました。
* Zendesk #23825 - Cookie がコールバックに含まれていません Android Cookie のサポートを提供することで修正されました。

**バージョン 1.4.25 (1620)**

* Zendesk #22900 - Live Adobe Primetime DRM ストリームが Android リファレンスプレーヤーで再生されないメモリ割り当ての問題が修正されました。
* Zendesk #23176 - VPAID 広告を再生しようとするとアプリケーションがクラッシュします。VPAID 広告をレンダリングするカスタム広告ビューを作成しないので、クラッシュが発生しました。 この問題は、カスタム広告ビューがない場合に広告サーバー応答の VPAID 広告を無視することで解決されました。

* Zendesk #23153 - SampleAES DRM Stream - TVSDK Reference Player での再生停止この問題は Zendesk #22900と同じです。

**バージョン 1.4.24 (1612)**

* Zendesk #20784 - Analytics：ライブビデオトランジションのコンテンツ完了をトリガーこの問題は、ライブ/リニアビデオトラッキングセッション中にコンテンツの完了を手動でトリガーする API(trackVideoComplete) を追加することで解決されました。

* placeAdBreak/acceptAd 操作中に Zendesk #21977 VideoEngineTimeline がクラッシュする
   * この問題では、次のライブラリが更新されました。
      * AdobeMobile ライブラリからバージョン4.10.0へ
      * VHL ライブラリからバージョン 1.5.6 へ
      * VHL-Nielsen ライブラリからバージョン 1.6.7 へ

この問題は、許可された広告リストに広告を追加する前に null チェックを追加することで解決されました。

* Zendesk #22313 Amilogic チップセットを搭載した STB のビットレートは 1.2M を超えていませんこの問題は、メディアコーデック機能をプリロードし、Amilogic チップセットデバイスのシームレススイッチを無効にすることで解決されました。

* Zendesk #19520サンプル AES HLS アセットが TVSDK プレーヤーで再生されないこの問題は、サンプル AES で暗号化された HLS ストリームに対して複数の PMT 記述子を処理することで解決されました。

**バージョン 1.4.23 (1602)**

* Zendesk #18852 - CRS ルールに基づいてクリエイティブの選択ロジックを更新この問題は、クリエイティブの選択優先度を指定する JSON 設定ファイルを追加することで解決されました。

* Zendesk #20861 - Android N このリリースでは、Android N 上で動作するアプリケーションからアクセスできなくなった Android プラットフォームネイティブライブラリを直接使用する機能が削除され、Android N のサポートが提供されます。

* Zendesk #21018 - Android N クラッシュ ZD# 20861と同じ解像度。

* Zendesk #21266 - VideoEngineAdapter が Invalid_Key エラーでクラッシュする Invalid_Key エラーには AVE からの説明が含まれていないので、テキストを解析すると NPE になりました。 この問題は、説明を解析する前に、onError 中に説明に対して null チェックを追加することで解決されました。

* Zendesk #22286 — ネイティブライブラリはメモリ読み取りキー/フラグメントを割り当てているため、クラッシュが発生しています。複数のキーを持つマニフェストを同時に読み込もうとしたときに Android で発生するこのクラッシュが修正されました。

**バージョン 1.4.22 (1581)**

* Zendesk #17236 - DRM を使用した HLS ビデオの信頼性の低い再生ヘッド時間オーディオセグメントの開始時間がビデオセグメントの開始時間と一致しない LBA ストリームでの時間ジャンプを修正しました。

* Zendesk #17680 - Video playback is freezing on the Selevision Andredo ボックスこのデバイスのビデオデコーダは、出力バッファからビデオフレームをデキューする際に、大きな出力時間ジャンプを返す場合があり、この出力タイムスタンプは高いままです。 この問題は、 *ビデオプロファイルはサポートされていません* 同じプロファイルを再試行するか、別のプロファイルを選択するようプレーヤーに強制しないエラー。

* Zendesk #19074 - FFWD および REW トリック再生中にビデオがフリーズするこの問題は、新しい警告 TRICKPLAY_ENDED_DUE_TO_ERROR を追加し、トリック再生が終了し、回復不能なエラーが原因でビデオが一時停止したことをアプリケーションに通知することで解決しました。

* Zendesk #19574 - TVSDK が DRM または DRM 以外のコンテンツに対する M3U8 応答データを返さないこの問題は、次の方法で解決されました。

* Zendesk #19986 - Android TV などの特定のデバイスでの OP 動作が破損している
* FILE_NOT_FOUND エラーを条件に追加します。
* エラーが *ファイルが見つかりません* エラーが発生し、応答がある場合は、エラーの説明から URL と応答を分離する。
NVidia シールド OP サポートによって発生したロジックエラーが修正されました。 非 NVidia シールドデバイスでは、表示の種類が不明な場合でも、表示セキュアフラグを信頼します。

* Zendesk #20549 — 古い再生リストの処理。 この問題は、以前のフェッチで新しいセグメントが受信されない場合、ライブマニフェストの更新間隔を、期待されるセグメント期間の半分に減らすことで解決されました。

* Zendesk #20742 - FireTV でライブコンテンツを再生する際、メモリ使用量が増加し続けているようです。クラッシュの原因は、JNI オブジェクト参照テーブルが制限に達したことです。 この問題は、デコーダーの再起動中に作成された MediaFormat オブジェクトへの参照を削除することで解決されました。

* Zendesk #21125 — ライブ/リニア広告ブレークから早期に戻る (CSAI)。 オポチュニティディテクターでスプライスを使用して広告キューにスプライスを登録した場合、広告ブレーク中にプレーヤーがメインコンテンツに戻れる機能が追加されました。

* Zendesk #21334 — サードパーティ広告リクエストの TVSDK 広告リクエストのタイムアウト値。 広告呼び出しのグローバルタイムアウトを有効にする adRequestTimeout 設定が AdvertisingMetadata に追加されました。

**バージョン 1.4.21 (1566)**

* Zendesk #17781 - ADB screencapture は機能しなくなりましたこの問題は、画面キャプチャを可能にする DefaultMediaPlayer.create(Context, boolean secureSurface) API を追加することで解決されました。
スクリーンキャプチャを許可するには、secureSurface に false を渡します。
重要：実稼働環境では、この画面キャプチャ機能を有効にしないことを強くお勧めします。

* Zendesk #19074 - FFWD および REW トリック再生中にビデオがフリーズする以下の問題が解決されました。

* Zendesk #19532 - Close Caption が順不同で表示されています
   * FHS はトリック再生を開始しますが、最初の iframe セグメントにフレームが含まれていませんでした。
   * iframe セグメントのダウンロード中に、FHS がエラー条件をヒットした場合、トリック再生から終了し、再生を一時停止します。
   * Andorid MediaCodec の実装は、すべての入力/出力バッファをフラッシュするように要求された間、入力キューの可用性を永久に待ちます。
この問題は、WebVTT キューの順序を逆にすることで解決され、重なり合う複数のキューが「上にスクロール」するように表示されました。

* Zendesk #19574 - TVSDK は DRM または非 DRM コンテンツの M3U8 応答データを返しません。 PTMediaPlayerItem.prepareToPlay のマニフェストファイルの最初の読み込み時に、読み込みに失敗した場合、 TVSDK はアプリケーションに対する失敗の本文を報告しません。
この問題は、 TVSDK がエラー応答をアプリケーションにエラーとしてレポートできるようにすることで解決されました。

* Zendesk #19701 - SAP/Discontinuity を使用して再生がフリーズするオーディオとビデオが不連続時にアラインされないと、プレーヤーがフリーズします。

* バグ#PTPLAY-11162 - OpenSSL ライブラリをバージョン 1.0.2f に更新しました。

**バージョン 1.4.20 (1546)**

* Zendesk #17384 — 機能リクエスト： AAC メディアでの ID3 メタデータの AAC 再生のサポート AAC メディアでの ID3 タグのサポートは、バージョン 1.4.20 以降の Android 向け TVSDK で提供されています。

* Zendesk #18358 - Player は、非同期の非連続性を持つビットレートスイッチでフリーズしますこの問題は、ABR ステッチのエッジケースを適切に処理することで解決されました。

* Zendesk #19232 - TVSDK 1.4.18 を使用したアプリは、古いAmazon OS バージョン 4 で異常に動作していますこの問題は、Android Webview をサポートしていないデバイスとの競合を避けるために、TVSDK プレーヤーの初期化プロセスで非表示の Web ビューの作成を削除して解決しました。

* Zendesk #19585 — アダプティブビットレートの切り替えが発生した場合のスローモーション再生。
ABR 切り替え中に、新しいプロファイルのオーディオサンプルレートが現在のプロファイルと異なる場合、再生は高速または遅い動きになります。 これは、ビデオプレゼンターに、オーディオ形式が変更されたことが通知されないためです。
この問題は、notify フラグが正しい場所に設定されていることを確認することで解決されました。

* Zendesk #19683 - SAP DAI 再生 — 数秒間オーディオがありません。
TVSDK のロジックのいくつかのケースでは、2 つのレンディションセグメントのタイムスタンプを比較した際に、タイムスタンプが常に 0 ms の差と一致するとは限らないので、 RENDITION_TIMEOUT_THRESHOLD が有効な値の範囲として使用されていました。 ギャップが RENDITION_TIMEOUT_THRESHOLD の範囲内にある場合、一致と仮定されます。

RENDITION_TIMEOUT_THRESHOLD が 100 ms に設定されましたが、一部のストリームには不十分であることがわかりました。 この問題は、 RENDITION_TIMEOUT_THRESHOLD の値を 200 ミリ秒に増やすことで解決されました。

* Zendesk #19699 - TVSDK は VTT 字幕トラックを切り替えられません。この問題は、トラックが変更されたときにプレイヤーダンプを作成し、マニフェストを再読み込みし、2 バイトの WebVTT キャプショントラック名に影響を与えた UTF8 文字列変換の問題を修正することで解決されました。

* Zendesk #19717 - CC オプションの表示問題この問題は、Unicode 文字列を正しく処理することで解決されました。

* Zendesk #19910 - TIT2 ID3 タグが検出されないこの問題は、ID3 v2.4 の文字列エンコーディングおよび ID3 v2.3 のサポートをより完全にサポートすることで解決されました。

* Zendesk #20135 - TVSDK は、VOD コンテンツに対して複数の onComplete をトリガーしています。
この問題は、ステータス変更イベントの大文字と小文字の区別ではなく、適切な場所に post_roll_compelete イベントリスナーを追加することで解決されました。

**バージョン 1.4.19 (1521)**

* Zendesk #4180 - TVSDK は HDCP を適用していません。
   * これはこのチケットの一部を修正したもので、NVidia シールドデバイスの問題にのみ対処します。
HDCP の状態を動的に追跡するには、Nvidia Shield で正しく実装された HDCP 検出 API を使用する必要があります。

* Zendesk #18358 - TVSDK は、ビットレートスイッチでフリーズし、非同期状態が続きません。
   * この問題は、PTS の不連続を検出する新しい警告を追加し、ABR スイッチごとに正しいセグメントを検索し直すように PTS チェックを強制することで解決されました。
フリーズを修正するには、 mediaPlayer.setCustomConfiguration メソッドの呼び出しに forcePTSCheckForABR を引数として含める必要があります。

* Zendesk #19038 - Asus Zenpad 10 にライブストリームがありません。

  この問題は、実行時に関数に対するクエリを実行しないように、メディアコーデック情報をプリロードすることで解決されました。

* 以下の問題は、Zendesk #19038と同じです。
   * Zendesk #19483 - TVSDK が Intel プラットフォームでクラッシュしています。
   * Zendesk #19171 - Asus メモパッド 7 で Android 5.0 でクラッシュします。

**バージョン 1.4.18 (1503)**

* Zendesk #3324 - Primetime 広告レポートは、VMAP に広告メディアがない場合、広告の時間を追跡しません。
広告ブレークが空の場合、広告ブレーク開始および完了追跡イベントが ping されていませんでした。 この問題は、VMAP AdBreak などの空の広告ブレークに対して、有効な AdSource ノードを使用して広告ブレーク開始 ping を送信することで解決されました。

* Zendesk #18229 - SetCCVisibility(VISIBLE) は MediaPlayer.reset() 呼び出しの後は無視されますこの問題は、MediaPlayer クラスに setCCVisibility(Visibility.INVISIBLE)；を reset() 関数に追加することで解決されました。

* Zendesk #18328 - 60 FPS のコンテンツ用Amazon Fire TV 第 2 世代デバイスでのフレームの問題この問題は、睡眠時間の決定にエンコードされた FPS を適用し、よりエンコードされた FPS 予測ロジックを適用することで解決されました。

**バージョン 1.4.17 (1472)**

* Zendesk #2231 - MediaPlayerNotification で使用できないマニフェストを取得した際にエラーが返されましたこの問題は、解析エラーが発生した場合に、マニフェストの応答本文を含めることで解決されました。

* Zendesk #17703 - VideoEngineView はビデオ再生中にスクリーンショットを防ぐことができません API 17 以降で setSecure メソッドを利用できましたが、API 17 は 4.2、4.2.1、4.2.2 をカバーしているので、どれが例外をスローするか、またはデバイス固有かは不明です。 この問題は、 VideoEngineView.setSecure を try catch 句にラッピングすることで解決されました。

* Zendesk #17919 - Content seek がハートビートエラーを引き起こす無効な入力データ位置エラーは、プリロール後にシークが開始されたときに生成されたハートビート呼び出しの結果として発生していました。 この問題は解決されました。

**1.4.16a** (1454a)

* Zendesk #18215 — 一部の AES ストリームが読み込めません。
この問題は、AES キーを読み込む前にプロファイルの DRM メタデータのサイズを確認することで解決されました。

**バージョン 1.4.16 (1454)**

* Zendesk #3875 - Tab S 再生中にクラッシュ CRS のAuditudeに対する OKHTTP の依存関係を元に戻す TVSDK は、curl の代わりに httpurlconnection を直接使用するようになりました。 この問題は、他の JNI 呼び出しをおこなう前に例外をクリアすることで解決されました。

* Zendesk #4487 - Tracking Linear Channel of Content リニアストリーム再生セッション中にビデオハートビートトラッカーを再初期化することで、この問題は解決されました。

* Zendesk #17919 - Android - content seek がハートビートエラーを引き起こすチャプター内のシークが解決された場合、ハートビートがエラー状態にあるときの問題。

* Zendesk #18053 - Adobe Primetimeが Marshmallow でクラッシュする TVSDK ライブラリが YUV ->RGBの色変換を行うネオンコードを使用した際に、Android M OS で TVSDK がクラッシュしていました。 この問題は、ネオンでないバージョンのコードを使用して、この問題の原因となっている機能を更新することで解決されました。

* Zendesk #18072 - Android M — アプリケーションクラッシュプロファイルとレベルがサポートされているかどうかを確認すると、MediaCodecList および MediaCodecInfo API を呼び出すとクラッシュが発生します。 この問題は、コーデック情報が必要な場合にのみこれらの API を呼び出さないように、すべてのコーデック情報を事前に読み込むことで、一時的な対処を提供することで解決されました。

* Zendesk #18074 - Android 6.0 で Nexus で動作しないアラビア語の字幕問題は、Android 用の CTS フォントマップのサポートを提供することで解決されました。

**バージョン 1.4.15 の更新 (1438)**

* Zendesk #17437 — 一部の AES ストリームでの VOD コンテンツの起動の遅延が長くなります。
この問題を解決するには、マニフェストに複数のキーが一覧表示されている場合は、すべての AES キーを並行してダウンロードします。

**バージョン 1.4.15 (1435)**

* Zendesk #4278 - Android でのグリッチは、適応ビットレート変更 (ABR) 時のトップボックスを設定します。
修正は、最新の Android メディアコーデックとのシームレスな ABR 切り替えのサポートを追加することでした。

* Zendesk #17063 - mediaPlayer.reset() を呼び出すと、ビデオエンジンのリセットエラーが発生します。
修正は、ErrorEvents のディスパッチ時に VideoEngineExceptions から元の MediaErrorCode を含めることでした。

* Zendesk #17130 - FireTV で見られるビットレートを変更する際の短いが目立つ一時停止。
( 上記の#4278と同じ ) 修正は、最新の Android メディアコーデックとのシームレスな ABR 切り替えのサポートを追加することでした。

* Zendesk #17666 — コンテンツを再開する際の追加の広告マーカー、予期しない、または広告なし。
この修正は、ビデオオンデマンド (VOD) コンテンツで prepareToPlay を実行する際に、初期シークが仮想時間ではなくローカル時間で実行される問題でした。

* Zendesk #17437 — 一部の AES ストリームでの VOD コンテンツの起動の遅延が長くなります。
修正では、マニフェストに複数のキーがリストされている場合、すべての AES キーを並行してダウンロードする必要がありました。

* Zendesk #17851 - Android TV - ABR 中の黒いフレームアダプティブ再生を有効にするために KEY_MAX_WIDTH と KEY_MAX_HEIGHT を指定することが修正されました。

**バージョン 1.4.14 (1415)**

* Zendesk #3875 - Tab S 再生中にクラッシュします。
クラッシュを防ぐために、追加の修正が必要でした。

* Zendesk #17245 - Android TV でのフォールバックが機能していません。
フォールバックが有効になっていて、VMAP 応答に空の広告ブレークがある場合に再生がハングする追加の問題を修正しました。

**バージョン 1.4.14 (1412)**

* Zendesk #17245 - Android TV でのフォールバックが機能しない。
フォールバック広告でのクリエイティブの再パッケージ化を無効にする制限を削除しました。

**バージョン 1.4.13 (1388)**

* Zendesk #3502 — 広告ブレーク中の HLS クライアントベースのフェイルオーバーサポートライブプロファイルの更新時に、広告ブレーク中にメインマニフェストへのフェイルオーバーが発生することを許可します。

* Zendesk #3875 - Tab S 再生中にクラッシュ HttpUrlConnection と cURLm の間の競合を解決するには、サードパーティのライブラリを使用してください。

* Zendesk #4450 — コンテンツリゾルバーでの 1 つの配置に対してカスタムメタデータを設定するセッターを商談設定に追加します。

**バージョン 1.4.12 (1388)**

* Zendesk #2751 - CSAI と CRS | Enhance：特定のメディアファイル URL の動的要素を処理します。
Creative Repackaging Service が更新され、動的なクリエイティブ URL を含む広告を適切に処理するようになりました。

* Zendesk #3965 — トリック再生から通常の再生に切り替えると、再生を開始する前に少し前にジャンプが発生します。
   * 修正には、GetStreamTime の計算を試みる代わりに、すべての変数が更新されるまでのレート変更までの時間を返す TVSDK が含まれます。
   * ストリームの終わり近くでトリック再生速度を変更するとクラッシュが修正されました。
   * トリック再生中の現在の時間の計算を修正しました。

* Zendesk #3978 - 8 倍と 16 倍のトリックプレイは頻繁にフリーズします。
   * バッファリングが一定でおこなわれないように、常に最も低いビットレートのトリック再生プロファイルを選択します。
   * 高いトリック再生率を得るには、スキップフレーム間隔を長くします。
   * トリック再生中にターゲットの長さに達した後もバッファが増え続ける問題を修正しました。

* Zendesk #3992 — 追加のトリックプレイ速度。
TrickPlay が 16x より高いレートを受け入れるように更新されました。+/- 32、+/-64 および+/-128 も許可されるようになりました。

* Zendesk #4007 - GEOB オブジェクトをタイムラインメタデータ（Android および Web）の一部として解釈します。
setByteArray および getByteArray API が追加されました。

* PTPLAY-7301 — ランダムアクセスポイントでの即時開始。
即時オンが更新され、ゼロ以外の開始点を使用できるようになりました。

**バージョン 1.4.11 (1363)**

* Zendesk #2076 - Frequent stutter when playing video on Motorola Xoom with Android 4.0.3許可リストにデバイスを追加し、高プロファイルのコンテンツを再生できなくしました。

* Zendesk #2197 - `[Ads]` 追跡広告エラーディスパッチ OperationFailedEvent （警告通知付き）。

* Zendesk #3304 - VAST 3.0 `[ERRORCODE]` マクロが入力されていません
   * インライン広告に不適切なクリエイティブがある場合、エラーコード 400 が表示されます。
   * `[ERRORCODE]` マクロは URL エンコードされます

**バージョン 1.4.10 (1354)**

* Zendesk #2941 — ライブアセットはシーク可能な範囲に「0」を持ちません以前は、ライブストリームの最初にシークする際に 3 つのセグメントバッファがあり、ライブストリームの最初（最初のセグメントの最初）をシークできるようになりました。

* Zendesk #3169 - Adobe Analyticsとの統合でリファレンスプレーヤーを更新リファレンスプレーヤーは、Adobe Analyticsライブラリを使用して埋め込みの例として更新されました。
* Zendesk #3299 — 説明のつかないトリック再生動作
   * トリック再生を停止した後に再生状態に戻ると、数秒（場合によっては 25 秒以上）かかる問題を修正しました。
   * 同じメディアでトリックを 2 回呼び出して再生すると、ストリームが現在の時間にフリーズする可能性があるバグを修正しました。
* Zendesk #3433 - Android とFlash — 字幕の問題

WebVTT 用の GetLine が、 &lt;cr>&lt;lf> パケットの長さを調整しました。最後のキャプションには、前のキャプションの文字を含めることができます。

* PTPLAY-6243 — 参照プレーヤーを強化してデバッグ情報を取り込む

Android サンプルリファレンスプレーヤーが強化され、デバッグログをオンにして結果を電子メールで送信するオプションが追加されました。 このオプションは、リファレンスプレーヤーのログメニューにあります。

**バージョン 1.4.9 (1332)**

* Zendesk #2649 — バッファー完了は、最初のバッファーがいっぱいになる前に発生します

シーク後に、ビデオエンジンがビデオプレゼンターが再生できる状態になる前に状態を PLAYING に設定する場合があります。 シークの前にバッファー状態が高い場合に発生します。 ビデオエンジンに低バッファ状態を通知して修正します。 ビデオエンジンの低バッファ状態で、Play を呼び出すと、状態が PLAYING ではなく BUFFERING に変わります。 状態が PLAYING に変わったときに再生が再開されます。

* Zendesk #2846 — 機能強化リクエスト：Auditudeライブラリがおこなった呼び出しに対して、異なるユーザーエージェント文字列を設定する機能を提供します。

広告関連の呼び出しのユーザーエージェントを設定する新しい API が追加されました、 auditudeSettings.setUserAgent(&quot;user/agent&quot;)。 ユーザーエージェントが設定されていない場合は、デフォルトが使用されます。 これは広告関連の呼び出しのユーザーエージェントにのみ影響し、メディア呼び出しのユーザーエージェントは変更されません (「Adobe Primetime」+)&lt;default useragent=&quot;&quot;>.

**バージョン 1.4.8 (1324)**

* Zendesk #1218 - 106000.33 ローカルでエラーが発生しました…FragmentedHTTPStreamer::ThreadParseManifest() でマニフェストを読み込めない場合は、URL ドメインが localhost であるかどうかを確認し、その場合はドメインを 127.0.0.1 に変更して、ThreadParseManifest を呼び出します。
* Zendesk #3072 — 低ビットレートへの自動切り替え。 ゼロ PTS ペイロードをスキップするようにバッファ長の計算を変更しました。
* Zendesk #3168 - WebVTT の字幕は最初の 10 秒間のみ表示されました。
* Zendesk #3193 - TVSDK でのプロファイル変更 API のリクエスト、 PlaybackEventListener.onProfileChanged() が追加されました。

**バージョン 1.4.7 (1311)**

* Zendesk #2197 — 広告エラーの追跡。 マニフェストを読み込めなかったアセットの通知を追加しました
* Zendesk #2575 - PSDK は、ビデオの前の MARK カスタムインストリーム広告を無視します
* Zendesk #2719 - Win Death ads、auditude プラグインで相対 url にリダイレクトされた際の固定ビーコン追跡機能
* Zendesk #2760 - TrickPlay モード中に DISCONTINUITY タグが無視される
* Zendesk #2805 — 再生開始時にプレーヤーがクラッシュする、Zendesk と同じ修正が行われまし#2719
* Zendesk #2817 - Android プレーヤー — 2.0 から 3.0 秒の間にデコードバッファを拡張することで、プレーヤーがハングしたり、再生を停止したりする場合があります。
* Zendesk #2839 - Adobe Primetime PSDK は ARMv8 チップセットをサポートしていますか？は、Galaxy S6 で見つかったクラッシュの修正を追加しました。
* Zendesk #2885 -Auditude再生をクラッシュし、Zendesk #2719と同じ修正を行いました
* Zendesk #2895 - 10 分間の再生後も、ライブ HLS のエラーが一貫して発生する
* Zendesk #2925 - Android 開発ビルド (1.4.5) に関するフィードバック (1.4.5) は、パケットを入力キューにキューに入れる際、PTS が負の場合、デコーダは、将来のパケットに対して常に負の出力 PTS を得るという奇妙な状態になります。 この問題を回避するために負の場合は、入力 PTS を 0 に設定します。
* PTPLAY-4645 - Openssl で RC4 暗号サポートをオフにする。 RC4 の既知の弱点があります。 つまり、RC4 しかサポートしていないサーバとの接続を試みると、失敗します。

**バージョン 1.4.6 (1282)**

* Zendesk #2192 - Bitrate は、高速なスイッチ実装を取り除くことで、ネットワークの状態が悪い場合に常に低下するとは限りません。
* Zendesk #2631 - Android のアラビア語字幕：複数行のテキストは切り取りで表示され、アラビア語フォントのフォントサイズを調整して固定されます。
* Zendesk #2844 - Note 4 でのバッファリングとフラグメントのダウンロード時間が正確ではありません。

この問題は、ビデオセグメントのダウンロード間の待ち時間を帯域幅の計算に追加し、ダウンロード時間の計算ロジックで完全なリクエストサイクル時間を使用することで修正されました。

* Zendesk #2908 — アラビア語の字幕が Nexust 5、6、7 で機能しない。アラビア語のスクリプト用に 2 つの代替フォントを追加することで修正。
* PTPLAY-4627 - Nielson appsdk をバージョン 1.2.3.7 に更新しました。
* PTPLAY-5084 — ライブマスターマニフェストの更新フェールオーバーのサポート

**バージョン 1.4.5 (1248)**

* Zendesk #1757 — 一部のビデオビットレートプロファイル、Nexus 4 および Nexus 7 で再生されたオーディオまたはプレーヤーのみがクラッシュする問題を修正しました。
* Zendesk #2072 - AdEvent の TimedMetadata には、「http」の完全な URL は含まれていません
* Zendesk #2192 - Bitrate は、ネットワークの状態が悪いときに常に低下するとは限りません
* Zendesk #2256 -マスタープレイリストへのアクセス、PSDK を更新し、マスタープレイリスト上のサブスクライブ済みタグに対する timedMetadata イベントをディスパッチしました。
* Zendesk #2269 - WebVTT を使用して、2 つの異なる字幕言語が画面に同時に表示されます
* Zendesk #2417 - Player が再生開始前に字幕をダウンロードしようとしたとき、WebVTT がセグメント番号の一致に誤ったセグメント番号変数を使用していました。 バグは、0 から始まるセグメントインデックスを持つメディアに対してのみ表示されます。
* Zendesk #2470 — サスペンション後にビットレート変更が発生した場合に、PSDK が SUSPENDED 状態から戻らない。 RestoreGPUResource がスマートシークを呼び出し（休止状態からプレーヤーを復元）、その前にストリームスイッチが検出された場合、スマートシークを完了できず、一定のバッファリングが発生します。
* Zendesk #2451 — クローズドキャプション「ボトムインセット」、キャプションコードに「bottomInset」パラメーターを追加
* Zendesk #2480 - HTTP 302 リダイレクト最適化の無効化、useRedirectedUrl プロパティの設定のサポートを追加
* Zendesk #2486 — サードパーティビーコン
* Zendesk #2547 — アラビア語の字幕：テキストは右揃えで配置する必要があります

**バージョン 1.4.4 (1195)**

* Zendesk #1158 - Huawei Valiant で再生が失敗する (Y301A1)
* Zendesk #1709 — メディアサイズが正しくなく、ビデオが引き伸ばされました
* Zendesk #1757 — 同一の spa/pps データを持つストリーム間でプロファイルを切り替えた後に再生されたオーディオのみ
* Zendesk #2095 - HTTP 307 ステータス（リダイレクト）により、Adobeプレーヤーが再生を停止します。
* Zendesk #2126 — 最後の ADEVENT の TimedMetaData イベントが見つかりません。最後のセグメントの後に存在するサブスクライブ済みタグは、AVE から PSDK に報告されませんでした。
* Zendesk #2227 - VideoEngine nativeReset と nativePause でのロックアップ
* バグ#3921755 - OpenSSL ライブラリをバージョン 1.0.1L に更新しました。

**バージョン 1.4.3 (1173)**

* Zendesk #1591 - RENDITION_M3U8_ERROR
* Zendesk #1870 — クローズドキャプションのオン/オフ
* PTPLAY-1818 — 巻き戻しトリック再生が、巻き戻しではなく広告で停止する
* PTPLAY-2736 - WebVTT キャプションを含むストリームの再生が完了すると、以前に表示された WebVTT キャプションが画面に表示されます。
* PTPLAY-3773 — 広告の位置の後にストリームの再生が開始された場合、ミッドロール広告は再生されません

**バージョン 1.4.2**

* Zendesk #1561 - HLS クライアントベースのフェイルオーバーサポート (primetime)。 プログラムの日時を使用してフェイルオーバーに対処
* Zendesk #1590 - LoadInfo.MediaDuration は常に 0 です（オーディオ専用では固定されていません）
* Zendesk #1626 - Potential Memory Leak in Player. 実際のメモリリークではなく、NotificationHistory が最近 1000 件の通知を保存する際に問題が発生しました。これは 100 件に削減されました。
* Zendesk #2192 - Bitrate は、ネットワークの状態が悪いときに常に低下するとは限りません

**バージョン 1.4.1 (1121)**

* Zendesk #1951 - 4.0.x デバイスでの VideoEngine.nativeReset() でのロックアップ
* Zendesk #2064 — 特定の Intel ベース Android デバイス上でのネイティブクラッシュ SIGSEGV
* Zendesk #2075 - Lockup in VideoEngine.nativeReleaseGPUResource on 4.0.x devices 注：このビルドは次のとおりです。 &#42;&#42;&#42;必須&#42;&#42;&#42; (Android 5.0(Lollipop) のサポート )
* Zendesk #1513 - Android Lollipop のサポート
* Zendesk #1709 — メディアサイズが正しくなく、ビデオが引き伸ばされました
* Zendesk #1871 - WebVTT キャプションは、WebVTT キャプションを含むライブストリームを表示すると、時折消え、再び表示されます
* Zendesk #1996 - PSDK 1.4.0 では、タイムラインマーカーは表示されません。
* Zendesk #2046 - PSDK 1.4.1.1113 でクラッシュし、Auditude から広告が返されない場合にライブストリームがクラッシュする問題を修正しました。
* バグ#3769657 - curl のバージョンを7.38.0に更新します
* PTPLAY-1575 - ABR 再生がオーディオのみのストリームで開始し、オーディオ/ビデオストリームに切り替わると、オーディオが続く間、ビデオはレンダリングされません
* PTPLAY-2499 - OpenSSL をバージョン 1.0.1j に更新し、最近の脆弱性に対処します。
* PTPLAY-2632 - Android Lollipop でミッドロール広告が完了した後、ビデオが回復しない
* PTPLAY-2678 - Android Lollipop でのライブ長期テスト中にビデオが停止する

**バージョン 1.4.0**

* Zendesk #1024 — マニフェストを介してストリームから広告を削除する機能
* Zendesk #1293 — クローズドキャプショントラックの選択に関する問題。
* Zendesk #1590 - LoadInfo.MediaDuration が常に 0 で、 mediaDuration が正しい値を表示するようになりました。
* Zendesk #1629 - Galaxy S4 での広告再生の終わりにプレーヤー/アプリがクラッシュする
* Zendesk #1674 - ClosedCaption 表示されません。0x03 ETX コードが見つからない場合は、708 のキャプションが表示されます。
* PTPLAY-2157 — 異なるスタイルが設定され、ストリーム上で視覚的に検証された後でも、デフォルトのクローズドキャプションスタイルがゲッターから返された。 クローズドキャプションスタイルのプロパティに、設定された値が表示されるようになりました。

## 1.4 の既知の問題 {#known-issues-in}

**バージョン 1.4.31**

* PTPLAY-16803 — クローズドキャプションは、キャプションシステムが動作するためにビデオを必要とするので、オーディオのみのコンテンツでは機能しません。 ビデオがない場合、ビューポートの寸法はなく、ビューポートの寸法がない場合、キャプションのグラフィックを表示できません。
* PTPLAY-1634 — 同じ配信登録済みタグが、異なるライブウィンドウで異なるタイムスタンプを持っています。 ライブウィンドウが移動した場合、同じタグに同じタイムスタンプが含まれている必要があります。 ただし、同じタグでも、異なるタイムスタンプを持つ場合があります。
* PTPLAY-3197 - Acer Iconia デバイスで信号 11 SIGSEGV エラーが発生し、連続再生から 1 時間後にクラッシュする
* PTPLAY-3310 — 低ビットレートのオーディオで、オーディオが Acer Iconia で途切れ途切れになる
* PTPLAY-3355 — 連続再生から 1 時間後に 4.0.x で Motorola Xoom で WIN DEATH がクラッシュする。
* PTPLAY-3557 — 広告の時間に巻き戻しが原因で、ストリームが完了している
* PTPLAY-7079 - Android クライアントの再生ウィンドウが、セキュアな停止/ハード停止で動作しない
* バグ#3760144 - Kindle Fire 7 や Samsung Galaxy Nexus などの一部のデバイスでストリームが一時停止すると、解像度がずれたりパルス状に表示されたりする場合があります。 近い検査でのみ観測可能
* バグ#3761170 - Ads を使用した Live での seekToLocal は、広告コンテンツをシークできません。ライブストリームに currentTime API を使用するのが最適です。
* バグ#3763370 — 広告のあるライブストリームでは、1 つの広告のみが存在する必要がある場合に、2 つの広告マーカーが近くに表示されることがあります。 これらの広告マーカーは同じ広告を表し、1 つのみ再生されます
* バグ#3763373 - VOD ストリームで広告をシークすると、広告マーカーが短時間消える場合があります。 広告マーカーが復元され、タイムラインに他の悪影響はありません
* 一部のデバイスでは、既知の再生の問題が発生しています。 詳しくは、 [1.4 でのデバイスの既知の問題](https://helpx.adobe.com/primetime/release-notes/tvsdk-1-4-android.html#Knownissuesin14).
* 参照実装 — トリック再生がサンプルアプリケーションに実装されていません
* 一部の Android TV デバイスでは、次のトランジションポイントでのデコーダーリセットにより、黒いフレームが表示される場合があります。
   * トリックプレイモードに入る、または出る
   * 遅延バインディングオーディオトラックの切り替え
   * 広告からメインコンテンツへ

**バージョン 1.4.23**

* クローズドキャプションは、ビデオが動作する必要があるので、音声のみのコンテンツでは機能しません。 ビデオがない場合、ビューポートの寸法はなく、ビューポートの寸法がない場合、キャプションのグラフィックを表示できません。
* バージョン 1.4.23 以降、 TVSDK は Gingerbread OS 2.3 をサポートしません。これは、 TVSDK が以下のプライベートな Android ライブラリを使用して、Gingerbread OS を使用するデバイスに関するハードウェア情報を収集したためです。

   * `libstagefright.so`
   * `libcutils.so`

Android N リリースでは、Googleはこれらのプライベートライブラリへのアクセスを削除しました。 現在、Gingerbread OS は Android OS の市場シェアの 1%未満を世界で占めているので、バージョン 1.4.23 以降、Gingerbread OS は TVSDK でサポートされなくなります。
バージョン 1.4.23（Android N のサポートを含む）以降を使用する場合：
* minSdkVersion 11 を使用するようにアプリを更新します。
* エンドユーザーが OS 2.3 を実行している場合、SDK のバージョンはアプリケーションの minSdkVersion よりも低くなります。 アプリケーションのインストールまたはアップグレードが中止されます。
* エンドユーザーが OS 2.3 より上のバージョンを実行している場合、アプリケーションは正しくインストールされます。

minSdkVersion を更新する場合：

* エンドユーザーが OS 2.3 を実行している場合、アプリケーションはインストールされていますが、再生は機能しません。
これは、更新および新規インストールの両方に適用されます。
* エンドユーザーが OS 2.3 より上のシステムを実行している場合、アプリは正しくインストールされ、コンテンツは正しく再生されます。

**バージョン 1.4.22**

* スプライスアウトタグとスプライスインタグが互いに近すぎる場合、広告からの早期終了が一部のミッドロール広告では機能しません。

**バージョン 1.4.2**

* 広告の時間に巻き戻しを行うと、ストリームが完了します。

メディアプレーヤーは、広告の境界に到達したときに、トリック再生の巻き戻し操作中に MediaPlayerPlayerState.Complete を誤って送信します。 トリック再生モードの場合、プレーヤーはこのイベントを無視する必要があります。無視しない場合、SDK は状態を正しく処理します。

**バージョン 1.4.0 (1086)**

* PTPLAY-1634 — 同じ Subscribed タグが、異なるライブウィンドウで異なるタイムスタンプを持っています。 ライブウィンドウを移動する場合、各ウィンドウ内の同じタグに同じタイムスタンプが割り当てられている必要があります。 ただし、同じタグでも、異なるタイムスタンプを持つ場合があります。
* PTPLAY-2541 — ブラックアウトで代替ストリームに対するスイッチ/切り替えが複数回行われた後に、COMPONENT_CREATION_FAILURE が表示される場合がある
* バグ#3726865 - MultiBitrate LBA ストリームがオーディオ専用ストリームから開始した場合、オーディオ/ビデオストリームに切り替えた場合、ビデオは表示されません。 オーディオ/ビデオストリームから開始すると、この問題は表示されず、オーディオとオーディオ/ビデオストリームを正常に切り替えることができます。
* バグ#3760144 - Kindle Fire 7 や Samsung Galaxy Nexus などの一部のデバイスでストリームが一時停止すると、解像度がシフトしたりパルス状態になったりする場合があります。 近い検査でのみ観測可能
* バグ#3761170 - Ads を使用した Live での seekToLocal は、広告コンテンツをシークできません。ライブストリームには currentTime API を使用するのが最適です。
* バグ#3763370 — 広告のあるライブストリームでは、1 つの広告のみが存在する必要がある場合に、2 つの広告マーカーが近くに表示されることがあります。 これらの広告マーカーは同じ広告を表し、1 つのみ再生されます
* バグ#3763373 - VOD ストリームで広告をシークすると、広告マーカーが短時間消える場合があります。 広告マーカーが復元され、タイムラインに他の悪影響はありません
* 一部のデバイスでは、既知の再生の問題が発生しています。 詳しくは、 [1.4 でのデバイスの既知の問題](https://helpx.adobe.com/primetime/release-notes/tvsdk-1-4-android.html#Knownissuesin14).
* 参照実装 — トリック再生はサンプルアプリケーションに実装されていません。

## 1.4 でのデバイスの既知の問題 {#known-device-issues-in}

| デバイス | チップセット | 問題 | 原因 | 回避策 |
|--- |--- |--- |--- |--- |
| Droid X | TI OMAP3 | ABR 遅延は、デコーダーを再起動するので、期待される動作です。 |  |  |
| HTC Desire（HTC Desire HD とは異なる） | QSD8250 | ビデオを再生できません。 VIDEO_PROFILE_NOT_SUPPORTED エラーを返します。 | Desire は適切な HW デコーダを提供しません。 Stagefright の SW デコーダを提供します。 | デバイスを再起動します。 |
| HTC EVO 4G | QSD8650 | HW デコーダーがありません。 | Qualcomm には HW デコーダがありません。 | Android 4.x にアップグレードします。 |
| Kindle FireSystem バージョン 6.0 | TI OMAP4 | HLS ストリームを再生しません。 AIRのビデオが動作しない。 |  | システムバージョン 6.3 にアップグレードします。 |
| Kindle Fire HD | TI OMAP4 | ビデオを再生できない状態になる可能性があります。 VIDEO_PROFILE_NOT_SUPPORTED エラーと UNRECOVERABLE_ERROR エラーを返します。 | 例えば、クラッシュが発生した後に、HW デコーダーが完全にシャットダウンされなかった場合、HW デコーダーは回復不能状態になります。 デバイス上のネイティブアプリでも発生します。 | デバイスを再起動します。 |
| Kindle Fire HD 8.9 | Snapdragon 800 | 複数の ABR 切り替え後に AVE がクラッシュします。 |  |  |
| モトローラアトリックス | Tegra2 | AIRとは対照的に、AVE の全体的なパフォーマンスの問題です。 9 ～ 15 分間再生した後、オーディオ/ビデオが同期されず、ビデオ再生がフリーズする。 クラッシュ。 | おそらく、AIRで有効にする openGLES に関連しています。 調査中です。 |  |
| Nexus 7（第 2 世代） | S4Pro APQ8064 (Qualcomm) | ムービーが 30 分以上一時停止された場合にデバイスがハングする。 | Googleに報告されたデバイスの問題。 | 長い一時停止状態を許可しないように、アプリケーションはタイムアウトする必要があります。 |
| Nexus S (GB) | ハミングバード | HW デコーダを使用してビデオを再生できません。 | Nexus S には Stagefright ベースの HW デコーダーがないので、Android 2.3 では SW デコーダーを使用しています。 | ICS にアップグレードします。 |
| Nexus S (ICS) | ハミングバード | ビデオが時折ちらつく。 | データが正しくないと、デコーダーが無効な状態になる可能性があります。 | デバイスを再起動します。 |
| Nook tabletAndroid OS: 2.3 | TI OMAP 4 | ビデオが再生されず、アプリがハングします。 | アプリを数回実行した後、stagefright が不安定な状態に入る。 mediaplayer::QueryCodecs への呼び出しはハングします。 | 状態をリセットするには、デバイスを再起動します。 |
| Samsung Galaxy ACE | Qualcomm MSM7227 | SampleMediaPlayer アプリをインストールできません。 | より一般的な ARM v7 チップセットの代わりに、ARM v6 を使用します。 FP/AIRはこのデバイスをサポートしていません。 |  |
| Samsung Galaxy ACE2Android OS: 2.3.6 | ノバトール U8500 | ビデオを再生できません。 | このチップセットは、AVE の Android プリ ICS 用の不明なデコーダです。 |  |
| Samsung Galaxy S2 (GT-I9100) | エキノス | このデバイスのビデオパフォーマンスは上限ではありません。 | HW デコーダは、誤った PTS でデコードされたフレームを返します。 デコーダーは、プレゼンテーション時間ではなく、デコード時間を使用しているようです。 |  |
| Samsung Galaxy S2 GAndroid OS: 2.3.6 | TI OMAP4 | ビデオの開始時にクラッシュします。 |  | Android 2.3.7 または 4.x にアップグレードします。 |
| Samsung Galaxy S3 (I747) | Qualcomm MSM8960 | 断続的に、ビデオがフリーズし、オーディオのみが再生され、応答しなくなります。 |  |  |
| Samsung Galaxy S3 I747M | SAMSUNG_M2ATT | ビデオがフリーズする。 | 調査中です。 |  |
| Samsung Galaxy Tab 1 v10.1 | テグラ 2 | MBR の切り替えには最大 3 秒かかる場合があります。 | MBR クラッシュの修正として、ストリームスイッチごとにデコーダーを再起動します（最大 3 秒かかる場合があります）。 |  |
| Samsung Galaxy Y |  | SampleMediaPlayer アプリをインストールできません。 | より一般的な ARM v7 チップセットの代わりに、ARM v6 を使用します。 FP/AIRはこのデバイスをサポートしていません。 |  |
| Xoom | テグラ | 切り替えのためにいくつかのフレームがドロップされます。 デコーダーが再起動されません。 | OMXAL の制限。 |  |

## 役立つリソース {#helpful-resources}

* 完全なヘルプドキュメントは、 [Adobe Primetimeラーニングとサポート](https://helpx.adobe.com/support/primetime.html) ページに貼り付けます。
