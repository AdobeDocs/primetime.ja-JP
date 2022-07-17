---
title: Android 向け TVSDK 2.4.1 リリースノート
description: TVSDK 2.4.1 for Android リリースノートでは、 TVSDK Android 2.4.1 の新機能とサポートされる機能、既知の問題と制限事項について説明します。
topic-tags: release-notes
products: SG_PRIMETIME
exl-id: 3de09048-ae32-43b4-a019-34b217931a4c
source-git-commit: 3b051c3188c81673129e12dfeb573aaf85c15c97
workflow-type: tm+mt
source-wordcount: '1962'
ht-degree: 0%

---

# Android 向け TVSDK 2.4.1 リリースノート {#tvsdk-for-android-release-notes}

TVSDK 2.4.1 for Android リリースノートでは、 TVSDK Android 2.4.1 の新機能とサポートされる機能、既知の問題と制限事項について説明します。

## TVSDK Android 2.4.1 {#tvsdk-android}

Adobeは、Android 向け TVSDK 2.4.1 をリリースしています。

このバージョンの TVSDK を使用するには、システムが次のページで説明されている要件を満たしていることを確認します。 [必要システム構成](https://helpx.adobe.com/content/dam/help/en/primetime/programming-guides/psdk_android_2.5.pdf#page=6).

ドキュメントは次の場所にあります。

・ Android ヘルプ用オンラインヘルプシステム TVSDK 2.4

・ [Android Java API 用 Javadocs TVSDK 2.4](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.4/index.html)

Javadoc は TVSDK のソースコードから直接自動的に生成されるので、究極の典拠となります。

・ [C++ API ドキュメント Android C++ API 用 TVSDK 2.4](https://help.adobe.com/en_US/primetime/api/psdk/cpp_2.4/namespaces.html)

各 Java クラスには対応する C++クラスがあり、C++ドキュメントには Javadoc よりも説明が多い資料が含まれているので、Java API の詳細については、C++のドキュメントを参照してください。

・移行ガイド ([Android 向け TVSDK 2.4 移行ガイド](../migration-guides/tvsdk-14-25-android.md))

このガイドでは、TVSDK 1.4 に基づくアプリケーションを TVSDK 2.4 に基づくアプリケーションに移行するために変更する必要がある事項を説明します。

## 新機能 {#new-features}

Android 向け TVSDK 2.4.1 は、以前のバージョンと比べて多くのパフォーマンスを向上させました。 高品質の表示エクスペリエンスを提供します。

このバージョンには、バージョン 2.4 および 2.4.1 のすべての機能が含まれており、非推奨（廃止予定）の機能はありません。

バージョン 2.4.1 の主な新機能を次に示します。

* HLS バージョン 4 の機能

   * **ビデオ再生** （再生、一時停止、シーク）ライブ、リニアおよび VOD ストリームのプレーヤーコントロールを使用します。
   * **クローズドキャプション。** TVSDK は、フォント、フォントサイズ、色、背景の選択肢を持つクローズドキャプションを表示できま608/708。 また、ロールアップキャプションを含むビデオをサポートし、使用可能な場合は言語トラック間で切り替えることもできます。
   * **トリック再生モード** は、I-Frame を使用する HLS ストリームの早送りと巻き戻しをサポートします。 すべてのビデオ再生コントロールは、コンテンツで機能します。 スローモーション（前方）は、0 ～ 1 のレートの外部ビデオ再生モードで使用できます。
   * **可変ビットレート (ABR)** を使用すると、再生する同じコンテンツストリームの複数のバージョンの中から、ネットワークやその他の条件に基づいて、どのバージョンをプレーヤーが動的に選択できます。 動的に、またはマニフェストファイルで、積極的、中程度、保守的な選択ポリシーの中から選択するようにパラメーターを設定できます。
   * **バイト範囲** 1 つの TS ファイルに複数の TS セグメントを含めることができます。
   * **代替オーディオレンディション** プレーヤーで使用可能なオーディオトラック間を切り替えるようにします。
   * **ID3 のサポート。** TVSDK は、アーティスト名、タイトル、アルバムなど、ID3 オーディオメタデータを含む HLS オーディオおよびビデオストリームを再生できます。
   * **フェイルオーバー。 ** TVSDK は、ホストサーバー、プレイリストファイル、セグメントに障害が発生した場合でも、中断されない再生を継続する方法を使用します。
   * **マルチチャネルオーディオパススルー (DD+)。** TVSDK は、Dolby Digital Plus オーディオ (E-AC3) データをサポートハードウェアに渡すことができます。

* コンテンツ保護機能

   * **HLS の DRM。** すべてのビデオ再生 API は、Adobeアクセスで保護された暗号化されたビデオコンテンツで動作します。 次の DRM 機能がサポートされています。

      * ライセンスのローテーション
      * キーの回転
      * ライセンスのキャッシュ
      * ポリシー時間
      * 静脈回転

* **AES 128 再生** TVSDK は、キーサイズが 128 ビットの高度な暗号化標準 (AES)HLS コンテンツを再生できます。
* **保護 HLS(PHLS)** には、ライブストリームや VOD ストリーム用の HLS 上での軽量な DRM を可能にする、事前に作成された DRM ポリシーの限られたセットと、Adobeアクセスのサブセットが用意されています。

* 広告/代替コンテンツおよび収益化機能

   * **サーバーサイドで挿入された広告のトラッキング。** TVSDK は、Ad Cloud Ad Insertion サービスによって挿入されたAdobeを追跡できます。 VOD およびライブ/リニアストリームの VAST2、VAST3、VMAP 形式のリニア広告をサポートしています。
   * **カスタム HLS タグ。** TVSDK は、そのを使用します。 `MediaPlayerConfig` クラスを使用して、カスタム HLS タグがストリームに表示されたときにプレーヤーアプリケーションに通知できるようにします。
   * **クライアント側の広告の挿入。** Auditude 広告挿入ライブラリは、Adobe Auditudeサーバーと連携して、ライブ、リニア、VOD コンテンツへの、プリロール、ミッドロール、ポストロールの各位置で動的に挿入する広告を解決します。
   * **カスタム広告リゾルバー。** この `ContentResolver, OpportunityGenerator,` および `MediaPlayerClientFactory` インターフェイスを使用すると、カスタム広告/代替コンテンツリゾルバーを実装し、TVSDK と連携するためのカスタムオポチュニティディテクターを登録できます。 この `TestAdResolver` および `AuditudeResolver` クラスは、コンテンツリゾルバーを実装する C++の例を提供します。 JavaScript の例については、次を参照してください。 `samples/jspsdk/testapp/psdk.js`.
   * **広告の動作が一貫している。** 以下を使用： `AdPolicySelector` インターフェイスを使用して、コンテンツに広告が存在する場合のシークやトリック再生などの操作で、すべてのプレーヤーで一貫した動作を有効にします。 独自のを実装しない場合、 TVSDK は `DefaultAdPolicySelector`.
   * **C3 広告を削除または置き換えます。** 適切な TVSDK API を使用して、カスタムコンテンツ範囲を削除し、追加の準備作業を行わずに新しい広告を動的に挿入します。 これは、ライブ/リニアコンテンツがブロードキャストされ、クリーンアップをおこなわずに即座にオンデマンドで使用可能にする場合に便利です。

バージョン 2.4 の主な新機能を次に示します。

* **VOD の即時オンとライブ** 即時オンを有効にすると、 TVSDK は、再生が開始する前にメディアを初期化し、バッファリングします。 これは、 `MediaPlayerItemLoader` インスタンスをバックグラウンドで同時にバッファリングすることができます。 ユーザーがチャネルを変更し、ストリームが適切にバッファリングされると、新しいチャネルでの再生が直ちに開始します。 TVSDK 2.4 は、ライブストリームのインスタントオンもサポートしています。 ライブストリームは、ライブウィンドウが移動すると再バッファリングされます。

* **パフォーマンスの向上**新しい TVSDK 2.4 アーキテクチャにより、次のような様々なパフォーマンスの向上が実現します。

   * **サブセグメント化** - TVSDK は、各フラグメントのサイズをできるだけ小さくして、再生を開始します。
   * **並列の広告ダウンロード** - TVSDK は、広告が広告ブレークをヒットする前に、コンテンツの再生と並行して広告をプリフェッチし、広告とコンテンツのシームレスな再生を可能にします。
   * **遅延広告解決**  — この機能を使用すると、再生を開始する前に、非プリロール広告の解決を待たずに、起動時間を短縮できます。 シークやトリック再生などの API は、すべての広告が解決されるまで、引き続き使用できません。

* **MP4 コンテンツ再生**

このバージョンの TVSDK では、MP4 をメインコンテンツとして再生できます。

* **永続的なネットワーク接続**

TVSDK は、再利用可能なネットワーク接続のセットを維持するので、ネットワークリクエストごとにネットワーク接続を作成して破棄するオーバーヘッドは発生しません。

* **解像度ベースの出力保護**

この機能は、再生の制限を特定の解像度に結び付け、DRM コントロールをより詳細に設定します。

* **可変ビットレート (ABR) を使用したトリック再生**

この機能を使用すると、 TVSDK は、トリック再生モード時に iFrame ストリームを切り替えることができます。 iFrame 以外のプロファイルを使用して、低速でトリック再生を実行できます。

* **よりスムーズなトリック再生**

以下の改善により、ユーザーエクスペリエンスが向上します。

・帯域幅とバッファプロファイルに基づく、トリック再生中の適応ビットレートおよびフレームレートの選択

・最大 30 fps の高速再生を実現するには、IDR ストリームの代わりにメインストリームを使用します。

* **ABR ロジックの改善**

新しい ABR ロジックは、バッファ長、バッファ長の変化率、測定された帯域幅に基づいています。 これにより、ABR は帯域幅が変動する際に適切なビットレートを選択し、また、バッファ長の変化率を監視することで、ビットレート切り替えが実際に発生する回数を最適化します。

* **請求**

TVSDK は、顧客の販売契約に従って自動的に指標を収集し、課金のために必要な定期的な使用状況レポートを生成します。 TVSDK は、すべてのストリーム開始イベントで、Adobe Analytics Data Insertion API を使用して、コンテンツタイプ、広告挿入有効フラグ、drm 有効フラグなどの請求指標を請求可能なストリームの期間に基づいてAdobe Analytics Primetime 所有のレポートスイートに送信します。 これは、お客様独自のAdobe Analyticsレポートスイートやサーバー呼び出しに干渉したり、含まれたりすることはありません。 この請求使用状況レポートは、リクエストに応じて定期的にお客様に送信されます。 これは、使用状況の請求のみをサポートする請求機能の第 1 段階です。 ドキュメントに記載されている API を使用して、販売契約に基づいて設定できます。

## サポートされる機能 {#supported-features}

Android 用 TVSDK 2.4 は、ビデオアプリケーションに機能を追加するために実装できる多くの機能をサポートしています。

>[!NOTE]
>
>以下の機能マトリックスの表では、√は、この機能が現在のリリースでサポートされていることを意味します。

### コア再生機能 {#core-playback-features}

| **機能** | **コンテンツタイプ** | **HLS** | **ダッシュ** |
|---|---|---|---|
| 一般的な再生（再生、一時停止、シーク） | VOD + Live | √ | √ （VOD のみ） |
| FER — 一般的な再生（再生、一時停止、シーク） | FER VOD | √ | サポートなし |
| MP3 | VOD | サポートなし | サポートなし |
| MP4 コンテンツ再生 | VOD | √ | √ |
| 適応ビットレート切り替えロジック | VOD + Live | √ | サポートなし |
| オーディオのみ再生 | VOD + Live | √ | サポートなし |
| クローズドキャプション — 608/708 | VOD + Live | √ | √ （VOD のみ） |
| クローズドキャプション — WebVTT | VOD + Live | √ | √ （VOD のみ） |
| マニフェストのフェイルオーバー | VOD + Live | √ | √ （VOD のみ） |
| 高度なフェイルオーバー | VOD + Live | √ | √ （VOD のみ） |
| QoS とプレーヤーの通知 | VOD + Live | √ | √ （VOD のみ） |
| cookie ヘッダーのサポート | VOD + Live | √ | √ （VOD のみ） |
| カスタムヘッダーのサポート | VOD + Live | サポートなし | サポートなし |
| バッファ制御パラメータを設定 | VOD + Live | √ | √ （VOD のみ） |
| アダプティブビットレートコントロールの設定 | VOD + Live | √ | √ （VOD のみ） |
| カスタムマニフェストタグ (HLS)/イベントストリーム (DASH) | VOD + Live | √ | √ （VOD のみ） |
| 遅延バインドオーディオ | VOD + Live | √ | √ （VOD のみ） |
| 302 リダイレクト | VOD + Live | √ | √ （VOD のみ） |

### 高度な再生機能 {#advanced-playback-features}

<table> 
 <tbody>
  <tr>
   <td><strong>機能</strong></td> 
   <td><strong>コンテンツタイプ</strong></td> 
   <td><strong>HLS</strong></td> 
   <td><strong>ダッシュ</strong></td> 
  </tr>
  <tr>
   <td>オフセットの再生</td> 
   <td>ライブ</td> 
   <td>√</td> 
   <td>サポートなし</td> 
  </tr>
  <tr>
   <td>オーディオのみ再生</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>サポートなし</td> 
  </tr>
  <tr>
   <td>トリック再生 </td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>サポートなし</td> 
  </tr>
  <tr>
   <td>スムーズなトリック再生（ABR を使用）</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>サポートなし</td> 
  </tr>
  <tr>
   <td>ID3 解析 (HLS) /時間指定メタデータ (DASH)</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>サポートなし</td> 
  </tr>
  <tr>
   <td>ブラックアウト </td> 
   <td>VOD + Live</td> 
   <td>サポートなし</td> 
   <td>サポートなし</td> 
  </tr>
  <tr>
   <td>即時オン</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>サポートなし</td> 
  </tr>
  <tr>
   <td>
    <ul> 
     <li>Discontinuity Marker Support（HLS；不連続マーカーサポート） </li> 
     <li>複数ピリオド (DASH)</li> 
    </ul> </td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>サポートなし</td> 
  </tr>
  <tr>
   <td>302 リダイレクトの固定</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>√ （VOD のみ）</td> 
  </tr>
  <tr>
   <td>サムネールのスクラブ (Iframe およびJPEG)</td> 
   <td>VOD + Live</td> 
   <td>サポートなし</td> 
   <td>サポートなし</td> 
  </tr>
  <tr>
   <td>ストリームの整合性 </td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>サポートなし</td> 
  </tr>
 </tbody>
</table>

### コアAd Insertion機能 (CSAI) {#core-ad-insertion-features-csai}

| **機能** | **コンテンツタイプ** | **HLS** | **ダッシュ** |
|---|---|---|---|
| 一般再生、広告有効 | VOD + Live | √ | √ （VOD プリロールのみ） |
| 広告が有効な FER コンテンツ | VOD | √ | サポートなし |
| デフォルトの広告動作 | VOD + Live | √ | √ （VOD プリロールのみ） |
| VAST 2.0/3.0 | VOD + Live | √ | √ （VOD プリロールのみ） |
| VMAP 1.0 | VOD + Live | √ | √ （VOD プリロールのみ） |
| MP4 広告 | VOD + Live | √ （CRS から） | √（CRS から、プリロールのみ） |

### 高度なAd Insertion機能 (CSAI) {#advanced-ad-insertion-features-csai}

<table> 
 <tbody>
  <tr>
   <td><strong>機能</strong></td> 
   <td><strong>コンテンツタイプ</strong></td> 
   <td><strong>HLS</strong></td> 
   <td><strong>ダッシュ</strong></td> 
  </tr>
  <tr>
   <td>広告を有効にしたトリック再生</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>サポートなし</td> 
  </tr>
  <tr>
   <td>広告のみ </td> 
   <td>VOD</td> 
   <td>サポートなし</td> 
   <td>サポートなし</td> 
  </tr>
  <tr>
   <td>ターゲティングパラメーター</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>√ （VOD プリロールのみ）</td> 
  </tr>
  <tr>
   <td>カスタムパラメーター</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>√ （VOD プリロールのみ）</td> 
  </tr>
  <tr>
   <td>カスタム広告動作</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>√ （VOD プリロールのみ）</td> 
  </tr>
  <tr>
   <td>カスタム広告タグ</td> 
   <td>ライブ</td> 
   <td>√ </td> 
   <td>サポートなし</td> 
  </tr>
  <tr>
   <td>カスタム広告リゾルバー</td> 
   <td>VOD + Live</td> 
   <td>√ </td> 
   <td>サポートなし</td> 
  </tr>
  <tr>
   <td>Freewheel Custom Ad Resolver</td> 
   <td>VOD</td> 
   <td>サポートなし</td> 
   <td>サポートなし</td> 
  </tr>
  <tr>
   <td>C3 広告の置き換え </td> 
   <td>VOD + Live</td> 
   <td>√ </td> 
   <td>サポートなし</td> 
  </tr>
  <tr>
   <td>遅延広告読み込み</td> 
   <td>VOD</td> 
   <td>√ </td> 
   <td>サポートなし</td> 
  </tr>
  <tr>
   <td>
    <ul> 
     <li>Discontinuity マーカーのサポート — SSAI(HLS) </li> 
     <li>複数ピリオド (DASH)</li> 
    </ul> </td> 
   <td>VOD + Live</td> 
   <td>√ </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>コンパニオン広告、バナー広告、クリック可能な広告</td> 
   <td>VOD + Live</td> 
   <td>√ </td> 
   <td>√ （VOD プリロールのみ）</td> 
  </tr>
  <tr>
   <td>VPAID 2.0</td> 
   <td>VOD + Live</td> 
   <td>√ (JS) </td> 
   <td>√ （VOD プリロールのみ）</td> 
  </tr>
  <tr>
   <td>早期広告出口</td> 
   <td>ライブ</td> 
   <td>√ </td> 
   <td>サポートなし</td> 
  </tr>
  <tr>
   <td>ルールベースのクリエイティブ VOD とライブの優先順位付け</td> 
   <td>VOD + Live</td> 
   <td>√ </td> 
   <td>サポートなし</td> 
  </tr>
  <tr>
   <td>CRS ルール </td> 
   <td>VOD + Live</td> 
   <td>√ </td> 
   <td>サポートなし</td> 
  </tr>
 </tbody>
</table>

## コンテンツ保護機能 {#content-protection-features}

| **機能** | **コンテンツタイプ** | **HLS** | **ダッシュ** |
|---|---|---|---|
| AES 暗号化 | VOD + Live | √ | √ （VOD のみ） |
| AES 暗号化の例 | VOD + Live | √ |  |
| トークン化ストリーム | VOD + Live | √ |  |
| DRM | VOD + Live | Primetime DRM のみ ( 今後：Widevine) | Widevine のみ |
| 外部再生 (RBOP) | VOD + Live | Primetime DRM のみ | サポートなし |
| ライセンスのローテーション | VOD + Live | Primetime DRM のみ | サポートなし |
| キーの回転 | VOD + Live | Primetime DRM のみ | サポートなし |

### 統合の機能 {#integration-features}

| **機能** | **コンテンツタイプ** | **HLS** | **ダッシュ** |
|---|---|---|---|
| Adobe Analytics VHL 統合 | VOD + Live | √ | √ |
| 請求 | VOD + Live | √ | サポートなし |

## サポートされていない機能 {#features-not-supported}

このバージョンの TVSDK は、次の機能をサポートしていません。

* 広告のブラックアウト。
* トリック再生でのスローモーション。
* MP4 コンテンツでシークしてトリック再生します。
* MP4 メインコンテンツを使用した広告挿入
* 広告が再生中にシークします。
* オーディオのみのメディアでの広告の再生。

## 既知の問題と制限事項 {#known-issues-and-limitations}

このバージョンの TVSDK には、次の問題があります。

* デバイス固有 (Samsung Galaxy Tab 4) のクラッシュ VOD DRM LBA と監査でのクリックと広告
* ポストロール広告は、特定のコンテンツに対しては再生されません。
* クローズドキャプションを CJK 言語に設定しても機能しない。
* ビデオは、VOD とライブの両方の間で、自動的にトリックモードから出ることができます。
* VHL — オフセットからコンテンツを開始すると、誤ったハートビート呼び出しが送信されます。
* VPAID 広告が再生されると、VHL ハートビートがイベントの呼び出しを呼び出します:type:再生広告が見つかりません。
* adBreakPolicy SKIP が選択されている場合でも、プリロール広告が再生されます。
* プレーヤーは、完了状態に移行した後、ポストロール広告の SKIP adBreakPolicy を使用して再生状態に戻ります。

ビデオがない場合、ビューポートの寸法はなく、ビューポートの寸法がない場合、キャプションのグラフィックを表示できません。

## 参考リソース {#helpful-resources}

* 完全なヘルプドキュメントは、 [Adobe Primetimeラーニングとサポート](https://experienceleague.adobe.com/docs/primetime.html) ページ。
