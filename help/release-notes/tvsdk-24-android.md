---
title: Android向けTVSDK 2.4.1リリースノート
seo-title: Android向けTVSDK 2.4.1リリースノート
description: TVSDK 2.4.1 for Androidリリースノートでは、TVSDK Android 2.4.1の新機能およびサポートされる機能、および既知の問題と制限について説明します。
seo-description: TVSDK 2.4.1 for Androidリリースノートでは、TVSDK Android 2.4.1の新機能およびサポートされる機能、および既知の問題と制限について説明します。
uuid: 929fc577-e851-4e03-9201-13280cc6137a
topic-tags: release-notes
products: SG_PRIMETIME
discoiquuid: a6dbcc4a-9e14-4452-9004-b39ed13fad6f
translation-type: tm+mt
source-git-commit: e644e8497e118e2d03e72bef727c4ce1455d68d6

---


# Android向けTVSDK 2.4.1リリースノート {#tvsdk-for-android-release-notes}

TVSDK 2.4.1 for Androidリリースノートでは、TVSDK Android 2.4.1の新機能およびサポートされる機能、および既知の問題と制限について説明します。

## TVSDK Android 2.4.1 {#tvsdk-android}

アドビは、Android向けTVSDK 2.4.1をリリースします。

このバージョンのTVSDKを使用するには、お使いのシステムが必要システム構成に記載されている要件を満たしているこ [とを確認しま](https://helpx.adobe.com/content/dam/help/en/primetime/programming-guides/psdk_android_2.5.pdf#page=6)す。

ドキュメントは次の場所にあります。

・ Android向けオンラインヘルプシステムTVSDK 2.4ヘルプ

・ [Android Java API用Javadocs TVSDK 2.4](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.4/index.html)

Javadocは、TVSDKソースコードから直接自動的に生成されるので、究極の権限です。

・ [Android C++ API用C++ APIドキュメントTVSDK 2.4](https://help.adobe.com/en_US/primetime/api/psdk/cpp_2.4/namespaces.html)

各Javaクラスには対応するC++クラスがあり、C++ドキュメントにはJavadocよりも詳しい説明が含まれているので、Java APIの詳細については、C++のドキュメントを参照してください。

・移行ガイド([Android向けTVSDK 2.4移行ガイド](../migration-guides/tvsdk-14-25-android.md))

このガイドでは、TVSDK 1.4に基づくアプリケーションをTVSDK 2.4に基づくアプリケーションに移行するために変更する必要のある事項を説明します。

## 新機能 {#new-features}

Android向けTVSDK 2.4.1は、以前のバージョンと比べて多くのパフォーマンスが向上しています。 高品質の視聴環境を提供します。

このバージョンには、バージョン2.4および2.4.1のすべての機能が含まれ、非推奨の機能はありません。

バージョン2.4.1の主な新機能を次に示します。

* HLSバージョン4の機能

   * **ライブ** 、リニアおよびVODストリームのプレーヤーコントロールを使用したビデオ再生（再生、一時停止、シーク）。
   * **クローズドキャプション。** TVSDKは、フォント、フォントサイズ、色、背景を選択して、608/708のクローズドキャプションを表示できます。 また、ロールアップキャプションを含むビデオをサポートし、言語トラックが使用可能な場合はそれらを切り替えることもできます。
   * **トリック再生モードは** 、I-Frameを使用するHLSストリームの早送りと巻き戻しをサポートします。 すべてのビデオ再生コントロールがコンテンツで機能します。 0 ～ 1のレートの外部ビデオ再生モードでは、スローモーション（前方）を使用できます。
   * **アダプティブビットレート(ABR)を使用すると** 、プレイヤーは、ネットワークやその他の条件に基づいて、再生する同じコンテンツストリームの複数のバージョンのうちどれを動的に選択するかを選択できます。 パラメーターを動的に、またはマニフェストファイル内で設定し、積極的、モデレート、保守的な選択ポリシーの中から選択できます。
   * **バイト範囲を使用すると** 、1つのTSファイルに複数のTSセグメントを含めることができます。
   * **代替オーディオレンディションを使用すると** 、プレーヤーは使用可能なオーディオトラックを切り替えることができます。
   * **ID3のサポート。** TVSDKは、アーティスト名、タイトル、アルバムなど、ID3オーディオメタデータを含むHLSオーディオストリームおよびビデオストリームを再生できます。
   * **フェイルオーバー。 **TVSDKは、ホストサーバー、プレイリストファイルおよびセグメントに障害が発生した場合でも、中断されない再生を継続する方法を使用します。
   * **マルチチャネルオーディオパススルー(DD+)。** TVSDKは、Dolby Digital Plusオーディオ(E-AC3)データをサポートするハードウェアに渡すことができます。

* コンテンツ保護機能

   * **HLSのDRM。** すべてのビデオ再生APIは、Adobe Accessで保護された暗号化されたビデオコンテンツで機能します。 次のDRM機能がサポートされています。

      * ライセンスのローテーション
      * キーの回転
      * ライセンスのキャッシュ
      * ポリシー時間
      * 静脈回転

* **AES 128再生。** TVSDKは、キーサイズが128ビットの高度な暗号化標準(AES)HLSコンテンツを再生できます。
* **Protected HLS(PHLS)は** 、Adobe Accessが提供するもののサブセットである、事前に構築されたDRMポリシーの限定されたセットを提供し、ライブストリームおよびVODストリームに対してHLS上の軽量なDRMを有効にします。

* 広告/代替コンテンツと収益化機能

   * **サーバー側で挿入された広告の追跡。** TVSDKは、Adobe Cloud広告挿入サービスによって挿入された広告を追跡できます。 VODストリームおよびライブ/リニアストリーム用に、VAST2、VAST3およびVMAP形式のリニア広告をサポートします。
   * **カスタムHLSタグ。** TVSDKは、そのクラスを使用し `MediaPlayerConfig` て、カスタムHLSタグがストリームに表示されたときにプレイヤーアプリケーションに通知できるようにします。
   * **クライアント側の広告挿入。** Auditude広告挿入ライブラリは、Adobe Auditudeサーバーと連携して、プリロール、ミッドロールまたはポストロールの位置で、ライブ、リニアおよびVODコンテンツに動的に挿入する広告を解決します。
   * **カスタム広告リゾルバー。** およびイ `ContentResolver, OpportunityGenerator,` ンターフェイス `MediaPlayerClientFactory` を使用すると、カスタム広告/代替コンテンツリゾルバーを実装し、TVSDKと連携するカスタムオポチュニティディテクターを登録できます。 およびク `TestAdResolver` ラス `AuditudeResolver` は、コンテンツリゾルバーの実装のC++の例を提供します。 JavaScriptの例は、を参照してくださ `samples/jspsdk/testapp/psdk.js`い。
   * **一貫した広告動作。** インターフェイス `AdPolicySelector` を使用して、コンテンツ内に広告が存在する場合のシークやトリック再生などの操作に関して、すべてのプレーヤーで一貫した動作を有効にします。 独自のを実装しない場合、TVSDKはを使用します `DefaultAdPolicySelector`。
   * **C3広告の削除/置換** 適切なTVSDK APIを使用して、カスタムコンテンツ範囲を削除し、追加の準備作業を行わずに新しい広告を動的に挿入します。 これは、ライブ/リニアコンテンツがブロードキャストされ、クリーンアップを行わずにオンデマンドで即座に使用できるようにする場合に便利です。

次に、バージョン2.4の主な新機能を示します。

* **VODおよびライブの即時オン** ：即時オンを有効にすると、TVSDKは再生開始前にメディアを初期化し、バッファリングします。 複数のインスタンスをバックグラウン `MediaPlayerItemLoader` ドで同時に起動できるので、複数のストリームをバッファーできます。 ユーザーがチャネルを変更し、ストリームが正しくバッファーされると、新しいチャネルでの再生がすぐに開始されます。 TVSDK 2.4は、ライブストリームのインスタントオンもサポートします。 ライブストリームは、ライブウィンドウの移動時に再バッファリングされます。

* **パフォーマンスの向上**新しいTVSDK 2.4アーキテクチャにより、様々なパフォーマンスが向上しました。

   * **サブセグメント** - TVSDKは、各フラグメントのサイズをさらに小さくして、可能な限り早く再生を開始します。
   * **並行広告ダウンロード** - TVSDKは、広告の時間をヒットする前に、コンテンツの再生と並行して広告をプリフェッチするので、広告とコンテンツのシームレスな再生を可能にします。
   * **遅延広告の解決** — この機能を使用すると、再生を開始する前に、非プリロール広告の解決を待たずに、起動時間が短くなります。 シークやトリック再生などのAPIは、すべての広告が解決されるまで使用できません。

* **MP4コンテンツの再生**

このバージョンのTVSDKは、MP4の再生をメインコンテンツとしてサポートしています。

* **永続的なネットワーク接続**

TVSDKは、再利用可能なネットワーク接続のセットを維持するので、各ネットワーク要求のネットワーク接続を作成および破棄するオーバーヘッドは発生しません。

* **解像度ベースの出力保護**

この機能は、再生の制限を特定の解像度に関連付け、DRMコントロールをより詳細に設定します。

* **可変ビットレート(ABR)を使用したトリック再生**

この機能を使用すると、TVSDKは、トリック再生モードでiFrameストリームを切り替えることができます。 iFrame以外のプロファイルを使用して、低速でトリック再生を行うことができます。

* **スムーズなトリック再生**

以下の改善により、ユーザーエクスペリエンスが向上しました。

・トリック再生中の可変ビットレートとフレームレートの選択（帯域幅とバッファープロファイルに基づく）

・最大30 fpsの高速再生を行うには、IDRストリームの代わりにメインストリームを使用します。

* **ABRロジックの改善**

新しいABRロジックは、バッファーの長さ、バッファーの長さの変化率および測定された帯域幅に基づきます。 これにより、ABRは帯域幅が変動する場合に適切なビットレートを選択し、バッファー長が変化するレートを監視することで、ビットレート切り替えが実際に発生する回数を最適化します。

* **請求**

TVSDKは、顧客の販売契約に従って指標を自動的に収集し、課金の目的で必要な定期的な使用状況レポートを生成します。 TVSDKは、すべてのストリーム開始イベントで、Adobe Analyticsデータ挿入APIを使用して、コンテンツタイプ、広告挿入が有効なフラグ、および請求可能なストリームの継続時間に基づくdrmが有効なフラグなどの請求指標をAdobe Analytics Primetimeが所有するレポートスイートに送信します。 これは、お客様のAdobe Analyticsレポートスイートやサーバー呼び出しに影響を及ぼしたり、含まれたりすることはありません。 リクエストに応じて、この請求の使用状況レポートが定期的に顧客に送信されます。 これは、利用状況の請求のみをサポートする請求機能の最初のフェーズです。 ドキュメントで説明されているAPIを使用して、販売契約に基づいて設定できます。

## サポートされる機能 {#supported-features}

TVSDK for Android 2.4は、ビデオアプリケーションに機能を追加するために実装できる多数の機能をサポートしています。

>[!NOTE]
>
>以下の機能マトリックスの表で、√とは、その機能が現在のリリースでサポートされていることを意味します。

### コア再生機能 {#core-playback-features}

| **機能** | **コンテンツタイプ** | **HLS** | **DASH** |
|---|---|---|---|
| 一般再生（再生、一時停止、シーク） | VOD + Live | √ | √（VODのみ） |
| FER — 一般再生（再生、一時停止、シーク） | FER VOD | √ | 未サポート |
| MP3 | VOD | 未サポート | 未サポート |
| MP4コンテンツ再生 | VOD | √ | √ |
| 可変ビットレート切り替えロジック | VOD + Live | √ | 未サポート |
| オーディオのみ再生 | VOD + Live | √ | 未サポート |
| クローズドキャプション — 608/708 | VOD + Live | √ | √（VODのみ） |
| クローズドキャプション — WebVTT | VOD + Live | √ | √（VODのみ） |
| マニフェストのフェイルオーバー | VOD + Live | √ | √（VODのみ） |
| 高度なフェイルオーバー | VOD + Live | √ | √（VODのみ） |
| QoSとプレイヤー通知 | VOD + Live | √ | √（VODのみ） |
| cookieヘッダーのサポート | VOD + Live | √ | √（VODのみ） |
| カスタムヘッダーのサポート | VOD + Live | 未サポート | 未サポート |
| バッファ制御パラメータの設定 | VOD + Live | √ | √（VODのみ） |
| 可変ビットレートコントロールの設定 | VOD + Live | √ | √（VODのみ） |
| カスタムマニフェストタグ(HLS)/イベントストリーム(DASH) | VOD + Live | √ | √（VODのみ） |
| 遅延バウンドオーディオ | VOD + Live | √ | √（VODのみ） |
| 302リダイレクト | VOD + Live | √ | √（VODのみ） |

### 高度な再生機能 {#advanced-playback-features}

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
   <td>未サポート</td> 
  </tr>
  <tr>
   <td>オーディオのみ再生</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>未サポート</td> 
  </tr>
  <tr>
   <td>トリック再生 </td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>未サポート</td> 
  </tr>
  <tr>
   <td>スムーズトリック再生（ABRを使用）</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>未サポート</td> 
  </tr>
  <tr>
   <td>ID3解析(HLS)/時間指定メタデータ(DASH)</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>未サポート</td> 
  </tr>
  <tr>
   <td>ブラックアウト </td> 
   <td>VOD + Live</td> 
   <td>未サポート</td> 
   <td>未サポート</td> 
  </tr>
  <tr>
   <td>即時オン</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>未サポート</td> 
  </tr>
  <tr>
   <td>
    <ul> 
     <li>Discontinuity Marker Support(HLS) </li> 
     <li>複数ピリオド(DASH)</li> 
    </ul> </td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>未サポート</td> 
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
   <td>未サポート</td> 
   <td>未サポート</td> 
  </tr>
  <tr>
   <td>ストリームの整合性 </td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>未サポート</td> 
  </tr>
 </tbody>
</table>

### コア広告挿入機能(CSAI) {#core-ad-insertion-features-csai}

| **機能** | **コンテンツタイプ** | **HLS** | **DASH** |
|---|---|---|---|
| 一般再生、広告有効 | VOD + Live | √ | √（VODプリロールのみ） |
| 広告が有効なFERコンテンツ | VOD | √ | 未サポート |
| デフォルトの広告動作 | VOD + Live | √ | √（VODプリロールのみ） |
| VAST 2.0/3.0 | VOD + Live | √ | √（VODプリロールのみ） |
| VMAP 1.0 | VOD + Live | √ | √（VODプリロールのみ） |
| MP4広告 | VOD + Live | √（CRSから） | √（CRS、プリロールのみ） |

### 高度な広告挿入機能(CSAI) {#advanced-ad-insertion-features-csai}

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
   <td>未サポート</td> 
  </tr>
  <tr>
   <td>広告のみ </td> 
   <td>VOD</td> 
   <td>未サポート</td> 
   <td>未サポート</td> 
  </tr>
  <tr>
   <td>ターゲット設定パラメーター</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>√（VODプリロールのみ）</td> 
  </tr>
  <tr>
   <td>カスタムパラメータ</td> 
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
   <td>未サポート</td> 
  </tr>
  <tr>
   <td>カスタム広告リゾルバー</td> 
   <td>VOD + Live</td> 
   <td>√ </td> 
   <td>未サポート</td> 
  </tr>
  <tr>
   <td>フリーホイールカスタム広告リゾルバー</td> 
   <td>VOD</td> 
   <td>未サポート</td> 
   <td>未サポート</td> 
  </tr>
  <tr>
   <td>C3広告の置換 </td> 
   <td>VOD + Live</td> 
   <td>√ </td> 
   <td>未サポート</td> 
  </tr>
  <tr>
   <td>遅延広告読み込み</td> 
   <td>VOD</td> 
   <td>√ </td> 
   <td>未サポート</td> 
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
   <td>未サポート</td> 
  </tr>
  <tr>
   <td>ルールベースのクリエイティブVOD +ライブの優先順位付け</td> 
   <td>VOD + Live</td> 
   <td>√ </td> 
   <td>未サポート</td> 
  </tr>
  <tr>
   <td>CRSルール </td> 
   <td>VOD + Live</td> 
   <td>√ </td> 
   <td>未サポート</td> 
  </tr>
 </tbody>
</table>

## コンテンツ保護機能 {#content-protection-features}

| **機能** | **コンテンツタイプ** | **HLS** | **DASH** |
|---|---|---|---|
| AES暗号化 | VOD + Live | √ | √（VODのみ） |
| AES暗号化の例 | VOD + Live | √ |  |
| トークン化ストリーム | VOD + Live | √ |  |
| DRM | VOD + Live | Primetime DRMのみ(将来：Widevine) | Widevineのみ |
| 外部再生(RBOP) | VOD + Live | Primetime DRMのみ | 未サポート |
| ライセンスローテーション | VOD + Live | Primetime DRMのみ | 未サポート |
| キーの回転 | VOD + Live | Primetime DRMのみ | 未サポート |

### 統合機能 {#integration-features}

| **機能** | **コンテンツタイプ** | **HLS** | **DASH** |
|---|---|---|---|
| Adobe Analytics VHLの統合 | VOD + Live | √ | √ |
| 請求 | VOD + Live | √ | 未サポート |

## サポートされていない機能 {#features-not-supported}

このバージョンのTVSDKは、次の機能をサポートしていません。

* 広告のブラックアウト。
* トリック再生でのスローモーション。
* MP4コンテンツでシークしてトリック再生します。
* MP4のメインコンテンツを使用した広告挿入。
* 広告の再生中にシークします。
* オーディオ専用メディアを含む広告の再生。

## 既知の問題と制限 {#known-issues-and-limitations}

このバージョンのTVSDKには、次の問題があります。

* デバイス固有(Samsung Galaxy Tab 4)で、auditudeを使用してVOD DRM LBAをクラッシュし、広告をクリックします。
* ポストロール広告は、特定のコンテンツに対しては再生されません。
* クローズドキャプションをCJK言語に設定しても機能しません。
* ビデオは、VODとライブの両方の間で自動的にトリックモードから取り出される場合があります。
* VHL — オフセットからコンテンツを開始すると、誤ったハートビート呼び出しが送信されます。
* VPAID広告が再生されると、event:type:play広告に対するVHLハートビート呼び出しが見つかりません。
* adBreakPolicy SKIPが選択されている場合でも、プリロール広告が再生されます。
* 完了状態に切り替えると、ポストロール広告に対してSKIP adBreakPolicyを使用して再生状態に戻ります。

ビデオがない場合、ビューポートの寸法はなく、ビューポートの寸法がない場合は、キャプションのグラフィックを表示できません。

## 役立つリソース {#helpful-resources}

* 完全なヘルプドキュメントは、 [Adobe Primetimeのラーニングとサポートページで参照してください](https://helpx.adobe.com/support/primetime.html) 。