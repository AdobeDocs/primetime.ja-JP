---
title: ブラウザー TVSDK 2.4 リリースノート
description: ブラウザー TVSDK 2.4 リリースノートでは、Browser TVSDK 2.4 の新機能、サポートされる機能、サポートされない機能、および既知の問題について説明します。
contentOwner: dekalra
topic-tags: release-notes
products: SG_PRIMETIME
exl-id: 83fdf530-5cbb-41d9-ab2a-28e117f04488
source-git-commit: 3b051c3188c81673129e12dfeb573aaf85c15c97
workflow-type: tm+mt
source-wordcount: '6812'
ht-degree: 0%

---

# ブラウザー TVSDK 2.4 リリースノート {#browser-tvsdk-release-notes}

ブラウザー TVSDK 2.4 リリースノートでは、Browser TVSDK 2.4 の新機能、サポートされる機能、サポートされない機能、および既知の問題について説明します。

## はじめに {#introduction}

ブラウザー TVSDK は、高度なビデオ再生機能、コンテンツ保護、広告をブラウザーベースのビデオプレーヤーアプリケーションに追加できるツールキットです。

ブラウザー TVSDK 2.4 は、ブラウザーベースのビデオアプリケーションを構築するための JavaScript API を提供し、次のモードでの再生のサポートを含みます。

* HTML5 のみ
* HTML5 （自動フラッシュフォールバックを使用）
* Flashが常に

このリリースには、次の情報が含まれています。

・ [ブラウザー TVSDK API ドキュメント](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html).

・ [ブラウザー TVSDK プログラミングガイド](https://helpx.adobe.com/content/dam/help/en/primetime/programming-guides/psdk_browser-tvsdk.pdf).

・ [1.4 DHLS 用 TVSDK からブラウザー TVSDK 2.4 への移行ガイド](https://helpx.adobe.com/primetime/migration-guides/tvsdk-14-dhls-browser-tvsdk-24.html).

・ [ブラウザー TVSDK 2.4.6 からバージョン 2.4.7 への変換](https://helpx.adobe.com/primetime/conversion-guides/browser-tvsdk-246-to-247-for-javascript.html).

・ビルドに含まれる参照実装。

>[!NOTE]
>
>*このリリースのセキュリティに関する考慮事項の完全なリストについては、セキュリティに関する考慮事項を参照してください。

## 新機能とサポートされる機能 {#what-s-new-and-supported-features}

このリリースの Browser TVSDK は、ビデオアプリケーションを拡張するために使用できる新機能を提供します。

**2.4.12 の新機能更新（ビルド 204）**

Browser TVSDK 2.4.12 の更新（ビルド 204）の一部として、次の追加が使用できます。

* AdobePSDK.MediaPlayer のボリューム API の実装が変更され、再生がミュートされたときにiOSで自動再生できるようになりました。

・新しい API、 `auditudeSettings.ignoreVPAIDAds`は、Auditude サーバーから受信した VPAID 広告を無視できるようにするために追加されます。 この API は、Flashフォールバックでは機能しません。

**バージョン 2.4.11**

Browser TVSDK 2.4.11 リリースの一部として、次の機能強化および追加が可能です。

・ HLS ライブセグメントフェールオーバーは、MSE およびFlashのフォールバックモードでサポートされます。

・のサポート `AuditudeSettings.creativeRepackagingDomain` MSE でも API を利用できるようになりました。 以前は、フォールバックモードでのみFlashされていました。

・このリリースには、お客様の重大な問題に対する修正が含まれています。 詳しくは、 *修正された問題* リスト。

**バージョン 2.4.10**

Browser TVSDK 2.4.10 リリースの一部として、次の機能強化および追加が可能です。

・ TVSDK は、ログを有効または無効にする enableLogging() を提供します。 詳しくは、 [API ドキュメント](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html)を参照してください。

・ TVSDK は、Adobe Analyticsを使用する際に、デフォルトのチャプターをサポートしなくなりました。 アプリケーションを使用してチャプターを定義および管理します。

・このリリースには、お客様の重大な問題に対する修正が含まれています。 リストの「修正された問題」を参照してください。

**バージョン 2.4.9**

Browser TVSDK 2.4.9 リリースの一部として、次の機能強化および追加が可能です。

・時間不連続のある HLS VOD と Live ストリーム（不連続マーカーなし）がサポートされています。

・ ID3 v2.4.0 フレームは、HLS VOD およびライブストリーム用の Safari ビデオタグでサポートされています。

・セキュアな広告の読み込み実装では、広告サーバー呼び出しが API 設定に基づいてセキュアな HTTP にアップグレードされます。 詳しくは、 AdobePSDK.AdvertisingMetadata クラスと AdobePSDK.ForceHttpsAdConfiguration クラスを参照してください。 この機能は、Flashフォールバックモードではサポートされていません。

・ VAST 3.0 応答に関連する広告 ID 情報と拡張情報が、 TVSDK によってアプリケーションで使用できるようになり、広告の測定に Mort 統合を実装するために使用できます。 詳しくは、 AdobePSDK.NetworkAdInfo API を参照してください。 これは、Flashフォールバックモードではサポートされていません。

・ AdobePSDK.ForceHttpsConfiguration クラスは使用できなくなりました。 これは次の方法で成功します。

AdobePSDK.ForceHttpsAdConfiguration クラス。

・新しい API AdobePSDK.optimizeFlashCalls を使用して呼び出しを最適化し、Flashのフォールバックモードでの HLS 再生エクスペリエンスを改善できるようになりました。 これはデフォルトでは無効になっています。

**2.4.8 の新機能の更新（ビルド 6002）**

この更新には、お客様の重大な問題に対する修正が含まれています。 詳しくは、 *修正された問題*（リスト）。

**バージョン 2.4.8**

Browser TVSDK 2.4.8 リリースの一部として、次の機能強化および追加が可能です。

・ SDK は現在 Chrome EME に準拠しており、Chrome v58 以降で利用可能なベストプラクティスの変更に対応しています。 詳しくは、 [https://storage.googleapis.com/wvdocs/Chrome_EME_Changes_and_Best_Practices.pdf](https://storage.googleapis.com/wvdocs/Chrome_EME_Changes_and_Best_Practices.pdf)**

・ UI フレームワークは、Flash、広告のみ、ターゲティング情報ワークフローで HLS Access DRM をサポートするようになりました。

・ setDRMAuthenticateData API が UI フレームワークに追加されます。 AdobeAccess DRM で保護されたストリームを再生するには、この API を呼び出します。 または、 drmAuthenticateData 属性をプレーヤーで指定できます。 詳しくは、 [AdobePSDK.videoBehavior ](https://help.adobe.com/en_US/primetime/api/psdk/btvsdk-ui-framework/VideoBehavior.html)」を参照してください。

**バージョン 2.4.7**

バージョン 2.4.7 の新機能は次のとおりです。

・ UI フレームワークに UI コンフィギュレータを追加

プレーヤーは、次のいずれかの方法で設定できます。

・ JSON オブジェクトの使用

・ API の使用

JSON オブジェクトの生成に役立つよう、Browser TVSDK は、**UI Configurator **ツールを提供します。

このツールでは、様々な設定を選択し、「**設定をテスト**」をクリックして設定を確認し、「**設定をダウンロード**」をクリックして設定をダウンロードできます。 ファイルをダウンロードした後、このファイルの内容を JSON オブジェクトとして、ptp.videoPlayer API に渡すことができます。

・ UI フレームワークへの MediaPlayerItemConfig API の追加

advertisingMetadata、advertisingFactory、adSignalingMode、networkConfiguration、customRangeMetadata、useHardwareDecoder、subscribeTags、adTags、thumbnailScrubber、billingMetricsConfiguration などの様々な機能は、MediaPlayerPPe を使用して設定できます。 詳しくは、 [ブラウザー TVSDK API](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html)* * [ドキュメント](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html).

UI フレームワークでは、プレーヤー設定を通じてネットワーク設定を渡す方法が変更されています。

**バージョン 2.4.6**

`var player = ptp.videoPlayer(‘#videoHolder', {`

`player: {`

`networkConfiguration: <network configuration object>`

`}`

`};`

**バージョン 2.4.7**

`var player = ptp.videoPlayer(‘#videoHolder', {`

`player: {`

`mediaPlayerItemConfig: {`

`networkConfiguration: <network configuration object>`

`}`

`}`

`};`

* UI フレームワークでの DRM および Analytics ワークフローのサポート

DRM 設定と Analytics のトラッキングは、UI フレームワークを通じて有効にできます。

* の追加 `AdobePSDK.embedSWFinFullScreenDiv` API

この新しい API は、プレーヤーアプリケーションが FlashFallback.swf ファイルを埋め込むことのできる div を柔軟に選択できるようにします。

* 置換済み `getVersion`からの API `AdobePSDK.MediaPlayer` クラス `AdobePSDK.Version` TVSDK バージョン関連情報用のクラス。 詳しくは、 `AdobePSDK.Version` API [ここ](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/AdobePSDK.Version.html).

**バージョン 2.4.6**

バージョン 2.4.6 の新機能は次のとおりです。

* **サポートを参照**

Browserify を使用すると、ブラウザーで node.js スタイルモジュールを使用できます。 依存関係を定義し、バンドルを 1 つの JavaScript ファイルに参照できます。

* **請求**

課金の助けを借りて、ブラウザー TVSDK は、プレーヤー使用指標を収集し、Primetime の顧客に請求することができます。

>[!NOTE]
>
>Enum PSDKErrorCode の非推奨の enum MediaPlayer.Events と非推奨の定数は、バージョン 2.4.6 で削除されました。詳しくは、 [ブラウザー TVSDK 2.4.5 からバージョン 2.4.6 への変換](https://helpx.adobe.com/primetime/conversion-guides/browser-tvsdk-245-to-246-for-javascript.html).

**バージョン 2.4.5**

バージョン 2.4.5 の新機能は次のとおりです。

* **完全なイベント再生と広告**

   HLS フルイベント再生 (FER) ストリームで、広告の解像度と広告の動作がサポートされるようになりました。 このサポートを有効にするには、広告シグナリングモードをに設定します。 `MANIFEST_CUES` 作成時 `MediaPlayerItemConfig` オブジェクト。

* **MediaplayerView ScalePolicy のサポート**

   アプリケーション開発者は、 MediaplayerView scalePolicy プロパティを使用して、ビューに別の scalePolicy を指定できるようになりました。

* **アナモルフィックコンテンツのサポート**

   MSE とFlash再生を使用した場合、アナモフィックコンテンツの再生がサポートされるようになりました。

* **選択的適用`withCredentials`**

条件 `withCredentials` が true に設定されている場合、 `Access-Control-Allow-Origin` ヘッダーをワイルドカードに設定することはできません。 サーバーの応答に応じて、Browser TVSDK は、 `withCredentials` 属性。 このサポートの詳細については、 [ブラウザー TVSDK API ドキュメント](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html).

**バージョン 2.4.4**

バージョン 2.4.4 では、次の新機能が追加されました。

* **Chromecast サンプルアプリ**

このリリースでは、クライアントサイド広告を挿入した DASH VOD ストリームと DASH Widevine ストリームの再生を示す、送信者と受信者のアプリがサポートされます。

* **高度なフェイルオーバーのサポート**

このリリースでは、HLS VOD ストリームの高度なフェイルオーバー使用例（セグメントおよびサーバーのフェイルオーバー）をサポートしています。

**バージョン 2.4.3**

バージョン 2.4.3 では、次の新機能が追加されました。

* **DASH VOD のカスタムタグ**

   インラインカスタムタグ (Events) は、TimedMetadata オブジェクトとしてサブスクライブし、受け取ることができます。

* **拡張機能のないストリームの再生**

   拡張子のない HLS および DASH ストリームがサポートされるようになりました。 マニフェストファイルの場合、リソースの読み込み時に resourceType を指定する必要があります。 セグメントおよび VTT ファイルの場合、 Content-Type 応答ヘッダーを使用してコンテンツタイプが決定されます。

**バージョン 2.4.2**

バージョン 2.4.2 で追加された新機能は次のとおりです。

* **API パリティ**

API パリティの完全なリストについては、 [1.4 DHLS 用 TVSDK からブラウザー TVSDK 2.4 への移行ガイド](https://helpx.adobe.com/primetime/migration-guides/tvsdk-14-dhls-browser-tvsdk-24.html).

* **Sample-AES のサポート**

   このリリースでは、MSE での Sample-AES 暗号化コンテンツ再生およびFlashフォールバックのサポートが追加されました。 Google Chrome 上で安全なオリジンで AES コンテンツをホストするための要件は削除されました。

* **AAC コンテナのサポート**

   拡張子が.aac のファイルの再生がサポートされるようになりました。 これは、音声のみのストリームまたは代替オーディオです。

   >[!NOTE]
   >
   >AC3 および拡張 AC3 コーデックは、まだサポートされていません。

* **トークン化されたストリーム再生**

コンテンツ配信ネットワーク (CDN) を通じて配信される HLS ストリームでは、マニフェストとセグメントリクエストで認証トークンを使用して検証をおこなうことができます。また、これらのトークンは URL パラメーターとして、または cookie ヘッダーとして提供できます。 このようなストリームの再生がサポートされるようになりました。

**バージョン 2.4.1**

バージョン 2.4.1 では、次の新機能が追加されました。

* **UI フレームワーク**

このフレームワークは、再生/一時停止や音量などの基本的なコントロールを含め、スクラブバーの状態やクローズドキャプション設定などの要素を簡単に追加または削除するための API で構成されています。 コントロールに関連付けられた動作を指定し、カスタムコントロールを作成して、プレーヤー UI をスキンにすることができます。 これらはすべてフレームワークを通じておこなわれ、DOM 構造を直接操作する必要はありません。

* **ライブストリームの HLS 再生の強化**

このリリースでは、広告挿入による継続性の低下がサポートされます。 アダプティブビットレートプロファイル間で同期を行い、再生をスムーズにおこなうために、 EXT-PROGRAM-DATE-TIME タグと EXT-MEDIA-SEQUENCE タグを使用します。

* **VPAID 2.0 のサポート**

ビデオプレーヤー広告配信インターフェイス定義 (VPAID) バージョン 2.0 は、ユーザーにリッチメディアエクスペリエンスを提供し、発行者が広告のターゲット設定、広告インプレッションの追跡、ビデオコンテンツの収益化を改善できます。 このリリースでは、ビデオオンデマンド (VOD) コンテンツ用のリニア JavaScript VPAID 広告がサポートされています。

* **カスタム HLS タグ**

メディアストリームは、プレイリスト/マニフェストファイル内のタグの形式で追加のメタデータを伝達できます。 ブラウザー TVSDK を使用すると、追加のタグを指定してサブスクライブし、それらのタグがマニフェストに表示されたら通知を受け取ることができます。

* **プレーヤータイムラインに表示される広告マーカー**

このリリースでは、VOD コンテンツと Live コンテンツのプレーヤータイムラインへの広告マーカーの表示がサポートされています。 この動作は、リファレンスプレーヤーで確認できます。

**2.4 でサポート**

バージョン 2.4 では、次の機能が使用できました。

* **MP3 オーディオ再生**

   このリリースでは、メディアソース拡張機能 (MSE) と Safari ビデオタグが設定されたブラウザーでの MP3 オーディオ再生がサポートされます。

* **MP4 ビデオ再生**

   次の機能がサポートされています。

   * 単一ストリーム再生
   * 広告動作と追跡を含むプリロールおよびポストロール MP4 広告
   * 広告動作と追跡を含むプリロールおよびポストロール HLS 広告
   * 広告動作と追跡機能を備えたプリロールおよびポストロール DASH 広告

## サポートされるプラットフォーム {#supported-platforms}

ブラウザー TVSDK には、実行する必要のあるプラットフォームとソフトウェアのレベルに固有の要件があります。 次のプラットフォームとソフトウェアレベルがサポートされています。

### デスクトップ設定 {#desktop-configurations}

* Microsoft Windows 7:

   * Internet Explorer 11 以降
   * Chrome 33 以降
   * Firefox 38 以降

* Microsoft Windows 8.1

   * Internet Explorer 11 以降
   * Chrome 33 以降
   * Firefox 38 以降

* Microsoft Windows 10

   * Edge+

* Apple OS X

   * Safari 9 以降
   * Chrome 33 以降
   * Firefox 38 以降

### モバイル Web 設定 {#mobile-web-configurations}

* Android 4.4

   * ネイティブブラウザー
   * Chrome 33 以降

* Android 5.0

   * ネイティブブラウザー
   * Chrome 33 以降

* Android 6.0

   * ・ Chrome 33 以降

* Apple iOS 9

   * Safari 9 以降
   * Chrome 33 以降

* Apple iOS 10

   * Safari 9 以降
   * Chrome 33 以降

**Google Chromecast( 第 2 世代；（DASH 再生のみ）**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>技術</strong> </p> </td> 
   <td><p><strong>Browser TVSDK ビデオタグ</strong><sup>1</sup></p> </td> 
   <td><p><strong>Browser TVSDK MSE</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>デフォルトの技術</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>iOS</p> </td> 
   <td><p>MP4 および HLS</p> </td> 
   <td><p>-</p> </td> 
   <td><p>-</p> </td> 
   <td><p>ビデオタグ</p> </td> 
  </tr> 
  <tr> 
   <td><p>Android</p> </td> 
   <td><p>MP4</p> </td> 
   <td><p>HLS および DASH</p> </td> 
   <td><p>-</p> </td> 
   <td><p>MSE</p> </td> 
  </tr> 
  <tr> 
   <td><p>Apple Safari 8</p> </td> 
   <td><p>MP4 および HLS</p> </td> 
   <td><p>-</p> </td> 
   <td><p>MP4 および HLS</p> </td> 
   <td><p>ビデオタグ</p> </td> 
  </tr> 
  <tr> 
   <td><p>Google Chrome</p> </td> 
   <td><p>MP4</p> </td> 
   <td><p>HLS および DASH</p> </td> 
   <td><p>MP4 および HLS</p> </td> 
   <td><p>MSE</p> </td> 
  </tr> 
  <tr> 
   <td><p>Mozilla Firefox</p> </td> 
   <td><p>MP4</p> </td> 
   <td><p>HLS および DASH</p> </td> 
   <td><p>MP4 および HLS</p> </td> 
   <td><p>MSE<sup>2</sup></p> </td> 
  </tr> 
  <tr> 
   <td><p>Internet Explorer 11</p> <p>(Windows 7)</p> </td> 
   <td><p>MP4</p> </td> 
   <td><p>-</p> </td> 
   <td><p>MP4 および HLS</p> </td> 
   <td><p>Flash</p> </td> 
  </tr> 
  <tr> 
   <td><p>Internet Explorer 11</p> <p>(Windows 8.1)</p> </td> 
   <td><p>MP4</p> </td> 
   <td><p>HLS、DASH</p> </td> 
   <td><p>MP4 および HLS</p> </td> 
   <td><p>MSE</p> </td> 
  </tr> 
 </tbody> 
</table>

## 機能マトリックス {#feature-matrix}

このリリースでサポートされる機能とサポートされない機能の一覧を次に示します。

* *MP3 オーディオ機能 — コア再生*
* *MP4 ビデオ機能 — コア再生*
* *MP4 ビデオ機能 — コアAd Insertion*

>[!NOTE]
>
>*以下の機能マトリックステーブルでは、「Y」は、この機能が現在のリリースでサポートされていることを意味します。*

### MP3 オーディオ機能 {#mp-audio-features}

**表 1:コア再生{#table-core-playback}**

| カテゴリ | コンテンツタイプ | 機能 | Flash | HTML5:FF、IE、Chrome、Android Chrome | HTML5:Safari、iOS Safari |
|--- |--- |--- |--- |--- |--- |
| 再生 | MP3 VOD | 一般再生（再生、一時停止、シーク） | サポート対象外 | Y | Y |

1 Browser TVSDK Video タグは、ストリーミングと DRM をサポートしていません。 コーデックとコンテナのサポートは、すべてのブラウザーで同じではありません。

2 Firefox のデフォルトは、Flash Player41 以前のバージョンです。

### MP4 オーディオ機能 {#mp-audio-features-1}

**表 2:コア再生**

| カテゴリ | コンテンツタイプ | 機能 | Flash | HTML5:FF、IE、Chrome、Android Chrome | HTML5:Safari、iOS Safari |
|--- |--- |--- |--- |--- |--- |
| 再生 | MP4 VOD | 一般再生（再生、一時停止、シーク） | サポート対象外 | Y | Y |

**表 3:コアAd Insertion**

| カテゴリ | コンテンツタイプ | 機能 | Flash | HTML5:FF、IE、Chrome、Android Chrome | HTML5:Safari、iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Ad Insertion | MP4 VOD | プリロール (MP4) | サポート対象外 | Y | Y |
| Ad Insertion | MP4 VOD | ポストロール (MP4) | サポート対象外 | Y | Y |

HLS または DASH の機能のサポートの詳細については、以下を参照してください。

## HLS 機能マトリックス {#hls-feature-matrix}

Browser TVSDK の HLS 機能の機能一覧を示します。

* *HLS コア再生*
* *HLS の高度な再生機能*
* *HLS コンテンツ保護機能*
* *HLS コア広告挿入機能*
* *HLS の高度な広告挿入機能*
* *HLS 統合*

>[!NOTE]
>
>*以下の機能マトリックステーブルでは、「Y」は、この機能が現在のリリースでサポートされていることを意味します。*

### HLS 機能 {#hls-features}

次の機能がサポートされています。

**表 4:HLS コア再生**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>カテゴリ</strong></p> </td> 
   <td><p><strong>コンテンツタイプ</strong></p> </td> 
   <td><p><strong>機能</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>HTML5:FF、IE、Chrome、Android Chrome</strong></p> </td> 
   <td><p><strong>HTML5:Safari、iOS Safari</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>一般的な再生（再生、一時停止、シーク）</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>FER VOD</p> </td> 
   <td><p>一般的な再生（再生、一時停止、シーク）</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>適応ビットレート</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>608/708キャプション</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>WebVTT</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>VOD のみ</p> </td> 
   <td><p>VOD のみ</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>マニフェストのフェイルオーバー</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>高度なフェイルオーバー</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>プラットフォームの制限</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>QoS とプレーヤーの通知</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>QoS の制限のサポート</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>cookie ヘッダーのサポート</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>プラットフォームの制限</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>バッファ制御パラメータの設定</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p>プラットフォームの制限</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>アダプティブを設定</p> <p>ビットレート制御</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>プラットフォームの制限</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>カスタムタグ</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>プラットフォームの制限</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td>遅延バインディングオーディオ</td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>プラットフォームの制限</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>302 リダイレクト</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>プラットフォームの制限</p> </td> 
  </tr> 
 </tbody> 
</table>

**表 5:HLS の高度な再生機能**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>カテゴリ</strong></p> </td> 
   <td><p><strong>コンテンツタイプ</strong></p> </td> 
   <td><p><strong>機能</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>HTML5:FF、IE、Chrome、Android Chrome</strong></p> </td> 
   <td><p><strong>HTML5:Safari、iOS Safari</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>オフセットでの再生</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>オーディオのみの再生</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>トリック再生</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>スムーズなトリック再生</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>プラットフォームの制限</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>ID3 の解析</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Discontinuity マーカーのサポート</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>トークン化ストリーム</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>プラットフォームの制限</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>請求</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
 </tbody> 
</table>

**表 6:HLS コンテンツ保護機能**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>カテゴリ</strong></p> </td> 
   <td><p><strong>コンテンツタイプ</strong></p> </td> 
   <td><p><strong>機能</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>HTML5:FF、IE、Chrome、Android Chrome</strong></p> </td> 
   <td><p><strong>HTML5:Safari、iOS Safari</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>コンテンツ保護</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>AES-128</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>コンテンツ保護</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Sample-AES</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>コンテンツ保護</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>DRM</p> </td> 
   <td><p>Adobeアクセス</p> </td> 
   <td><p>サポート対象外</p> </td> 
   <td><p>FairPlay</p> </td> 
  </tr> 
 </tbody> 
</table>

**表 7:HLS コア広告挿入機能**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>カテゴリ</strong></p> </td> 
   <td><p><strong>コンテンツタイプ</strong></p> </td> 
   <td><p><strong>機能</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>HTML5:FF、IE、Chrome、Android Chrome</strong></p> </td> 
   <td><p><strong>HTML5:Safari、iOS Safari</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>プリロール (MP4/HLS)</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>ミッドロール (HLS)</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>プラットフォームの制限</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>ポストロール (MP4/HLS)</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>FER VOD</p> </td> 
   <td><p>広告の解像度と動作</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>プラットフォームの制限</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>デフォルトの広告ポリシー</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>プラットフォームの制限</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>VAST 2.0/3.0</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>VMAP 1.0</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>クリエイティブの再パッケージ化（MP4 から HLS）</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
 </tbody> 
</table>

**表 8:HLS の高度な広告挿入機能**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>カテゴリ</strong></p> </td> 
   <td><p><strong>コンテンツタイプ</strong></p> </td> 
   <td><p><strong>機能</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>HTML5:FF、IE、Chrome、Android Chrome</strong></p> </td> 
   <td><p><strong>HTML5:Safari、iOS Safari</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>広告のみ</p> </td> 
   <td><p>サポート対象外</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>ターゲティングパラメーター</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>カスタムパラメーター</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>カスタム広告ポリシー</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>プラットフォームの制限</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>遅延広告読み込み</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>サポート対象外</p> </td> 
   <td><p>プラットフォームの制限</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>コンパニオン広告、バナー広告、クリック可能な広告</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>VPAID 2.0</p> </td> 
   <td><p>SWF</p> </td> 
   <td><p>JavaScript</p> </td> 
   <td><p>JavaScript</p> </td> 
  </tr> 
 </tbody> 
</table>

**表 9:HLS 統合{#table-hls-integrations}**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>カテゴリ</strong></p> </td> 
   <td><p><strong>コンテンツタイプ</strong></p> </td> 
   <td><p><strong>機能</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>HTML5:FF、IE、Chrome、Android Chrome</strong></p> </td> 
   <td><p><strong>HTML5:Safari、iOS Safari</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>統合</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Adobe Analytics VHL 統合</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
 </tbody> 
</table>

## DASH 機能マトリックス {#dash-feature-matrix}

以下に、ブラウザー TVSDK の DASH 機能の機能マトリックスを示します。

・ *DASH コア再生機能*

・ *DASH 高度な再生機能*

・ *DASH コンテンツ保護機能*

・ *DASH コア広告挿入機能*

・ *DASH の高度な広告挿入機能*

・ *DASH 統合*

>[!NOTE]
>
>以下の機能マトリックスの表では、Y は、現在のリリースで機能がサポートされていることを意味します。

### DASH 機能 {#dash-features}

次の機能がサポートされています。

**表 10:DASH コア再生機能**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>カテゴリ</strong></p> </td> 
   <td><p><strong>コンテンツタイプ</strong></p> </td> 
   <td><p><strong>機能</strong></p> </td> 
   <td><p><strong>HTML5 FF、IE、Chrome、Android Chrome</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>一般的な再生（再生、一時停止、シーク）</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>FER VOD</p> </td> 
   <td><p>一般的な再生（再生、一時停止、シーク）</p> </td> 
   <td><p>サポート対象外</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>適応ビットレート</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>608/708キャプション</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>WebVTT</p> </td> 
   <td><p>VOD のみ</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>フェイルオーバー</p> </td> 
   <td><p>VOD のみ</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>QoS とプレーヤーの通知</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>cookie ヘッダーのサポート</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>バッファ制御パラメータの設定</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>アダプティブビットレートコントロールの設定</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>カスタムタグ (EventStream)</p> </td> 
   <td><p>VOD のみ（インライン）</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>遅延バインドオーディオ</p> </td> 
   <td><p>VOD のみ</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>302 リダイレクト</p> </td> 
   <td><p>VOD のみ</p> </td> 
  </tr> 
 </tbody> 
</table>

**表 11:DASH 高度な再生機能**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>カテゴリ</strong></p> </td> 
   <td><p><strong>コンテンツタイプ</strong></p> </td> 
   <td><p><strong>機能</strong></p> </td> 
   <td><strong>HTML5 FF、IE、Chrome、Android Chrome</strong></td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>オフセットでの再生</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>オーディオのみの再生</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>トリック再生</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>スムーズなトリック再生</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>ID3 の解析</p> </td> 
   <td><p>サポート対象外</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>複数期間のサポート</p> </td> 
   <td><p>VOD のみ</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>トークン化ストリーム</p> </td> 
   <td><p>サポート対象外</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>請求</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
 </tbody> 
</table>

**表 12:DASH コンテンツ保護機能**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>カテゴリ</strong></p> </td> 
   <td><p><strong>コンテンツタイプ</strong></p> </td> 
   <td><p><strong>機能</strong></p> </td> 
   <td><p><strong>HTML5 FF、IE、Chrome、Android Chrome</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>コンテンツ保護</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>AES-128</p> </td> 
   <td><p>サポート対象外</p> </td> 
  </tr> 
  <tr> 
   <td><p>コンテンツ保護</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Sample-AES</p> </td> 
   <td><p>サポート対象外</p> </td> 
  </tr> 
  <tr> 
   <td><p>コンテンツ保護</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>DRM</p> </td> 
   <td><p>・ Widevine（Chrome、Firefox 47 以降、Chromecast）</p> <p>・ Windows 8.1 および Edge 上の Internet Explorer での PlayReady</p> <p>・ Windows Firefox 用の Primetime DRM（ビデオのみ）</p> </td> 
  </tr> 
 </tbody> 
</table>

**表 13:DASH コア広告挿入機能**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>カテゴリ</strong></p> </td> 
   <td><p><strong>コンテンツタイプ</strong></p> </td> 
   <td><p><strong>機能</strong></p> </td> 
   <td><p><strong>HTML5 FF、IE、Chrome、Android Chrome</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>プリロール (MP4/DASH)</p> </td> 
   <td><p>VOD のみ</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>ミッドロール (DASH)</p> </td> 
   <td><p>VOD のみ</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>ポストロール (MP4/DASH)</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>FER VOD</p> </td> 
   <td><p>広告の解像度と動作</p> </td> 
   <td><p>サポート対象外</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>デフォルトの広告ポリシー</p> </td> 
   <td><p>VOD のみ</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>VAST 2.0/3.0</p> </td> 
   <td><p>VOD のみ</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>VMAP 1.0</p> </td> 
   <td><p>VOD のみ</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>クリエイティブの再パッケージ化（MP4 から DASH）</p> </td> 
   <td><p>サポートなし</p> </td> 
  </tr> 
 </tbody> 
</table>

**表 14:DASH の高度な広告挿入機能**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>カテゴリ</strong></p> </td> 
   <td><p><strong>コンテンツタイプ</strong></p> </td> 
   <td><p><strong>機能</strong></p> </td> 
   <td><p><strong>HTML5</strong> FF、IE、Chrome、Android Chrome</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>広告のみ</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>ターゲティングパラメーター</p> </td> 
   <td><p>VOD のみ</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>カスタムパラメーター</p> </td> 
   <td><p>VOD のみ</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>カスタム広告ポリシー</p> </td> 
   <td><p>サポート対象外</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>遅延広告読み込み</p> </td> 
   <td><p>サポート対象外</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>コンパニオン広告，バナー広告，クリック可能な広告</p> </td> 
   <td><p>サポート対象外</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>VPAID 2.0</p> </td> 
   <td><p>サポート対象外</p> </td> 
  </tr> 
 </tbody> 
</table>

**表 15:DASH 統合**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>カテゴリ</strong></p> </td> 
   <td><p><strong>コンテンツタイプ</strong></p> </td> 
   <td><p><strong>機能</strong></p> </td> 
   <td><p><strong>HTML5:FF、IE、Chrome、Android Chrome</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>統合</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Adobe Analytics VHL 統合</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
 </tbody> 
</table>

## 修正された問題 {#issues-fixed}

**2.4.12 の更新（ビルド 204）で修正された問題**

Browser TVSDK version 2.4.12 Update（ビルド 204）で、以下の問題を修正しました。

・ **21647** — オーディオがミュートされている場合、iOSデバイスでのビデオの自動再生を TVSDK で許可する必要があります。

・ **21465**- DRM で保護された DASH ストリームを DASH ライブストリームの再生後に再生すると、エラーキーシステムアクセス拒否が受信されました。

・ **21442** — プリロール広告がユーザージェスチャーで再生された後、iOS Web でコンテンツの自動再生を有効にします。

・ **21240**— Auditude/VMAP から解析された VPAID 広告をフィルタリングする API が提供されました。

**バージョン 2.4.11 で修正された問題**

Browser TVSDK バージョン 2.4.11 では、以下の問題が修正されました。

**コア再生の機能：**

・ **19192**:TVSDK は、 TextFormat:bottomInset と TextFormat:safeArea を実装するようになりました。 これらの機能強化により、コントロールバーが画面に表示されている場合、クローズドキャプションの位置を変更できます。

・ **21009**:クローズドキャプションは、新しいキャプションが表示されるまで、不連続を越えてシークした場合に、画面上で保持されます。

・ **21141**:セグメント追加中の競合状態が原因で、シークバックが拒否されます。

・ **21142**:プレーヤーが INITIALIZED 状態のときに、シーク可能な再生範囲を使用できるようにします。 これらの変更により、位置でのセッションの開始がサポートされるようになりました。

・ **21363**:608/708 DASH ストリームの広告挿入後にクローズドキャプションが同期されない。

**広告挿入機能：**

・ **21179**:VOD コンテンツを含むミッドロール関連の問題（長い一時停止、黒いフレーム）は、 ad.primaryAsset.adParameters プロパティを正しく設定することで解決されるようになりました。

・ **21257**:MP4 が有効な MIME タイプではなく、クリエイティブの再パッケージ化機能が有効な場合は、最もビットレートの高い MP4 ファイルがトランスコード用に選択されます。

・ **21361**:追加の正規化ルールをサポートするために、 TVSDK は、広告システムとクリエイティブ ID をクリエイティブパッケージ化リクエストのクエリパラメーターとして VAST 応答から渡すようになりました。

**バージョン 2.4.10 で修正された問題**

Browser TVSDK バージョン 2.4.10 では、以下の問題が修正されました。

**コア再生の機能：**

・ **21060**:不連続を含む HLS ストリームと ISO BMFF ボックスがストリームの最後まで実行されると、無効なコーデックエラーがスローされます。

・ **21045**:プレイリスト内の最初のビデオ再生が完了した後、iOSで自動再生が機能しない。

・ **20975**:Chrome ブラウザーの QoS プロバイダーは、フレームレートを NaN として返します。

・ **20823**:データのないセグメントが発生した場合に、サポートされていないコーデックエラーがスローされました。

・ **20769**:ABR ポリシーに基づいて即座に切り替える代わりに、SDK はシーク時に現在のビットレートで開始するようになりました。

・ **20031**:IE11(Windows 8.1) で縦向きモードの場合、ビデオ画面は小さくなります。 コンテンツ保護機能：

・ **19316**:HLS AES-128 ストリームの場合に復号に失敗したセグメントをスキップします。

**バージョン 2.4.9 で修正された問題**

Browser TVSDK バージョン 2.4.9 では、以下の問題が修正されました。

**コア再生の機能：**

・ **13407**:Firefox が再生中に「ontimeupdate」イベントの送信を停止すると、DASH ストリームが停止する場合があります。

・ **16380**:MSE を介した非一致の開始時間を持つセグメントの Muxed Audio Video コンテンツ再生中に、表現間の Audio Sync Error が ABR スイッチに蓄積され、最終的に Error(Chromium の問題#663686) が発生します。

・ **17985**:Firefox ブラウザーで特定の ISO-BMFF ストリームを再生すると、再生が停止する (Firefox の問題#1342913)。 これは Firefox v53 以降で修正されました。

・ **19141**:Uncaught (in promise) ReferenceError :幅が定義されていません。

・ **18997, 19299**:セグメントの境界でのビデオのちらつきの問題。 この問題は、SDK が最後のサンプルのコンポジション時間オフセットを正しく計算しなかったために発生していました。

・ **19780**:Firefox v53 で HLS コンテンツと HLS 広告の再生が開始されない (Firefox の問題#354653)。

・ **20046**:時間指定メタデータオブジェクトとして受け取った場合、プログラムの日時は値ではなくキーとして受け取られます。

・ **20047**:useDefaultResizeHandler は、エラーのフォールバックをスローし、Flashをスローします。

・ **20179**:FlashフォールバックがFlash Playerv25.0.0.171 で機能しない。

・ **20293**:Firefox が、停止につながる特定の HLS ストリームのデータのバッファリングを停止します。

・ **20626**:再生時間がゼロのビデオサンプルの処理が正しく処理されないため、プレーヤーが Chrome でメディアデコードエラーをスローする。

・ **20078**:ブラウザーエラー「QuotaExceeded」で再生が停止した。

・ **18639**:HLS Live stream 608 CC では、テキストがスペルミスとして表示される場合があります。

・ **20028**:ClosedCaptions のサイズパラメーターは、フォントサイズを変更しません。

・ **20613**:クローズドキャプションボックスは互いに重なり合っているので、読みにくくなります。

**コアAd Insertion(CSAI) の機能：**

・ **20043**:複数の広告とサードパーティのリダイレクトを伴う広告インプレッションおよび広告トラッキングコールが見つかりません。

・ **20044**:クリエイティブの再パッケージ化を使用する場合、広告ブレーク内のすべての広告を正常に再パッケージ化する必要があります。そうしないと、広告ブレークは完全に破棄されます。

・ **20097**:広告マニフェストが使用できない場合は、20 秒のタイムアウトを待つのではなく、広告再生がスキップされ、メインコンテンツが直ちに再開されます。

**バージョン 2.4.8 の更新（ビルド 6002）で修正された問題**

Browser TVSDK version 2.4.8 Update (Build 6002) で、以下の問題を修正しました。

・ **14126:** MSE ソースバッファの内部ギャップが原因で、Firefox( 問題#1316024) で再生が停止する場合があります。 再生を再開するには、シークを試してみてください

・ **19608:** Auditude VMAP 応答の timeoffset 値を尊重するよう修正しました。

・ **19635:** Windows 10 での Internet Explorer 11 でのビデオの停止を修正しました。

・ **19761:** HLS での ABR の問題を修正しました。

・ **19780:** Mozilla Firefox v53 で壊れていた HLS コンテンツを含む広告再生を修正しました。

・ **19877および19744:** この問題により、シーク操作後にビットレートを選択する際の不整合が修正されます。 これで、シーク時のビットレート選択が、現在のビットレートの低い値と、起動時のビットレートになります。

・ **19881:** 再生が停止し、バッファリングオーバーレイが、シークが 3 ～ 4 回実行された後、無限の時間表示されます。

・ **19884:** Chrome 59 Beta 検証済みメディアパス (VMP) 要件のコンプライアンスを確認します。 bTVSDK は、Chrome 59 ベータ版で Widevine DRM コンテンツを再生できました。

・ **19916:** UI-Framework での DRM 再生が壊れました。 現在は、メタデータにポリシーがない場合でも、 acquireLicense を呼び出します。

**バージョン 2.4.8 で修正された問題**

Browser TVSDK 2.4.8 リリースでは、次の問題が修正されました。

・ **10075**:タイムラインの前のシーク時に、Firefox および Chrome で再生完了イベントが受信されず、Firefox でシークイベントが受信されなかった問題を修正しました。

・ **15775**:Windows 8.1 Internet Explorer で Play Complete イベントを受け取っていません。

・ **17306**:SSAI ストリームでは、再生がサポートされます。 ステッチされた広告のトラッキングはサポートされていません。

・ **19142**:時には巻き戻しによって、ビデオプレーヤーが永久にバッファリング状態のままになる。

・ **19218**:広告マーカーは、UI フレームワークを通じては使用できません。

・ **19219**:広告のみの再生は、UI フレームワークを通じては機能しません。

・ **19222**:AES-128 キーはプレイリストに対して 1 回リクエストされ、以降のリクエストはキャッシュから提供されます。 以前は、各セグメントに対してリクエストが受け取られていました。

・ **19597**:&quot;Uncaught TypeError:Chrome のカナリアビルドで、「log」（未定義の）プロパティを読み取れませんでした。

・ **19605**:adRequestDomain は、フォールバックモードでは使用できませんでしたFlash。

・ **19608**:HLS ライブストリームに VMAP 広告が挿入されませんでした。 SDK は、キューマーカーを考慮し、VMAP 応答の時間オフセット値に依存しなくなりました。

・ **19637**:広告のみ再生すると、広告の最後にスクリプトエラーが発生します。

・ **19732**:CRS プレイリストのリクエストが 404 エラーで失敗していました。 ブラウザー TVSDK からの 1401 および 1403 リクエストが更新され、この処理がおこなわれるようになりました。

・ **19762**:acquireLicense setAuthenticationToken の前に呼び出されたので、トークンの有効性に関係なく有効なライセンスが返されました。 これが修正され、 setAuthenticationToken 応答の後でのみ acquireLicense が呼び出されます。

**バージョン 2.4.7 で修正された問題**

バージョン 2.4.7 で修正された問題を次に示します。

・ **8397**:Adobe Mediumサーバーで生成された HLS ライブストリームは、セグメントがキーフレームで開始しない場合、再生されない可能性があります。

・ **13606**:Chrome ブラウザーの HLS ストリームに関する複数の Seek 関連の問題を修正しました。

・ **14807**:Chrome ブラウザーで、play() の直後にシークまたは一時停止がトリガーされた場合、再生がエラー DOMException で停止することがあります。play() リクエストが呼び出しによって中断されました…(Chromium の問題# 593273)。

・ **19085**:MediaPlayer Params（volume、abrControlParameters、ccStyle など）は、Resetting 時に Defaults に設定されません。

**バージョン 2.4.6 で修正された問題**

バージョン 2.4.6 で修正された問題：

・ **18093**:サブスクライブされたタグの横にあるタグの TimedMetadata は、Flash PlayerフォールバックモードでFlashバージョン 24 を使用すると返されます。

**バージョン 2.4.4 で修正された問題**

バージョン 2.4.4 では、次の問題が修正されました。

・ **8711**:MSE では、608/708キャプションはデフォルトで両端揃えされます。

・ **13934**:広告の ABR 設定は、HLS ライブストリームを再生する際には適用されません。

・ **14079**:DVR の少ない HLS ライブストリームの場合、ネットワークの遅延の問題が原因で再生が遅れる可能性があるので、長期間の再生が失敗する可能性があります。 再生を再開するには、ライブポイントをクリックします。

・ **15037**:プレーヤー UI フレームワークに付属のサンプルは、Windows 7 上のMicrosoft Internet Explorer 10 では機能しません。

・ **15913**:HLS VOD ストリームの場合、Chrome で、マニフェストの応答が 304 未変更の場合、ストリームは再生されません。 これは、Chrome v55 以降 (Chromium の問題633696) で修正されました。

・ **16103**:Android Chrome では、低帯域幅の条件下で、Uncaught TypeError が発生して再生が停止する場合があります。未定義エラーのプロパティ「programDateTime」を読み取れません。

・ **16265**:HLS VOD およびライブストリームの場合、不連続を越えたシークは機能しません。

・ **16709**:PDT と不連続マーカーを使用して HLS ライブストリームを再開すると、プレーヤーがバッファリングで動かなくなる場合があります。

## 既知の問題と制限事項 {#known-issues-and-limitations}

Browser TVSDK の制限事項と既知の問題については、以下で説明します。

**表 16:コア再生機能**

<table> 
 <tbody> 
  <tr> 
   <td><strong>コンテンツタイプ</strong></td> 
   <td><strong>機能</strong></td> 
   <td><strong>Flash</strong></td> 
   <td><strong>Firefox のHTML5、IE、Chrome、Android Chrome</strong></td> 
   <td><strong>Safari でのHTML5、iOS Safari</strong></td> 
   <td><strong>Chromecast（DASH 再生のみ）</strong></td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>一般再生（再生、一時停止、シーク）</td> 
   <td><p>・ HLS 以外のメディア形式はサポートされていません。</p> <p>8799:Flashのフォールバックでは混合コンテンツは処理されないので、コンテンツ、広告および他の URL で混合コンテンツ（安全なコンテンツと安全でないコンテンツを組み合わせて）が生じないようにする必要があります。</p> <p>・ 19271:UI フレームワークを使用したマルチビュー再生は、Flashフォールバックモードではサポートされていません。</p> <p>・ Windows 7 上のMicrosoft Internet Explorer 8 および 9 では、Flashのフォールバックが機能しません。これらのバージョンは、SDK ではサポートされていません。</p> <p>・ 20262:Flashのフォールバックは、ターゲット情報リストにカスタムパラメータを追加します。 また、カスタムパラメーターの優先順位も、Flashと MSE の場合は異なります。</p> <p>・ 20653:Browser TVSDKFlashフォールバックは、Creators Update を使用する Win10 では機能しません。</p> <p>・Flashフォールバックは、Flash Playerバージョン 23 以降で機能します。</p> <p>・ 20087 - Chrome 59 Beta（を使用）</p> <p>Flash25.0.0.171</p> <p>ベータ版（デフォルト）の場合、HLS 再生はFlashフォールバックモードで動作しません。 カナリアでは問題なく機能しています。</p> </td> 
   <td><p>・ 12563:オーディオコーデック mp4a.40.02 のダッシュストリームは、MPD でサポートされていないオーディオコーデック文字列が原因で、Firefox で再生されません。 オーディオコーデック mp4a.40.2 がサポートされています。</p> <p>15029:UI-Framework の multiView でビデオを切り替える際に、再生/一時停止ボタンがそれに応じて更新されない。</p> <p>・ 16034:Windows 8.1 IE で reset() を呼び出すと、不明な MIME タイプエラーが発生します。 再生を再開するには、メディアを再読み込みしてください。</p> <p>・ 18235:広告を含む DASH VOD ストリームでは、特定のシークの問題が発生していました。</p> <p>・ 18727:エラー API は MSE ではサポートされていません</p> <p>18750:ステータス変更イベントが、SDK と UI の両方のフレームワークと UI フレームワークで、リソースの読み込み後に追加されたイベントの IDLE イベントと Initializing StatusChange イベントが欠落する場合があります。</p> <p>・ 18889:MediaPlayer が ERROR 状態の場合、 view オブジェクトは返されません。</p> <p>・ 19039:AdobePSDK の場合。 MediaPlayer. seekToLocal() を EOF より大きい値で使用すると、MSE の場合は最初から再生が開始されます。</p> <p>・ 19049:再生中にビデオがブロックされた場合、Chrome、IE、Firefox のFlash Playerでエラー状態が報告されませんでした。</p> <p>・ 17205:オーディオの再生が続く間、ビデオの再生が数時間停止し、無音のストリームの再生が停止する (Chromium の問題# 664033)。</p> <p>・ 12308:composition_time_offset が指定された DASH ストリームは、Chrome ブラウザーで timeStampOffset が適用され、負のデコード時間になる可能性があり、その結果、MEDIA_ERR_ SRC_NOT_SUPPORTED エラー (Chromium の問題#398141) になる。</p> <p>・ 14126:MSE ソースバッファの内部ギャップが原因で、Firefox( 問題# 1316024) で再生が停止する場合があります。 再生を再開するには、シークを試してみます。</p> <p>・ 19115:MS Edge および IE 11（Win 8.1 および 10）では、CORS リダイレクトで Origin が null に設定されず、再生エラーを引き起こすヘッダーが null でないので、失敗します。</p> <p>・ 19861：メディアが既に再生されている場合に、ソースバッファに追加動作が発生する問題。 Chrome は moov を含む追加されたフラグメントを拒否し、その後のデコードエラーが発生します。 (Chromium の#735335号 )</p> <p>19921:特定の HLS コンテンツが正常にバッファーされた場合でも再生が停止する (Chromium の問題#713540)</p> <p>・ 20444:IE および Edge 上でバッファー範囲の終わりまでシークすると、再生が停止する場合があります。</p> <p>・ 20511:広告のある場合もない場合もある HLS ストリームでは、シーク拒否が見られることがあります。</p> <p>・ 20743:Windows 10 Chrome では、HLS ライブストリームは、MP4 プリロール再生の数秒前に再生されます。</p> <p>・ 21043:メタデータがないので、初回の読み込み時にビデオのサイズが正しくない可能性があります。</p> <p>・ 21115:プリロール広告がプレイリスト内のビデオで使用可能な場合、再生を開始するには Android のユーザージェスチャーが必要です。</p> <p>・ HLS Live はタイムスタンプのロールオーバーをサポートしていません。</p> <p>・ AAC-SSR オーディオはサポートされていません。</p> <p>オーディオコーデック AC3 および拡張 AC3 はサポートされていません。</p> <p>・タイムスタンプの不連続性を持つが、不連続マーカーを持たないストリームの場合</p> <p>・ジャンプが原因で、再生の異常や誤ったシークが発生する可能性があります。</p> <p>・コンテンツの再生時間と再生時間が一致しない可能性があります。</p> <p>・表示域とレンディション間の不連続性は、他の条件と一致する必要がある場合、同期と停止の問題が発生する可能性があります。</p> <p>・キャプションと WebVTT は、ストリームの終わりの近くに表示されない場合があります。</p> <p>・オーディオコーデックの変更は、タイムスタンプジャンプをまたいではサポートされません。</p> <p>・広告の挿入はサポートされていません。</p> <p>・早送りトリックモードが原因で、Win 8.1 IE 11 で再生ループが発生する場合があります (MS の問題#12446268)。</p> <p>ダッシュ：</p> <p>・ライブストリームの場合 — 動的タイプのライブプロファイルがサポートされます。</p> <p>・ VoD ストリームの場合 — 静的タイプのライブプロファイルがサポートされます。</p> <p>VoD ストリームの場合 — OnDemand プロファイルは、広告ワークフローに対して認定されていません。</p> </td> 
   <td><p>・ DASH Live および DASH Video on Demand ストリームはサポートされていません。</p> <p>・ PIP(Picture in Picture) ビデオの再生は、フルスクリーンモードのiOSではサポートされていません。</p> <p>Safari（ビデオタグ）では、正しいコンテンツタイプヘッダーを持たない拡張機能ではマニフェストが少なく機能しません。</p> </td> 
   <td><p>・送信者アプリの applicationID は、受信者の URL をカスタム受信者アプリとして登録する際に生成されたものと同じである必要があります。</p> <p>・リファレンスプレーヤーは、DASH ワークフローに対して認定されています。 UI フレームワークが認証されていません。</p> <p>サポートされるメディアコーデックのリストについては、 <a href="https://developers.google.com/cast/docs/media"><em>ここ</em></a>.</p> </td> 
  </tr> 
  <tr> 
   <td>FER VOD</td> 
   <td>一般再生（再生、一時停止、シーク）</td> 
   <td> </td> 
   <td>18098:HLS LBA FER ストリームで、特定のシーク問題が発生していました。</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>アダプティブビットレート</td> 
   <td><p>・ 20079:バッファー範囲内のシーク時にバッファーを書き換えます。</p> <p>20080:FlashABR の動作は MSE と一致しません。</p> </td> 
   <td><p>・ ABR ストリーム内のオーディオのみのフォールバックバリアントは、バッファ関連の制限のため無視されます。</p> <p>・ 12289:ABR 制御パラメーターは、HLS/DASH ストリームが無変の場合、オーディオには適用されません。</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>608/708 Captions</td> 
   <td> </td> 
   <td><p>・ 7810:Android 4.4.4 では、Chrome はプレーヤーで使用される基本的な CSS フォントファミリをサポートしていないようで、フォントスタイル変更機能が動作しません。</p> <p>・ 608 キャプションの場合、CC チャネルは変更できません。</p> <p>・ 608 キャプションの高度なスタイル設定機能はサポートされていません。</p> <p>埋め込みキャプション(608/708)は、アクセシビリティタグを介して通知されます。</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>WebVTT</td> 
   <td> </td> 
   <td><p>・ 5206:WebVTT ファイルの領域タグは、キャプションの表示時にプレーヤーでは無視されます。</p> <p>・ DASH:断片化/セグメント化 VTT ファイルはサポートされていません。</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>マニフェストのフェイルオーバー</td> 
   <td>21056:Flashフォールバックを使用すると、再生中にプライマリストリームが 404 エラーを返した場合、ライブストリームでフェイルオーバーは発生しません。</td> 
   <td>マニフェストのフェイルオーバーは、コンテンツにのみ適用でき、広告には適用されません。</td> 
   <td>プレイリストのフェイルオーバーが見つからない場合、Safari では HTTP エラーコード 404 に対してのみ機能します。</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>高度なフェイルオーバー</td> 
   <td> </td> 
   <td><p>・セグメントのフェイルオーバーは、使用できないセグメントのスキップや再生の続行をサポートしていません。</p> <p>20533:プレイリスト内の欠落したセグメントは Discontinuity として扱われ、次に使用可能なセグメントから再生が再開されます。</p> <p>21267:フェールオーバーによるストリームの切り替えにより、古いセグメントがダウンロードされる場合があります。</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>QoS とプレーヤーの通知</td> 
   <td>21129:フレームレートは、Flashフォールバックの場合は使用できません。</td> 
   <td><p>・ 11170:</p> <p>Timed_Event は、MSE を備えたブラウザー TVSDK では、Flashフォールバックを備えたブラウザー TVSDK とは異なり、使用できません。</p> <p>21129:ライブストリームのフレームレートは計算されません。</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>cookie ヘッダーのサポート</td> 
   <td> </td> 
   <td> </td> 
   <td><p>Safari では、withCredentials フラグと cookie ヘッダーはサポートされていません。</p> <p>21051:Safari で cookie を許可するには、環境設定/プライバシーで「Cookie と Web サイトのデータ」設定を有効にします。</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>カスタムタグ</td> 
   <td>14763:#で始まる以外のカスタムタグはサポートしないでください。 現在、Flashのフォールバック中に TimedMetadata オブジェクトが作成され、そのタグに関してレポートされます。</td> 
   <td>インバンドカスタムタグを含むストリームは認定されていません。</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>遅延バインディングオーディオ</td> 
   <td> </td> 
   <td><p>・広告の挿入は、HLS Live LBA ストリームではサポートされていません。</p> <p>・ 17273:HLS VOD LBA ストリームは、フェイルオーバーの場合はデフォルトのレンディションに切り替わり、最後に選択したレンディションに戻すことはできません。</p> <p>・ 20251:HLS Live LBA ストリームは、シーク時に停止する場合があります。</p> <p>・ 20497:HLS LBA の無音ストリームで、オーディオまたはビデオフレームが欠落していてストリームの終わりに近い場合、プレーヤーはバッファリング状態のままになります。</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>302 リダイレクト</td> 
   <td> </td> 
   <td><p>15787:302</p> <p>リダイレクトの最適化は、windows Edge および IE ブラウザーでは、XMLHttpRequest オブジェクトの responseURL プロパティをサポートしていないので、サポートされていません。</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

**表 17:高度な再生機能**

<table> 
 <tbody> 
  <tr> 
   <td>コンテンツタイプ</td> 
   <td>機能</td> 
   <td>Flash</td> 
   <td><strong>Firefox のHTML5、IE、Chrome、Android Chrome</strong></td> 
   <td><strong>Safari でのHTML5、iOS Safari</strong></td> 
   <td><strong>Chromecast（DASH 再生のみ）</strong></td> 
  </tr> 
  <tr> 
   <td>VOD</td> 
   <td>オフセットでの再生</td> 
   <td><p>特定のオフセット値で再生を開始することは、MP4 コンテンツをサポートしていません。</p> </td> 
   <td>20492:オフセットの前のミッドロール広告は、コンテンツがオフセット値から再開される前に再生されます。</td> 
   <td>オフセット機能を使用した再生は、iOSではサポートされていません。</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD</td> 
   <td>トリック再生</td> 
   <td>スムーズなトリックプレイは、iFrame レンディションがないストリームでは機能しません。</td> 
   <td><p>・ Firefox および Internet Explorer では Trick Play アダプテーションがサポートされていないので、これらのブラウザーでは逆トリックモードを使用できません。</p> <p>・広告と共にコンテンツを再生する場合は、トリック再生を使用できません。</p> <p>・ 10435:DASH 再生中に、Internet Explorer でのフォワードトリック再生でビデオがフリーズする (Win 8.1)</p> <p>断続的に これは、トリック再生適応なしでビデオ要素 playbackRate プロパティを使用しているので発生しています。</p> <p>14182:Chrome ブラウザーで巻き戻し中に、シークイベントが受信されない場合があり、トリックモードが機能しない場合があります。</p> <p>・ 14942:非トリック再生ストリームの場合でも、Android 向け Chrome で再生率を設定できますが、設定は適用されず、通常の速度で再生が続行されます。</p> <p>・ 17308:シークは、トリック再生モードでは機能しません。</p> <p>・ 17309:Chrome ブラウザーでは、逆トリックモードを 2 秒以上維持できません。</p> <p>19272:DASH ストリームの場合、Windows 10 Edge ブラウザーでバッファリングからトリック再生が回復しない場合がある。</p> </td> 
   <td>巻き戻しトリックモードはサポートされていません。</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>ID3 解析</td> 
   <td>20346:ID3 フレームのテキストエンコーディングバイトも、SDK から返す必要があります。</td> 
   <td><p>オーディオデータトランスポートストリーム (ADTS) で使用できる ID3 タグは、SDK では無視されます。</p> <p>・ 12378:ID3 時間指定メタデータは、MSE がサポートされているFlashとブラウザーで別の時間に解析されるので、参照プレーヤータイムラインでの表示動作も異なります。</p> <p>・ 19247:ID3 の解析は、UI フレームワークではサポートされていません。</p> </td> 
   <td><p>・ 20323:AAC セグメントの最初のサンプルのタイムスタンプを伝えるために使用される PRIV ID3 タグは、Safari で解析されません (Safari の問題#32422733)</p> <p>・ 20350:特定のデバイス (MAC OS X 10.1、iPad10 など ) では、Safari は、トリックモードではキュー変更イベントを提供しないので、ID3 フレームを受け取りません。 (Safari の問題#32450526)</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Discontinuity マーカーのサポート</td> 
   <td> </td> 
   <td><p>・不連続を含む HLS ストリームでは、クライアント側の広告挿入はサポートされません。</p> <p>・ HLS ストリームの不連続部分では、オーディオコーデックの変更は許可されません。</p> <p>・不連続マーカーを持つ HLS ストリームでは、Audio Track スイッチはサポートされていません。</p> </td> 
   <td>Safari での再生には、不連続性のある HLS ストリームに対する不連続シーケンス番号が必要です。</td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

**表 18:コンテンツ保護機能**

<table> 
 <tbody> 
  <tr> 
   <td><strong>コンテンツタイプ</strong></td> 
   <td><strong>機能</strong></td> 
   <td><strong>Flash</strong></td> 
   <td><strong>Firefox のHTML5、IE、Chrome、Android Chrome</strong></td> 
   <td><strong>Safari でのHTML5、iOS Safari</strong></td> 
   <td><strong>Chromecast（DASH 再生のみ）</strong></td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>AES-128</td> 
   <td> </td> 
   <td>バイト範囲は、AES-128 で暗号化されたコンテンツではサポートされていません。</td> 
   <td>12324:HLS AES-128 で暗号化されたストリームは、IV タグが指定されていない場合、Safari で再生に失敗します。</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD</td> 
   <td>DRM</td> 
   <td> </td> 
   <td><p>・ 12660:HTML5 プレーヤーが、期限切れの PlayReady で暗号化されたダッシュコンテンツに対して内部サーバーエラーをスローする。</p> <p>・ 16720:期間タグの start 属性が見つからない場合、DASH DRM で暗号化されたコンテンツは機能しません。</p> <p>・ 18589:DRM 保護された Dash VoD Multiperiod ストリーム（Xlink を使用）では、再生はサポートされていません。</p> <p>・ 18653:複数のキーを持つ Widevine MultiPeriod コンテンツの再生は、最初の期間で停止し、次の期間に切り替えることはできません。</p> <p>・ 18656:異なるキーで暗号化された再生可能な MultiPeriod ストリームは、再生されません。</p> <p>Dash 用の Playready 2.0 は認定されていません。</p> <p> </p> <p> </p> </td> 
   <td>12602:HLS Fairplay DRM メタデータが Safari 上の FairPlayer で繰り返しHTML5 によって更新される</td> 
   <td><p>Bento4 でパッケージ化された DASH Widevine DRM コンテンツを再生できます。 Offline Packager と Shaka Packager を使用してパッケージ化されたコンテンツは再生されません。 DASH PlayReady DRM はサポートされていません。</p> </td> 
  </tr> 
 </tbody> 
</table>

**表 19:コアAd Insertion機能 (CSAI)**

<table> 
 <tbody> 
  <tr> 
   <td><strong>コンテンツタイプ</strong></td> 
   <td><strong>機能</strong></td> 
   <td><strong>Flash</strong></td> 
   <td><strong>Firefox のHTML5、IE、Chrome、Android Chrome</strong></td> 
   <td><strong>Safari でのHTML5、iOS Safari</strong></td> 
   <td><strong>Chromecast（DASH 再生のみ）</strong></td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Pre/Mid/Post</td> 
   <td> </td> 
   <td><p>・ HLS ライブコンテンツを使用したプリロール広告は、デュアルプレーヤーモードで再生されます。</p> <p>・ HLS コンテンツを含む DASH 広告と DASH コンテンツを含む HLS 広告はサポートされていません。</p> <p>・ 19002:MSE adBreak を使用するHTML5 プレーヤー。 insertionType は、正しい挿入タイプを表す正しい値を返しません。つまり、クライアントが挿入されたか、サーバーが挿入されたかを返します。</p> <p>7794:デフォルトのコントロールバーがフルスクリーンモードで表示されるモバイルデバイス (iOS、Chrome 33 以前またはネイティブブラウザー搭載の Android) では、広告再生時にシークバーおよび早送りボタンを使用できます。</p> <p>・ 11048:メディアソース拡張機能の場合、広告から HLS ライブコンテンツに切り替えることはスムーズではありません。</p> <p>・ 16083:Android 4.4 Chrome v52 では、再生を停止した後に、HLS コンテンツを含む HLS 広告がパイプラインデコードエラーにつながる場合があります。</p> <p>・ 16097:広告ブレーク中に発生したエラーは処理されず、メインストリームの再生が停止する可能性があります。</p> <p>・ 18095:MP4 広告は、HLS ライブコンテンツではサポートされていません。</p> <p>19120:HLS コンテンツを含む HLS 広告に対して複数のシークがあると、ストリームの再生が停止する場合があります。</p> <p>・ 19131:プリロール広告ブレークからコンテンツに切り替える際に、バッファリングオーバーレイが表示される場合があります。</p> <p>・ 20296:HLS ライブストリームの場合、DVR ウィンドウでシークバックし、解決されたミッドロールをシークオーバーした後に再生が停止する可能性があります。</p> <p>・ 20298:HLS ミッドロールを含むライブストリームは、最初のミッドロール広告が DVR ウィンドウから出ると、モーメントを停止します。</p> <p>・ 20317:広告ブレークに複数の広告が含まれている場合、次の広告に切り替えたり、広告からコンテンツに切り替えたりすると、HLS ライブストリームが停止することがあります。</p> 
    <ul> 
     <li>HLS ライブストリームの DVR ウィンドウ内の広告は解決されません。</li> 
    </ul> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>VAST 2.0/3.0</td> 
   <td> </td> 
   <td>SDK は、VAST adSource に対する VMAP 応答内のシーケンス属性を保持しません。</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>VAST 2.0/3.0</td> 
   <td> </td> 
   <td>20779:SDK は、VAST adSource に対する VMAP 応答内の sequence 属性を保持しません。</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>VMAP 1.0</td> 
   <td> </td> 
   <td>12014:VMAP 繰り返し属性はサポートされていません。</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>クリエイティブの再パッケージ</td> 
   <td> </td> 
   <td>21464:広告ブレーク内の広告の 1 つに対してクリエイティブの再パッケージ化が失敗すると、広告の応答は完全に破棄されます。</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

**表 20:高度なAd Insertion機能 (CSAI)**

<table> 
 <tbody> 
  <tr> 
   <td><strong>コンテンツタイプ</strong></td> 
   <td><strong>機能</strong></td> 
   <td><strong>Flash</strong></td> 
   <td><strong>Firefox のHTML5、IE、Chrome、Android Chrome</strong></td> 
   <td><strong>Safari でのHTML5、iOS Safari</strong></td> 
   <td><strong>Chromecast（DASH 再生のみ）</strong></td> 
  </tr> 
  <tr> 
   <td>VOD</td> 
   <td>広告のみ</td> 
   <td> </td> 
   <td>20056:プレーヤーテクノロジープロパティは、広告のみ再生の場合は空のメインコンテンツに基づいているので、関連しません</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>カスタム広告ポリシー</td> 
   <td> </td> 
   <td><p>・広告の動作は、MP4 広告と MP4 コンテンツではサポートされていません。</p> <p>・ 13973:カスタム広告動作 — MSE と共に使用すると、SKIP ポリシーが complete イベントをスローしない。</p> <p>・ 14939:スキップ広告およびスキップ広告ブレークが DASH コンテンツに対して機能しないカスタム広告動作ポリシー。</p> <p>・ 17131:広告の最初のフレームが表示され、次に SKIP 広告ブレークポリシーの場合にコンテンツが再開されます。</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>コンパニオン広告/バナー広告/クリック可能な広告</td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td>リファレンスプレーヤーを使用している場合、バナー広告が表示されません。</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>VPAID 2.0</td> 
   <td> </td> 
   <td><p>・広告の動作は、VPAID 広告ではサポートされていません。</p> <p>・ 15032:広告ブレーク内の MP4 または HLS 広告と組み合わせた VPAID 広告はサポートされていません。</p> <p>・ 19001:Android とiOSで、VPAID 広告が MP4 で再生されたときに、メインコンテンツのダブルオーディオトラックが可聴になると、メインコンテンツの 1 つと広告の 1 つが再生されます。</p> <p>・ 20762:VPAID 広告は、ピクチャーインピクチャー (PIP) ではサポートされていません。</p> <p>・ 21172:VPAID 広告を含む HLS VOD コンテンツに対する再生完了イベントを受信しない。</p> <p>・ 21173:HLS VOD コンテンツおよびポストロール VPAID 広告に対して onAdBreakCompleteEvent を受信しません。</p> </td> 
   <td>VPAID 広告とメインコンテンツを切り替える際に、プレーヤーは通常モードとフルスクリーンモードを切り替えます。</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

**表 21:統合**

| **コンテンツタイプ** | **機能** | **Flash** | **Firefox のHTML5、IE、Chrome、Android Chrome** | **Safari でのHTML5、iOS Safari** | **Chromecast（DASH 再生のみ）** |
|---|---|---|---|---|---|
| VOD + Live | Adobe Analytics VHL 統合 |  | 19004:ビデオ分析のトラッキングは、UI コンフィギュレーターツールでは使用できません。 |  |  |

## 参考リソース {#helpful-resources}

* 完全なヘルプドキュメントは、 [Adobe Primetimeラーニングとサポート](https://experienceleague.adobe.com/docs/primetime.html) ページ。
