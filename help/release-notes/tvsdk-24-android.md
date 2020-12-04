---
title: TVSDK 2.4.1 for Androidリリースノート
seo-title: TVSDK 2.4.1 for Androidリリースノート
description: Android向けTVSDK 2.4.1リリースノートでは、TVSDK Android 2.4.1の新機能およびサポートされる機能、既知の問題および制限について説明します。
seo-description: Android向けTVSDK 2.4.1リリースノートでは、TVSDK Android 2.4.1の新機能およびサポートされる機能、既知の問題および制限について説明します。
uuid: 929fc577-e851-4e03-9201-13280cc6137a
topic-tags: release-notes
products: SG_PRIMETIME
discoiquuid: a6dbcc4a-9e14-4452-9004-b39ed13fad6f
translation-type: tm+mt
source-git-commit: e644e8497e118e2d03e72bef727c4ce1455d68d6
workflow-type: tm+mt
source-wordcount: '1988'
ht-degree: 0%

---


# TVSDK 2.4.1 for Androidリリースノート{#tvsdk-for-android-release-notes}

Android向けTVSDK 2.4.1リリースノートでは、TVSDK Android 2.4.1の新機能およびサポートされる機能、既知の問題および制限について説明します。

## TVSDK Android 2.4.1 {#tvsdk-android}

Adobeは、Android向けTVSDK 2.4.1をリリース中です。

このバージョンのTVSDKを使用するには、お使いのシステムが[必要システム構成](https://helpx.adobe.com/content/dam/help/en/primetime/programming-guides/psdk_android_2.5.pdf#page=6)に記載されている要件を満たしていることを確認してください。

ドキュメントは次の場所にあります。

・ Android向けオンラインヘルプシステムTVSDK 2.4ヘルプ

・ [Android Java API ](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.4/index.html)用JavaDocs TVSDK 2.4

Javadocは、TVSDKソースコードから直接自動的に生成されるので、最終的な権限です。

・ [Android C++ API用C++ APIドキュメントTVSDK 2.4](https://help.adobe.com/en_US/primetime/api/psdk/cpp_2.4/namespaces.html)

各Javaクラスは対応するC++クラスを持ち、C++ドキュメントにはJavadocsよりも詳しい説明が含まれているので、Java APIの詳細については、C++のドキュメントを参照してください。

・移行ガイド（[Android向けTVSDK 2.4移行ガイド](../migration-guides/tvsdk-14-25-android.md)）

このガイドでは、TVSDK 1.4に基づくアプリケーションをTVSDK 2.4に基づくアプリケーションに移行するために必要な変更事項について説明します。

## 新機能{#new-features}

Android向けTVSDK 2.4.1は、以前のバージョンと比べて多くのパフォーマンスが向上しています。 高画質で視聴できます。

このバージョンには、バージョン2.4および2.4.1のすべての機能が含まれており、機能は非推奨です。

バージョン2.4.1の主な新機能は次のとおりです。

* HLSバージョン4の機能

   * **ライブ、リニアおよびVODストリーム用のプレイヤーコントロールを使用したビデオ再生** （再生、一時停止、シーク）。
   * **クローズドキャプション。** TVSDKは、フォント、フォントサイズ、色および背景を選択した608/708クローズドキャプションを表示できます。また、ロールアップキャプションを含むビデオをサポートしたり、言語トラックがある場合はそれらを切り替えたりすることもできます。
   * **トリック再生** モードでは、I-Frameを使用するHLSストリームで早送りと巻き戻しがサポートされます。すべてのビデオ再生コントロールは、コンテンツで機能します。 0 ～ 1のレートを持つ外部ビデオ再生モードでは、スローモーション（前方）を使用できます。
   * **アダプティブビットレート(ABR)** を使用すると、同じコンテンツストリームの複数のバージョンのうち、どれを再生するかを、ネットワークや他の条件に基づいて動的に選択できます。アグレッシブ、モデレートおよび保守的な選択ポリシーの中から選択するように、パラメーターを動的またはマニフェストファイル内に設定できます。
   * **バイト** 範囲を使用すると、1つのTSファイルに複数のTSセグメントを含めることができます。
   * **代替オーディオ** レンディションは、プレーヤーが使用可能なオーディオトラックを切り替えられるようにします。
   * **ID3のサポート。** TVSDKは、アーティスト名、タイトル、アルバムなど、ID3オーディオメタデータを含むHLSオーディオストリームおよびビデオストリームを再生できます。
   * **フェイルオーバー。 **TVSDKは、ホストサーバー、プレイリストファイルおよびセグメントに障害が発生した場合でも、中断されない再生を継続する方法を使用します。
   * **マルチチャネルオーディオパススルー(DD+)** TVSDKは、Dolby Digital Plusオーディオ(E-AC3)データをサポートするハードウェアに渡すことができます。

* コンテンツ保護機能

   * **HLSのDRM。** すべてのビデオ再生APIは、Adobeアクセスで保護された暗号化されたビデオコンテンツで機能します。次のDRM機能がサポートされています。

      * ライセンスのローテーション
      * キーの回転
      * ライセンスのキャッシュ
      * ポリシー時間
      * 静脈回転

* **AES 128再生。** TVSDKは、キーサイズが128ビットのAES(Advanced Encryption Standard)HLSコンテンツを再生できます。
* **Protected HLS(PHLS)** は、ライブストリームおよびVODストリームに対してHLS上の軽量なDRMを可能にするために、事前に構築されたDRMポリシーの制限付きセット、Adobeアクセスのサブセットを提供します。

* 広告/代替コンテンツと収益化機能

   * **サーバー側で挿入された広告のトラッキング。** TVSDKは、Adobeクラウド広告挿入サービスによって挿入された広告を追跡できます。VODおよびライブ/リニアストリーム用に、VAST2、VAST3およびVMAP形式のリニア広告をサポートします。
   * **カスタムHLSタグ。** TVSDKは、この `MediaPlayerConfig` クラスを使用して、カスタムHLSタグがストリーム内に出現した場合にプレイヤーアプリケーションに通知できるようにします。
   * **クライアント側の広告挿入。** Auditude広告挿入ライブラリは、Adobe Auditudeサーバーと連携して、ライブ、リニアおよびVODコンテンツへの挿入、プリロール、ミッドロール、ポストロールの位置における広告を動的に解決します。
   * **カスタム広告リゾルバー。**  `ContentResolver, OpportunityGenerator,` お `MediaPlayerClientFactory` よびインターフェイスを使用すると、カスタム広告/代替コンテンツリゾルバーを実装し、カスタムオポチュニティディテクターをTVSDKと連携するように登録できます。`TestAdResolver`および`AuditudeResolver`クラスは、コンテンツリゾルバーの実装のC++の例を提供します。 JavaScriptの例は`samples/jspsdk/testapp/psdk.js`にあります。
   * **一貫した広告動作。** イン `AdPolicySelector` ターフェイスを使用して、広告がコンテンツ内に存在する場合のシークやトリック再生など、すべてのプレーヤーで一貫した動作を有効にします。独自の実装を行わない場合、TVSDKは`DefaultAdPolicySelector`を使用します。
   * **C3広告を削除/置き換えます。** 適切なTVSDK APIを使用して、カスタムコンテンツ範囲を削除し、追加の準備作業を行うことなく、新しい広告を動的に挿入します。これは、ライブ/リニアコンテンツがブロードキャストされ、クリーンアップせずにオンデマンドで即座に使用可能にする場合に便利です。

バージョン2.4の主な新機能は次のとおりです。

* **即時オン(VODおよび** live)即時オンを有効にすると、TVSDKは、再生開始の前にメディアを初期化し、バッファリングします。複数の`MediaPlayerItemLoader`インスタンスをバックグラウンドで同時に起動できるので、複数のストリームをバッファリングできます。 ユーザーがチャネルを変更し、ストリームが正しくバッファリングされた場合、新しいチャネル開始で直ちに再生されます。 TVSDK 2.4は、ライブストリームに対してもインスタントオンもサポートします。 ライブストリームは、ライブ時間が移動すると再バッファリングされます。

* **パフォーマンスの向上**新しいTVSDK 2.4アーキテクチャにより、次の様々なパフォーマンスの向上が実現します。

   * **サブセグメント化** - TVSDKは、各フラグメントのサイズをできるだけ早く開始再生まで減らします。
   * **並行的な広告のダウンロード** - TVSDKは、広告の時間をヒットする前に、コンテンツ再生と並行して広告をプリフェッチするので、広告とコンテンツのシームレスな再生を可能にします。
   * **遅延広告の解決**  — この機能では、非プリロール広告の解決を待たずに再生を開始するので、起動時間が短くなります。シークやトリック再生などのAPIは、すべての広告が解決されるまで許可されません。

* **MP4コンテンツの再生**

このバージョンのTVSDKは、メインコンテンツとしてMP4の再生をサポートしています。

* **永続的なネットワーク接続**

TVSDKは、再利用可能なネットワーク接続のセットを維持するので、ネットワーク要求ごとにネットワーク接続を作成および破棄するオーバーヘッドは発生しません。

* **解像度ベースの出力保護**

この機能により、再生制限が特定の解像度に結び付けられ、DRMコントロールがきめ細かくなります。

* **可変ビットレート(ABR)を使用したトリック再生**

この機能を使用すると、TVSDKはトリック再生モードでiFrameストリームを切り替えることができます。 iFrame以外のプロファイルを使用して、低速でトリック再生を行うことができます。

* **スムーズなトリック再生**

以下の改善により、ユーザーエクスペリエンスが向上します。

・トリック再生中の可変ビットレートとフレームレートの選択(帯域幅とバッファのプロファイルに基づく)

・最大30 fpsの高速再生を実現するには、IDRストリームではなくメインストリームを使用します。

* **ABRロジックの改善**

新しいABRロジックは、バッファー長、バッファー長の変化率、測定された帯域幅に基づいています。 これにより、ABRは帯域幅が変動する場合に適切なビットレートを選択し、バッファー長が変化するレートを監視することで、ビットレートの切り替えが実際に発生する回数を最適化します。

* **請求**

TVSDKは、顧客の販売契約に従って自動的に指標を収集し、課金の目的で必要な定期的な使用状況レポートを生成します。 TVSDKは、すべてのストリーム開始イベントで、Adobe Analyticsデータ挿入APIを使用して、コンテンツタイプ、広告挿入有効フラグ、drm有効フラグなどの請求指標（請求対象ストリームの長さに基づく）をAdobe AnalyticsPrimetimeが所有するレポートスイートに送信します。 これは、お客様独自のAdobe Analyticsレポートスイートやサーバーコールに影響を与えたり、含めたりすることはありません。 リクエストに応じて、この請求の使用状況レポートが定期的に顧客に送信されます。 これは、利用状況の請求のみをサポートする請求機能の最初のフェーズです。 ドキュメントで説明されているAPIを使用して、販売契約に基づいて設定できます。

## サポートされる機能{#supported-features}

Android向けTVSDK 2.4は、ビデオアプリケーションに機能を追加するために実装できる多数の機能をサポートしています。

>[!NOTE]
>
>以下の機能マトリクス表では、√とは、機能が現在のリリースでサポートされていることを意味します。

### コア再生機能{#core-playback-features}

| **機能** | **コンテンツタイプ** | **HLS** | **DASH** |
|---|---|---|---|
| 一般再生（再生、一時停止、シーク） | VOD + Live | √ | √（VODのみ） |
| FER — 一般再生（再生、一時停止、シーク） | FER VOD | √ | 非対応 |
| MP3 | VOD | 非対応 | 非対応 |
| MP4コンテンツ再生 | VOD | √ | √ |
| 可変ビットレート切り替えロジック | VOD + Live | √ | 非対応 |
| オーディオのみの再生 | VOD + Live | √ | 非対応 |
| クローズドキャプション — 608/708 | VOD + Live | √ | √（VODのみ） |
| クローズドキャプション — WebVTT | VOD + Live | √ | √（VODのみ） |
| マニフェストのフェイルオーバー | VOD + Live | √ | √（VODのみ） |
| 高度なフェイルオーバー | VOD + Live | √ | √（VODのみ） |
| QoSおよびプレイヤー通知 | VOD + Live | √ | √（VODのみ） |
| cookieヘッダーのサポート | VOD + Live | √ | √（VODのみ） |
| カスタムヘッダーのサポート | VOD + Live | 非対応 | 非対応 |
| バッファ制御パラメータの設定 | VOD + Live | √ | √（VODのみ） |
| 可変ビットレートコントロールの設定 | VOD + Live | √ | √（VODのみ） |
| カスタムマニフェストタグ(HLS)/イベントストリーム(DASH) | VOD + Live | √ | √（VODのみ） |
| 遅延バウンドオーディオ | VOD + Live | √ | √（VODのみ） |
| 302リダイレクト | VOD + Live | √ | √（VODのみ） |

### 高度な再生機能{#advanced-playback-features}

<table> 
 <tbody>
  <tr>
   <td><strong>機能</strong></td> 
   <td><strong>コンテンツタイプ</strong></td> 
   <td><strong>HLS</strong></td> 
   <td><strong>DASH</strong></td> 
  </tr>
  <tr>
   <td>オフセットのある再生</td> 
   <td>ライブ</td> 
   <td>√</td> 
   <td>非対応</td> 
  </tr>
  <tr>
   <td>オーディオのみの再生</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>非対応</td> 
  </tr>
  <tr>
   <td>トリック再生 </td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>非対応</td> 
  </tr>
  <tr>
   <td>スムーズなトリック再生（ABRを使用）</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>非対応</td> 
  </tr>
  <tr>
   <td>ID3解析(HLS)/時間指定メタデータ(DASH)</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>非対応</td> 
  </tr>
  <tr>
   <td>ブラックアウト </td> 
   <td>VOD + Live</td> 
   <td>非対応</td> 
   <td>非対応</td> 
  </tr>
  <tr>
   <td>即時オン</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>非対応</td> 
  </tr>
  <tr>
   <td>
    <ul> 
     <li>Discontinuity Marker Support（HLS；不連続マーカサポート） </li> 
     <li>複数ピリオド(DASH)</li> 
    </ul> </td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>非対応</td> 
  </tr>
  <tr>
   <td>302リダイレクトの固定性</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>√（VODのみ）</td> 
  </tr>
  <tr>
   <td>サムネールスクラブ（IframeおよびJPEG）</td> 
   <td>VOD + Live</td> 
   <td>非対応</td> 
   <td>非対応</td> 
  </tr>
  <tr>
   <td>ストリームの整合性 </td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>非対応</td> 
  </tr>
 </tbody>
</table>

### コアAd Insertion機能(CSAI) {#core-ad-insertion-features-csai}

| **機能** | **コンテンツタイプ** | **HLS** | **DASH** |
|---|---|---|---|
| 一般的な再生、有効な広告 | VOD + Live | √ | √（VODプリロールのみ） |
| 広告が有効なFERコンテンツ | VOD | √ | 非対応 |
| デフォルトの広告動作 | VOD + Live | √ | √（VODプリロールのみ） |
| VAST 2.0/3.0 | VOD + Live | √ | √（VODプリロールのみ） |
| VMAP 1.0 | VOD + Live | √ | √（VODプリロールのみ） |
| MP4広告 | VOD + Live | √（CRSから） | √（CRSから、プリロールのみ） |

### 高度なAd Insertion機能(CSAI) {#advanced-ad-insertion-features-csai}

<table> 
 <tbody>
  <tr>
   <td><strong>機能</strong></td> 
   <td><strong>コンテンツタイプ</strong></td> 
   <td><strong>HLS</strong></td> 
   <td><strong>DASH</strong></td> 
  </tr>
  <tr>
   <td>広告を有効にしたトリック再生</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>非対応</td> 
  </tr>
  <tr>
   <td>広告のみ </td> 
   <td>VOD</td> 
   <td>非対応</td> 
   <td>非対応</td> 
  </tr>
  <tr>
   <td>ターゲット設定パラメーター</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>√（VODプリロールのみ）</td> 
  </tr>
  <tr>
   <td>カスタムパラメーター</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>√（VODプリロールのみ）</td> 
  </tr>
  <tr>
   <td>カスタム広告動作</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>√（VODプリロールのみ）</td> 
  </tr>
  <tr>
   <td>カスタム広告タグ</td> 
   <td>ライブ</td> 
   <td>√ </td> 
   <td>非対応</td> 
  </tr>
  <tr>
   <td>カスタム広告リゾルバー</td> 
   <td>VOD + Live</td> 
   <td>√ </td> 
   <td>非対応</td> 
  </tr>
  <tr>
   <td>フリーホイールカスタム広告リゾルバー</td> 
   <td>VOD</td> 
   <td>非対応</td> 
   <td>非対応</td> 
  </tr>
  <tr>
   <td>C3広告の置き換え </td> 
   <td>VOD + Live</td> 
   <td>√ </td> 
   <td>非対応</td> 
  </tr>
  <tr>
   <td>遅延広告読み込み</td> 
   <td>VOD</td> 
   <td>√ </td> 
   <td>非対応</td> 
  </tr>
  <tr>
   <td>
    <ul> 
     <li>不連続マーカのサポート — SSAI(HLS) </li> 
     <li>複数ピリオド(DASH)</li> 
    </ul> </td> 
   <td>VOD + Live</td> 
   <td>√ </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>コンパニオン広告、バナー広告、クリック可能広告</td> 
   <td>VOD + Live</td> 
   <td>√ </td> 
   <td>√（VODプリロールのみ）</td> 
  </tr>
  <tr>
   <td>VPAID 2.0</td> 
   <td>VOD + Live</td> 
   <td>√(JS) </td> 
   <td>√（VODプリロールのみ）</td> 
  </tr>
  <tr>
   <td>早期広告出口</td> 
   <td>ライブ</td> 
   <td>√ </td> 
   <td>非対応</td> 
  </tr>
  <tr>
   <td>ルールベースのクリエイティブVOD +ライブの優先順位付け</td> 
   <td>VOD + Live</td> 
   <td>√ </td> 
   <td>非対応</td> 
  </tr>
  <tr>
   <td>CRSルール </td> 
   <td>VOD + Live</td> 
   <td>√ </td> 
   <td>非対応</td> 
  </tr>
 </tbody>
</table>

## コンテンツ保護機能{#content-protection-features}

| **機能** | **コンテンツタイプ** | **HLS** | **DASH** |
|---|---|---|---|
| AES暗号化 | VOD + Live | √ | √（VODのみ） |
| AES暗号化の例 | VOD + Live | √ |  |
| トークン化されたストリーム | VOD + Live | √ |  |
| DRM | VOD + Live | Primetime DRMのみ(将来：Widevine) | Widevineのみ |
| 外部再生(RBOP) | VOD + Live | Primetime DRMのみ | 非対応 |
| ライセンスのローテーション | VOD + Live | Primetime DRMのみ | 非対応 |
| キーの回転 | VOD + Live | Primetime DRMのみ | 非対応 |

### 統合機能{#integration-features}

| **機能** | **コンテンツタイプ** | **HLS** | **DASH** |
|---|---|---|---|
| Adobe AnalyticsVHL統合 | VOD + Live | √ | √ |
| 請求 | VOD + Live | √ | 非対応 |

## サポートされていない機能{#features-not-supported}

このバージョンのTVSDKは、以下をサポートしていません。

* 広告のブラックアウト。
* トリック再生でのスローモーション。
* MP4コンテンツを使用したシークとトリック再生
* MP4メインコンテンツを含む広告挿入
* 広告の再生中にシークします。
* オーディオ専用メディアを含む広告の再生。

## 既知の問題と制限{#known-issues-and-limitations}

このバージョンのTVSDKには、次の問題があります。

* デバイス固有(Samsung Galaxy Tab 4)のクラッシュVOD DRM LBAとauditudeを使用し、広告をクリックする
* ポストロール広告は、特定のコンテンツに対しては再生されません。
* クローズドキャプションをCJK言語に設定しても機能しません。
* ビデオは、VODとライブの両方の間で自動的にトリックモードから出る場合があります。
* VHL — オフセットからコンテンツを開始すると、誤ったハートビート呼び出しが送信されます。
* VPAID広告が再生される場合、イベント:type:play広告に対するVHLハートビート呼び出しが見つかりません。
* adBreakPolicy SKIPが選択されている場合でも、プリロール広告が再生されます。
* 完了状態に切り替えると、ポストロール広告に対してはSKIP adBreakPolicyを使用して再生状態に戻ります。

ビデオがない場合、ビューポートの寸法はなく、ビューポートの寸法がない場合は、キャプションのグラフィックを表示できません。

## 役立つリソース{#helpful-resources}

* [Adobe Primetimeラーニングとサポート](https://helpx.adobe.com/support/primetime.html)のページにある完全なヘルプドキュメントを参照してください。