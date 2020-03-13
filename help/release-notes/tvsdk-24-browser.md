---
title: ブラウザーTVSDK 2.4リリースノート
seo-title: ブラウザーTVSDK 2.4リリースノート
description: ブラウザーTVSDK 2.4リリースノートでは、Browser TVSDK 2.4の新機能、サポートされている機能、およびサポートされていない機能、および既知の問題について説明します。
seo-description: ブラウザーTVSDK 2.4リリースノートでは、Browser TVSDK 2.4の新機能、サポートされている機能、およびサポートされていない機能、および既知の問題について説明します。
uuid: 3a1eb1a5-0e72-4658-beeb-bca8816570e7
contentOwner: dekalra
topic-tags: release-notes
products: SG_PRIMETIME
discoiquuid: d71886cb-f34b-47b2-9df7-168686478106
translation-type: tm+mt
source-git-commit: e644e8497e118e2d03e72bef727c4ce1455d68d6

---


# ブラウザーTVSDK 2.4リリースノート {#browser-tvsdk-release-notes}

ブラウザーTVSDK 2.4リリースノートでは、Browser TVSDK 2.4の新機能、サポートされている機能、およびサポートされていない機能、および既知の問題について説明します。

## はじめに {#introduction}

ブラウザーTVSDKは、高度なビデオ再生機能、コンテンツ保護および広告をブラウザーベースのビデオプレーヤーアプリケーションに追加できるツールキットです。

ブラウザーTVSDK 2.4は、ブラウザーベースのビデオアプリケーションを構築するためのJavaScript APIを提供し、次のモードでの再生のサポートを含みます。

* HTML5のみ
* HTML5（自動フラッシュフォールバックを使用）
* Flash常に

このリリースには、次の情報が含まれています。

・ブラウザ [ーのTVSDK APIドキュメント](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html)。

・ブラウ [ザTVSDKプログラミングガイド](https://helpx.adobe.com/content/dam/help/en/primetime/programming-guides/psdk_browser-tvsdk.pdf)。

・ [TVSDK for 1.4 DHLSからブラウザーTVSDK 2.4への移行ガイド](https://helpx.adobe.com/primetime/migration-guides/tvsdk-14-dhls-browser-tvsdk-24.html)。

・ブ [ラウザーTVSDK 2.4.6からバージョン2.4.7への変換](https://helpx.adobe.com/primetime/conversion-guides/browser-tvsdk-246-to-247-for-javascript.html)。

・ビルドに含まれる参照実装。

>[!NOTE]
>
>*このリリースのセキュリティに関する考慮事項の一覧については、セキュリティに関する考慮事項を参照してください。

## 新機能とサポートされる機能 {#what-s-new-and-supported-features}

このリリースのブラウザーTVSDKは、ビデオアプリケーションを強化するために使用できる新機能を提供します。

**2.4.12アップデートの新機能（ビルド204）**

次の追加機能は、Browser TVSDK 2.4.12 Update(Build 204)の一部として利用できます。

* 再生がミュートされたときにiOSで自動再生を許可するように、AdobePSDK.MediaPlayerのボリュームAPIの実装が変更されました。

・ Auditudeサーバーから受信し `auditudeSettings.ignoreVPAIDAds`たVPAID広告を無視できる新しいAPIが追加されました。 このAPIは、Flashフォールバックでは機能しません。

**バージョン2.4.11**

Browser TVSDK 2.4.11リリースの一部として、次の機能強化および追加が利用できます。

・ HLSライブセグメントフェイルオーバーは、MSEおよびFlashのフォールバックモードでサポートされています。

・ APIのサポート `AuditudeSettings.creativeRepackagingDomain` がMSEでも利用できるようになりました。 以前は、Flashフォールバックモードでのみサポートされていました。

・このリリースには、お客様の重要な問題に対する修正が含まれています。 「修正さ *れた問題* 」リストを参照してください。

**バージョン2.4.10**

Browser TVSDK 2.4.10リリースの一部として、次の機能強化および追加が利用できます。

・ TVSDKは、ログを有効または無効にするenableLogging()を提供します。 使用方法については、 [APIのドキュメ](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html)ントを参照してください。

・ TVSDKは、Adobe Analyticsを使用する場合、デフォルトチャプターをサポートしなくなりました。 アプリケーションを使用して、チャプターを定義および管理します。

・このリリースには、お客様の重要な問題に対する修正が含まれています。 「*修正された問題*a」リストを参照してください。

**バージョン2.4.9**

Browser TVSDK 2.4.9リリースの一部として、次の機能強化および追加が利用できます。

・時間の不連続性があるが、不連続マーカーがないHLS VODストリームとLiveストリームがサポートされています。

・ HLS VODおよびライブストリーム用のSafariビデオタグでは、ID3 v2.4.0フレームがサポートされます。

・セキュアな広告読み込みの実装により、APIの設定に基づいて、広告サーバーの呼び出しがセキュアなHTTPにアップグレードされます。 詳しくは、AdobePSDK.AdvertisingMetadataおよびAdobePSDK.ForceHttpsAdConfigurationクラスを参照してください。 この機能は、Flashフォールバックモードではサポートされていません。

・ VAST 3.0応答に関連付けられた広告ID情報と拡張情報が、TVSDKがアプリケーションで使用できるようになり、広告の測定にMort統合を実装するために使用できるようになりました。 詳しくは、AdobePSDK.NetworkAdInfo APIを参照してください。 これは、Flashフォールバックモードではサポートされていません。

・ AdobePSDK.ForceHttpsConfigurationクラスは使用できなくなりました。 後を継ぐ

AdobePSDK.ForceHttpsAdConfigurationクラス。

・新しいAPIであるAdobePSDK.optimizeFlashCallsを使用して、呼び出しを最適化し、FlashフォールバックモードでのHLS再生エクスペリエンスを向上できるようになりました。 これはデフォルトで無効になっています。

**2.4.8アップデートの新機能（ビルド6002）**

このアップデートには、お客様の重要な問題に関する修正が含まれています。 リストに *ついては*、「修正された問題」を参照してください。

**バージョン2.4.8**

Browser TVSDK 2.4.8リリースの一部として、次の機能強化および追加が利用できます。

・ SDKがChrome EMEに準拠するようになり、Chrome v58以降で利用できるベストプラクティスの変更が加えられました。 詳しくは、https://storage.googleapis.com/wvdocs/Chrome_EME_Changes_and_Best_Practices.pdf [*](https://storage.googleapis.com/wvdocs/Chrome_EME_Changes_and_Best_Practices.pdf)*を参照してください。

・ UIフレームワークで、Flash、広告のみ、およびターゲット情報のワークフローでHLS Access DRMがサポートされるようになりました。

・ setDRMAuthenticateData APIがUIフレームワークに追加されます。 Adobe Access DRMで保護されたストリームを再生するには、このAPIを呼び出します。 または、drmAuthenticateData属性をプレイヤーで指定できます。 詳しく [は、AdobePSDK.videoBehaviorを参 ](https://help.adobe.com/en_US/primetime/api/psdk/btvsdk-ui-framework/VideoBehavior.html)照してください。

**バージョン2.4.7**

バージョン2.4.7の新機能を次に示します。

・ UIフレームワークにUIコンフィギュレータを追加

次のいずれかの方法でプレイヤーを設定できます。

・ JSONオブジェクトの使用

・ APIの使用

JSONオブジェクトの生成に役立つように、Browser TVSDKは**UI Configurator **toolを提供します。

このツールでは、様々な設定を選択し、「**設定をテスト**」をクリックして設定を確認し、「**設定をダウンロード**」をクリックして設定をダウンロードできます。 ファイルをダウンロードした後、このファイルの内容をJSONオブジェクトとしてptp.videoPlayer APIに渡すことができます。

・ UIフレームワークへのMediaPlayerItemConfig APIの追加

advertisingMetadata、advertisingFactory、adSignalingMode、networkConfiguration、customRangeMetadata、useHardwareDecoder、subscribeTags、adTags、thumbnailScrubber、billingMetricsConfigurationなど、様々な機能は、MediaPlayerItemConfigを使用して設定できます。 詳しくは、ブラウザーTVSDK API [* *のドキュメントで、AdobePSDK.MediaPlayerItemConfigのドキュメントを参照してく](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html)ださい [](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html)。

UIフレームワークで、ネットワーク構成をプレーヤー構成に渡す方法が変更されました。

**バージョン2.4.6**

`var player = ptp.videoPlayer(‘#videoHolder', {`

`player: {`

`networkConfiguration: <network configuration object>`

`}`

`};`

**バージョン2.4.7**

`var player = ptp.videoPlayer(‘#videoHolder', {`

`player: {`

`mediaPlayerItemConfig: {`

`networkConfiguration: <network configuration object>`

`}`

`}`

`};`

* UIフレームワークでのDRMおよびAnalyticsワークフローのサポート

DRM設定とAnalytics追跡は、UIフレームワークを通じて有効にできます。

* APIの追 `AdobePSDK.embedSWFinFullScreenDiv` 加

この新しいAPIは、プレーヤーアプリケーションに対して、FlashFallback.swfファイルを埋め込むことのできるdivを柔軟に選択できるようにします。

* APIをク `getVersion`ラスから `AdobePSDK.MediaPlayer` TVSDKバージ `AdobePSDK.Version` ョン関連情報のクラスに置き換えました。 詳しくは、 `AdobePSDK.Version` APIを参照して [ください](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/AdobePSDK.Version.html)。

**バージョン2.4.6**

バージョン2.4.6の新機能を次に示します。

* **ブラウズのサポート**

Browserifyを使用すると、ブラウザーでnode.jsスタイルのモジュールを使用できます。 依存関係を定義し、すべてのバンドルを1つのJavaScriptファイルに参照できます。

* **請求**

課金の支援を受けて、ブラウザーTVSDKは、Primetimeのお客様に課金するためのプレイヤー使用指標を収集できます。

>[!NOTE]
>
>バージョン2.4.6では、非推奨のenum MediaPlayer.EventsおよびEnum PSDKErrorCodeの非推奨の定数が削除されました。詳しくは、ブラウザーTVSDK 2.4.5 [からバージョン2.4.6への変換を参照してください](https://helpx.adobe.com/primetime/conversion-guides/browser-tvsdk-245-to-246-for-javascript.html)。

**バージョン2.4.5**

バージョン2.4.5の新機能を次に示します。

* **フルイベントの再生と広告**

   HLSフルイベント再生(FER)ストリームで、広告の解決と広告の動作がサポートされるようになりました。 このサポートを有効にするには、広告シグナリングモードをオブジェクトの作成時 `MANIFEST_CUES` ににに設定してく `MediaPlayerItemConfig` ださい。

* **MediaplayerView ScalePolicyのサポート**

   アプリケーション開発者は、MediaplayerView scalePolicyプロパティを使用して、ビューに別のscalePolicyを指定できるようになりました。

* **アナモルフィックコンテンツのサポート**

   MSEおよびFlash再生を使用する場合に、アナモフィックコンテンツの再生がサポートされるようになりました。

* **選択的適用`withCredentials`**

をtrueに `withCredentials` 設定した場合、ヘッダーをワ `Access-Control-Allow-Origin` イルドカードに設定することはできません。 サーバーの応答に応じて、ブラウザーTVSDKが属性を選択的に設定 `withCredentials` します。 このサポートについて詳しくは、ブラウザーTVSDK APIドキ [ュメントを参照してくださ](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html)い。

**バージョン2.4.4**

バージョン2.4.4の新機能：

* **Chromecastサンプルアプリ**

このリリースでは、DASH VODストリームおよびDASH Widevineストリームの再生とクライアント側の広告挿入を示す、送信者および受信者アプリがサポートされます。

* **高度なフェイルオーバーのサポート**

このリリースでは、HLS VODストリームの高度なフェイルオーバーの使用例（セグメントおよびサーバーのフェイルオーバー）をサポートしています。

**バージョン2.4.3**

バージョン2.4.3の新機能：

* **DASH VODのカスタムタグ**

   インラインカスタムタグ（イベント）は、TimedMetadataオブジェクトとしてサブスクライブおよび受信できます。

* **拡張子のないストリームの再生**

   拡張子のないHLSストリームとDASHストリームがサポートされるようになりました。 マニフェストファイルの場合、リソースを読み込む際にresourceTypeを指定する必要があります。 セグメントおよびVTTファイルの場合、Content-Type応答ヘッダーを使用してコンテンツタイプが決定されます。

**バージョン2.4.2**

バージョン2.4.2の新機能：

* **APIパリティ**

APIパリティの完全なリストについては、「 [TVSDK for 1.4 DHLS to Browser TVSDK 2.4 Migration Guide」を参照してください](https://helpx.adobe.com/primetime/migration-guides/tvsdk-14-dhls-browser-tvsdk-24.html)。

* **サンプル —AESのサポート**

   このリリースでは、MSEおよびFlashのフォールバックでのSample-AES暗号化コンテンツ再生のサポートが追加されています。 Google Chromeで安全なオリジン経由でAESコンテンツをホストする必要はなくなりました。

* **AACコンテナのサポート**

   .aac拡張子を持つファイルの再生がサポートされるようになりました。 これは、オーディオ専用のストリームまたは代替オーディオにすることができます。

   >[!NOTE]
   >
   >AC3および拡張AC3コーデックは、まだサポートされていません。

* **トークン化されたストリーム再生**

コンテンツ配信ネットワーク(CDN)を介して配信されるHLSストリームは、マニフェストおよびセグメントリクエストで認証トークンを使用して検証でき、URLパラメーターまたはcookieヘッダーとして提供できます。 このようなストリームの再生がサポートされるようになりました。

**バージョン2.4.1**

バージョン2.4.1の新機能：

* **UIフレームワーク**

このフレームワークは、再生/一時停止やボリュームなどの基本的なコントロールを含め、スクラブバーの状態やクローズドキャプションの設定などの要素を簡単に追加または削除するためのAPIで構成され、JavaScriptベースのビデオプレーヤーアプリケーションのUI開発を高速化します。 コントロールに関連付けられた動作を指定し、カスタムコントロールを作成して、プレイヤーのUIにスキンを適用することができます。 これらはすべてフレームワークを通じて行われ、DOM構造を直接操作する必要はありません。

* **ライブストリームのHLS再生の強化**

このリリースでは、広告挿入による非継続性をサポートしています。 スムーズな再生を実現するために、EXT-PROGRAM-DATE-TIMEタグの後にEXT-MEDIA-SEQUENCEタグを使用して、アダプティブビットレートプロファイル間で同期を行います。

* **VPAID 2.0のサポート**

ビデオプレーヤー広告配信インターフェイス定義(VPAID)バージョン2.0は、ユーザーにリッチメディアエクスペリエンスを提供し、発行者は広告のターゲット設定、広告インプレッションの追跡およびビデオコンテンツの収益化を改善できます。 このリリースでは、ビデオオンデマンド(VOD)コンテンツ用のリニアJavaScript VPAID広告がサポートされています。

* **カスタムHLSタグ**

メディアストリームは、プレイリスト/マニフェストファイル内のタグの形式で追加のメタデータを伝送できます。 ブラウザーTVSDKを使用すると、追加のタグを指定してサブスクライブし、それらのタグがマニフェストに表示されたら通知を受け取ることができます。

* **プレイヤーのタイムラインに表示される広告マーカー**

このリリースでは、VODコンテンツとLiveコンテンツの両方のプレーヤータイムラインでの広告マーカーの表示がサポートされています。 この動作は、参照プレーヤーで確認できます。

**2.4でサポート**

バージョン2.4では、次の機能が使用できました。

* **MP3オーディオ再生**

   このリリースでは、Media Source Extensions(MSE)およびSafariビデオタグを含むブラウザーでのMP3オーディオ再生がサポートされています。

* **MP4ビデオ再生**

   次の機能がサポートされています。

   * 単一ストリーム再生
   * 広告動作と追跡を含むプリロールおよびポストロールMP4広告
   * 広告動作と追跡を含むプリロールおよびポストロールHLS広告
   * 広告動作と追跡を含むプリロールおよびポストロールDASH広告

## サポートされるプラットフォーム {#supported-platforms}

ブラウザーTVSDKには、実行する必要のあるプラットフォームとソフトウェアのレベルに固有の要件があります。 次のプラットフォームとソフトウェアレベルがサポートされています。

### デスクトップ設定 {#desktop-configurations}

* Microsoft Windows 7:

   * Internet Explorer 11+
   * Chrome 33+
   * Firefox 38以降

* Microsoft Windows 8.1

   * Internet Explorer 11+
   * Chrome 33+
   * Firefox 38以降

* Microsoft Windows 10

   * Edge+

* Apple OS X

   * Safari 9+
   * Chrome 33+
   * Firefox 38以降

### モバイルWeb設定 {#mobile-web-configurations}

* Android 4.4

   * ネイティブブラウザー
   * Chrome 33+

* Android 5.0

   * ネイティブブラウザー
   * Chrome 33+

* Android 6.0

   * ・ Chrome 33+

* Apple iOS 9

   * Safari 9+
   * Chrome 33+

* Apple iOS 10

   * Safari 9+
   * Chrome 33+

**Google Chromecast(第2世代、（DASH再生のみ）**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>技術</strong> </p> </td> 
   <td><p><strong>ブラウザーTVSDKビデオタグ</strong><sup>1</sup></p> </td> 
   <td><p><strong>ブラウザーTVSDK MSE</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>デフォルトの技術</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>iOS</p> </td> 
   <td><p>MP4とHLS</p> </td> 
   <td><p>-</p> </td> 
   <td><p>-</p> </td> 
   <td><p>ビデオタグ</p> </td> 
  </tr> 
  <tr> 
   <td><p>Android</p> </td> 
   <td><p>MP4</p> </td> 
   <td><p>HLSとDASH</p> </td> 
   <td><p>-</p> </td> 
   <td><p>MSE</p> </td> 
  </tr> 
  <tr> 
   <td><p>Apple Safari 8</p> </td> 
   <td><p>MP4とHLS</p> </td> 
   <td><p>-</p> </td> 
   <td><p>MP4とHLS</p> </td> 
   <td><p>ビデオタグ</p> </td> 
  </tr> 
  <tr> 
   <td><p>Google Chrome</p> </td> 
   <td><p>MP4</p> </td> 
   <td><p>HLSとDASH</p> </td> 
   <td><p>MP4とHLS</p> </td> 
   <td><p>MSE</p> </td> 
  </tr> 
  <tr> 
   <td><p>Mozilla Firefox</p> </td> 
   <td><p>MP4</p> </td> 
   <td><p>HLSとDASH</p> </td> 
   <td><p>MP4とHLS</p> </td> 
   <td><p>MSE<sup>2</sup></p> </td> 
  </tr> 
  <tr> 
   <td><p>Internet Explorer 11</p> <p>(Windows 7)</p> </td> 
   <td><p>MP4</p> </td> 
   <td><p>-</p> </td> 
   <td><p>MP4とHLS</p> </td> 
   <td><p>Flash</p> </td> 
  </tr> 
  <tr> 
   <td><p>Internet Explorer 11</p> <p>(Windows 8.1)</p> </td> 
   <td><p>MP4</p> </td> 
   <td><p>HLS、DASH</p> </td> 
   <td><p>MP4とHLS</p> </td> 
   <td><p>MSE</p> </td> 
  </tr> 
 </tbody> 
</table>

## 機能のマトリックス {#feature-matrix}

このリリースでサポートされる機能とサポートされない機能の一覧を次に示します。

* *MP3オーディオ機能 — コア再生*
* *MP4ビデオ機能 — コア再生*
* *MP4ビデオ機能 — コア広告の挿入*

>[!NOTE]
>
>*以下の機能一覧の表で、「Y」は、この機能が現在のリリースでサポートされていることを意味します。*

### MP3オーディオ機能 {#mp-audio-features}

**表1:コア再生{#table-core-playback}**

| カテゴリ | コンテンツタイプ | 機能 | Flash | HTML5:FF、IE、Chrome、Android Chrome | HTML5:Safari、iOS Safari |
|--- |--- |--- |--- |--- |--- |
| 再生 | MP3 VOD | 一般再生（再生、一時停止、シーク） | 未サポート | Y | Y |

1ブラウザーTVSDKのビデオタグは、ストリーミングとDRMをサポートしていません。 コーデックとコンテナのサポートは、すべてのブラウザーで同じではありません。

2 Firefoxのデフォルトは、バージョン41以前のFlash Playerです。

### MP4オーディオ機能 {#mp-audio-features-1}

**表2:コア再生**

| カテゴリ | コンテンツタイプ | 機能 | Flash | HTML5:FF、IE、Chrome、Android Chrome | HTML5:Safari、iOS Safari |
|--- |--- |--- |--- |--- |--- |
| 再生 | MP4 VOD | 一般再生（再生、一時停止、シーク） | 未サポート | Y | Y |

**表3:コア広告の挿入**

| カテゴリ | コンテンツタイプ | 機能 | Flash | HTML5:FF、IE、Chrome、Android Chrome | HTML5:Safari、iOS Safari |
|--- |--- |--- |--- |--- |--- |
| 広告挿入 | MP4 VOD | プリロール(MP4) | 未サポート | Y | Y |
| 広告挿入 | MP4 VOD | ポストロール(MP4) | 未サポート | Y | Y |

HLSまたはDASH機能のサポートについて詳しくは、以下を参照してください。

## HLS機能のマトリックス {#hls-feature-matrix}

ブラウザーTVSDKのHLS機能の機能一覧を示します。

* *HLSコア再生*
* *HLS高度な再生機能*
* *HLSコンテンツ保護機能*
* *HLSコア広告挿入機能*
* *HLSの高度な広告挿入機能*
* *HLS統合*

>[!NOTE]
>
>*以下の機能一覧の表で、「Y」は、この機能が現在のリリースでサポートされていることを意味します。*

### HLSの機能 {#hls-features}

次の機能がサポートされています。

**表4:HLSコア再生**

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
   <td><p>一般再生（再生、一時停止、シーク）</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>FER VOD</p> </td> 
   <td><p>一般再生（再生、一時停止、シーク）</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>可変ビットレート</p> </td> 
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
   <td><p>VODのみ</p> </td> 
   <td><p>VODのみ</p> </td> 
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
   <td><p>QoSとプレイヤー通知</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>制限付きQoSのサポート</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>cookieヘッダーのサポート</p> </td> 
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
   <td><p>アダプティブの設定</p> <p>ビットレート制御</p> </td> 
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
   <td>オーディオの遅延バインディング</td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>プラットフォームの制限</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>302リダイレクト</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>プラットフォームの制限</p> </td> 
  </tr> 
 </tbody> 
</table>

**表5:HLS高度な再生機能**

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
   <td><p>スムーズトリック再生</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>プラットフォームの制限</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>ID3の解析</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>不連続マーカのサポート</p> </td> 
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

**表6:HLSコンテンツ保護機能**

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
   <td><p>Adobe Access</p> </td> 
   <td><p>未サポート</p> </td> 
   <td><p>FairPlay</p> </td> 
  </tr> 
 </tbody> 
</table>

**表7:HLSコア広告挿入機能**

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
   <td><p>広告挿入</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>プリロール(MP4/HLS)</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>広告挿入</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>ミッドロール(HLS)</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>プラットフォームの制限</p> </td> 
  </tr> 
  <tr> 
   <td><p>広告挿入</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>ポストロール(MP4/HLS)</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>広告挿入</p> </td> 
   <td><p>FER VOD</p> </td> 
   <td><p>広告の解像度と動作</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>プラットフォームの制限</p> </td> 
  </tr> 
  <tr> 
   <td><p>広告挿入</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>デフォルトの広告ポリシー</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>プラットフォームの制限</p> </td> 
  </tr> 
  <tr> 
   <td><p>広告挿入</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>VAST 2.0/3.0</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>広告挿入</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>VMAP 1.0</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>広告挿入</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>クリエイティブの再パッケージ化（MP4からHLS）</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
 </tbody> 
</table>

**表8:HLSの高度な広告挿入機能**

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
   <td><p>広告挿入</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>広告のみ</p> </td> 
   <td><p>未サポート</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>広告挿入</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>ターゲット設定パラメーター</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>広告挿入</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>カスタムパラメータ</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>広告挿入</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>カスタム広告ポリシー</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>プラットフォームの制限</p> </td> 
  </tr> 
  <tr> 
   <td><p>広告挿入</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>遅延広告読み込み</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>未サポート</p> </td> 
   <td><p>プラットフォームの制限</p> </td> 
  </tr> 
  <tr> 
   <td><p>広告挿入</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>コンパニオン広告、バナー広告、クリック可能な広告</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>広告挿入</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>VPAID 2.0</p> </td> 
   <td><p>SWF</p> </td> 
   <td><p>JavaScript</p> </td> 
   <td><p>JavaScript</p> </td> 
  </tr> 
 </tbody> 
</table>

**表9:HLS統合{#table-hls-integrations}**

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
   <td><p>Adobe Analytics VHLの統合</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
 </tbody> 
</table>

## DASH機能のマトリックス {#dash-feature-matrix}

ブラウザーTVSDKのDASH機能の機能一覧を示します。

・ *DASHコア再生機能*

・ *DASH高度な再生機能*

・ *DASHコンテンツ保護機能*

・ *DASHコア広告挿入機能*

・ *DASHの高度な広告挿入機能*

・ *DASH統合*

>[!NOTE]
>
>以下の機能一覧の表で、Yは、この機能が現在のリリースでサポートされていることを意味します。

### DASH機能 {#dash-features}

次の機能がサポートされています。

**表10:DASHコア再生機能**

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
   <td><p>一般再生（再生、一時停止、シーク）</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>FER VOD</p> </td> 
   <td><p>一般再生（再生、一時停止、シーク）</p> </td> 
   <td><p>未サポート</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>可変ビットレート</p> </td> 
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
   <td><p>VODのみ</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>フェイルオーバー</p> </td> 
   <td><p>VODのみ</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>QoSとプレイヤー通知</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>cookieヘッダーのサポート</p> </td> 
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
   <td><p>可変ビットレートコントロールの設定</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>カスタムタグ(EventStream)</p> </td> 
   <td><p>VODのみ（インライン）</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>遅延したオーディオ</p> </td> 
   <td><p>VODのみ</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>302リダイレクト</p> </td> 
   <td><p>VODのみ</p> </td> 
  </tr> 
 </tbody> 
</table>

**表11:DASH高度な再生機能**

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
   <td><p>スムーズトリック再生</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>ID3の解析</p> </td> 
   <td><p>未サポート</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>複数期間のサポート</p> </td> 
   <td><p>VODのみ</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>トークン化ストリーム</p> </td> 
   <td><p>未サポート</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>請求</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
 </tbody> 
</table>

**表12:DASHコンテンツ保護機能**

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
   <td><p>未サポート</p> </td> 
  </tr> 
  <tr> 
   <td><p>コンテンツ保護</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Sample-AES</p> </td> 
   <td><p>未サポート</p> </td> 
  </tr> 
  <tr> 
   <td><p>コンテンツ保護</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>DRM</p> </td> 
   <td><p>・ Chrome、Firefox 47以降、Chromecast上のWidevine</p> <p>・ Windows 8.1およびEdge上のInternet ExplorerでのPlayReady</p> <p>・ Windows Firefox向けPrimetime DRM（ビデオのみ）</p> </td> 
  </tr> 
 </tbody> 
</table>

**表13:DASHコア広告挿入機能**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>カテゴリ</strong></p> </td> 
   <td><p><strong>コンテンツタイプ</strong></p> </td> 
   <td><p><strong>機能</strong></p> </td> 
   <td><p><strong>HTML5 FF、IE、Chrome、Android Chrome</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>広告挿入</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>プリロール(MP4/DASH)</p> </td> 
   <td><p>VODのみ</p> </td> 
  </tr> 
  <tr> 
   <td><p>広告挿入</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>ミッドロール(DASH)</p> </td> 
   <td><p>VODのみ</p> </td> 
  </tr> 
  <tr> 
   <td><p>広告挿入</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>ポストロール(MP4/DASH)</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>広告挿入</p> </td> 
   <td><p>FER VOD</p> </td> 
   <td><p>広告の解像度と動作</p> </td> 
   <td><p>未サポート</p> </td> 
  </tr> 
  <tr> 
   <td><p>広告挿入</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>デフォルトの広告ポリシー</p> </td> 
   <td><p>VODのみ</p> </td> 
  </tr> 
  <tr> 
   <td><p>広告挿入</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>VAST 2.0/3.0</p> </td> 
   <td><p>VODのみ</p> </td> 
  </tr> 
  <tr> 
   <td><p>広告挿入</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>VMAP 1.0</p> </td> 
   <td><p>VODのみ</p> </td> 
  </tr> 
  <tr> 
   <td><p>広告挿入</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>クリエイティブの再パッケージ化（MP4からDASH）</p> </td> 
   <td><p>未サポート</p> </td> 
  </tr> 
 </tbody> 
</table>

**表14:DASH Advanced広告挿入機能**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>カテゴリ</strong></p> </td> 
   <td><p><strong>コンテンツタイプ</strong></p> </td> 
   <td><p><strong>機能</strong></p> </td> 
   <td><p><strong>HTML5</strong> FF、IE、Chrome、Android Chrome</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>広告挿入</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>広告のみ</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>広告挿入</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>ターゲット設定パラメーター</p> </td> 
   <td><p>VODのみ</p> </td> 
  </tr> 
  <tr> 
   <td><p>広告挿入</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>カスタムパラメータ</p> </td> 
   <td><p>VODのみ</p> </td> 
  </tr> 
  <tr> 
   <td><p>広告挿入</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>カスタム広告ポリシー</p> </td> 
   <td><p>未サポート</p> </td> 
  </tr> 
  <tr> 
   <td><p>広告挿入</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>遅延広告読み込み</p> </td> 
   <td><p>未サポート</p> </td> 
  </tr> 
  <tr> 
   <td><p>広告挿入</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>コンパニオン広告，バナー広告，クリック可能な広告</p> </td> 
   <td><p>未サポート</p> </td> 
  </tr> 
  <tr> 
   <td><p>広告挿入</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>VPAID 2.0</p> </td> 
   <td><p>未サポート</p> </td> 
  </tr> 
 </tbody> 
</table>

**表15:DASH統合**

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
   <td><p>Adobe Analytics VHLの統合</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
 </tbody> 
</table>

## 修正された問題 {#issues-fixed}

**2.4.12アップデート（ビルド204）で修正された問題**

ブラウザーTVSDKバージョン2.4.12の更新（ビルド204）で、次の問題が修正されました。

・ **21647**- TVSDKは、オーディオがミュートされている場合、iOSデバイスでのビデオの自動再生を許可する必要があります。

・ **21465**- DRM保護されたDASHストリームをDASHライブストリームの再生後に再生すると、エラーキーシステムアクセス拒否が受信されました。

・ **21442**— プリロール広告がユーザーのジェスチャーで再生された後、iOS Webでコンテンツの自動再生を有効にします。

・ **21240**- Auditude/VMAPから解析されたVPAID広告をフィルタリングするAPIを提供します。

**バージョン2.4.11で修正された問題**

ブラウザーTVSDKバージョン2.4.11で、次の問題が修正されました。

**コア再生機能：**

・ **19192**:TVSDKは、TextFormat:bottomInsetとTextFormat:safeAreaを実装するようになりました。 これらの機能強化により、コントロールバーが画面に表示されている場合は、クローズドキャプションの位置を変更できます。

・ **21009**:クローズドキャプションは、新しいキャプションが表示されるまで連続してシークする場合に、画面上で保持されます。

・ **21141**:セグメントの追加中に競合条件が発生したため、シークバックが拒否されました。

・ **21142**:プレーヤーがINITIALIZED状態の場合に、シーク可能な再生範囲を使用可能にする。 これらの変更により、位置での開始セッションがサポートされるようになりました。

・ **21363**:DASHストリームの広告挿入後、608/708クローズドキャプションが同期されなくなる。

**広告挿入機能：**

・ **21179**:VODコンテンツを使用したミッドロール関連の問題（長い一時停止、黒いフレーム）が、ad.primaryAsset.adParametersプロパティを正しく設定することで解決されるようになりました。

・ **21257**:MP4が有効なMIMEタイプではなく、クリエイティブの再パッケージ化機能が有効な場合は、ビットレートが最も高いMP4ファイルがトランスコード用に選択されます。

・ **21361**:追加の正規化ルールをサポートするため、TVSDKは、クリエイティブパッケージ化リクエストのクエリパラメーターとしてVAST応答から広告システムとクリエイティブIDを渡すようになりました。

**バージョン2.4.10で修正された問題**

ブラウザーTVSDKバージョン2.4.10で、次の問題が修正されました。

**コア再生機能：**

・ **21060**:不連続を含むHLSストリームと、ISO BMFFボックスがストリームの最後まで実行される場合に、無効なコーデックエラーが発生しました。

・ **21045**:プレイリストの最初のビデオ再生が完了した後、iOSで自動再生が機能しない。

・ **20975**:フレームレートは、ChromeブラウザーのQoSプロバイダーからNaNとして返されます。

・ **20823**:データのないセグメントが発生した場合に、サポートされていないコーデックエラーが発生する。

・ **20769**:SDKは、ABRポリシーに基づいて即座に切り替わるのではなく、シーク時に現在のビットレートで開始するようになりました。

・ **20031**:IE 11(Windows 8.1)で縦長モードの場合、ビデオ画面が小さくなります。 コンテンツ保護機能：

・ **19316**:HLS AES-128ストリームの場合、復号化に失敗したセグメントをスキップします。

**バージョン2.4.9で修正された問題**

ブラウザーTVSDKバージョン2.4.9で、次の問題が修正されました。

**コア再生機能：**

・ **13407**:Firefoxが再生中に「ontimeupdate」イベントの送信を停止すると、DASHストリームが停止する場合があります。

・ **16380**:MSEを介して、一致しない開始時間を持つセグメントのミックスオーディオビデオコンテンツ再生中に、表現間のオーディオ同期エラーがABRスイッチに蓄積され、最終的にエラーが発生します（Chromiumの問題#663686）。

・ **17985**:特定のISO-BMFFストリームをFirefoxブラウザーで再生すると、再生が停止する（Firefoxの問題#1342913）。 これは、Firefox v53以降で修正されました。

・ **19141**:Uncaught (in promise) ReferenceError:幅が定義されていません。

・ **18997, 19299**:セグメントの境界でのビデオのちらつきの問題。 これは、SDKが最後のサンプルのコンポジションのタイムオフセットを正しく計算していなかったために発生していました。

・ **19780**:Firefox v53でHLSコンテンツおよびHLS Adの再生が開始されない（Firefoxの問題#354653）。

・ **20046**:時間指定メタデータオブジェクトとして受け取った場合、プログラムの日時が値ではなくキーとして受け取られます。

・ **20047**:useDefaultResizeHandlerは、Flashのフォールバックでエラーをスローします。

・ **20179**:Flash Player v25.0.0.171でFlashフォールバックが機能しない。

・ **20293**:Firefoxでは、一部のHLSストリームのデータのバッファリングが停止し、停止する。

・ **20626**:再生時間がゼロのビデオサンプルの処理が正しくないため、Chromeでメディアデコードエラーが発生する。

・ **20078**:再生がブラウザーエラー「QuotaExceeded」で停止する。

・ **18639**:HLSライブストリーム608 CCで、テキストがスペルミスのあるテキストとして表示される場合があります。

・ **20028**:ClosedCaptionsのサイズパラメーターでは、フォントサイズは変更されません。

・ **20613**:クローズドキャプションボックスは互いに重なり合うので、読みにくくなります。

**コア広告挿入(CSAI)の機能：**

・ **20043**:複数の広告とサードパーティのリダイレクトを含む広告インプレッションと広告トラッキングの呼び出しが見つかりません。

・ **2004**:クリエイティブの再パッケージ化を使用する場合、広告の時間内のすべての広告を正常に再パッケージ化する必要があります。そうしないと、広告の時間が完全に破棄されます。

・ **20097**:広告マニフェストが使用できない場合、20秒のタイムアウトを待たずに、広告の再生がスキップされ、メインコンテンツが直ちに再開されます。

**バージョン2.4.8のアップデート（ビルド6002）で修正された問題**

ブラウザーTVSDKバージョン2.4.8の更新（ビルド6002）で、次の問題が修正されました。

・ **14126:** MSEソースバッファーの内部ギャップが原因で、Firefoxでの再生が停止する場合があります（問題#1316024）。 再生を再開するには、シークを試みてください

・ **19608:** Auditude VMAP応答のtimeoffset値を順守するように修正しました。

・ **19635:** Windows 10上のInternet Explorer 11でのビデオの停止を修正しました。

・ **19761:** HLSでのABRの問題を修正しました。

・ **19780:** Mozilla Firefox v53で壊れていたHLSコンテンツを含む広告再生を修正しました。

・ **1987および19744:** この問題により、シーク操作後のビットレート選択の矛盾が修正されました。 現在は、シーク時のビットレート選択は、現在のビットレートの低い値と、起動時のビットレートです。

・ **19881:** 再生が停止し、バッファリングオーバーレイが、3 ～ 4回シークが実行された後、無限に表示される。

・ **19884:** Chrome 59 Beta Verified Media Path(VMP)の要件への準拠を確認します。 bTVSDKは、Chrome 59ベータ版でWidevine DRMコンテンツを再生できました。

・ **19916:** UIフレームワークでのDRM再生が中断されました。 現在は、メタデータにポリシーがない場合でも、acquireLicenseを呼び出します。

**バージョン2.4.8で修正された問題**

ブラウザーTVSDK 2.4.8リリースで、次の問題が修正されました。

・ **10075**:タイムラインの前のシーク時に、再生完了イベントがFirefoxおよびChromeで受信されず、シークイベントがFirefoxで受信されなかった問題を修正しました。

・ **15775**:Windows 8.1 Internet Explorerで再生完了イベントを受信しない。

・ **17306**:SSAIストリームの場合、再生がサポートされます。 ステッチされた広告の追跡はサポートされていません。

・ **19142**:巻き戻しを行うと、ビデオプレーヤーは永久にバッファリング状態を維持します。

・ **19218**:広告マーカーは、UIフレームワークを通じては使用できません。

・ **19219**:広告のみ再生はUIフレームワークを通じては機能しません。

・ **1922**:AES-128キーはプレイリストに対して1回リクエストされ、その後のリクエストはキャッシュから処理されます。 以前は、各セグメントに対してリクエストが行われていました。

・ **19597**:&quot;Uncaught TypeError:Chrome Canaryビルドで「未定義のログ」のプロパティを読み取れません。

・ **19605**:Flashフォールバックモードの場合、adRequestDomainが使用できませんでした。

・ **19608**:HLSライブストリームにVMAP広告が挿入されなかった問題を修正しました。 SDKは、キューマーカーを考慮し、VMAP応答の時間オフセット値に依存しなくなりました。

・ **19637**:広告のみ再生すると、広告の最後にスクリプトエラーが発生します。

・ **19732**:CRSプレイリストの要求が404エラーで失敗していた問題を修正しました。 ブラウザーTVSDKからの1401および1403のリクエストが、この問題を解決するために更新されました。

・ **19762**:acquireLicenseは、setAuthenticationTokenの前に呼び出され、トークンの有効性に関係なく有効なライセンスが返されたために使用されました。 この問題は現在修正され、acquireLicenseはsetAuthenticationTokenの応答後にのみ呼び出されます。

**バージョン2.4.7で修正された問題**

バージョン2.4.7では、次の問題が修正されました。

・ **8397**:セグメントがキーフレームで始まらない場合、Adobe Media Serverを通じて生成されたHLSライブストリームが再生されないことがあります。

・ **13606**:ChromeブラウザーのHLSストリームに関する複数のシーク関連の問題が修正されました。

・ **14807**:Chromeブラウザーで、play()の直後にシークまたは一時停止がトリガーされると、再生が次のエラーDOMExceptionで停止する場合があります。play()要求が呼び出しによって中断されました…（Chromiumの号593273）。

・ **19085**:volume、abrControlParameters、ccStyleなどのMediaPlayerパラメーターは、プレイヤーのリセット時にデフォルトに設定されません。

**バージョン2.4.6で修正された問題**

バージョン2.4.6では、次の問題が修正されました。

・ **18093**:FlashフォールバックモードでFlash Playerバージョン24を使用すると、サブスクライブされたタグの横のタグのTimedMetadataが返されます。

**バージョン2.4.4で修正された問題**

バージョン2.4.4では、次の問題が修正されました。

・ **8711**:MSEでは、608/708のキャプションはデフォルトで左揃えされます。

・ **13934**:広告のABR設定は、HLSライブストリームで再生する場合は適用できません。

・ **14079**:DVR時間の少ないHLSライブストリームの長さは、ネットワークの遅延の問題が原因で再生が遅れる可能性があるので、失敗する可能性があります。 再生を再開するには、ライブポイントをクリックします。

・ **15037**:プレイヤーUIフレームワークに付属のサンプルは、Windows 7上のMicrosoft Internet Explorer 10では機能しません。

・ **15913**:HLS VODストリームの場合、マニフェストの応答が304未変更の場合、Chromeではストリームは再生されません。 これは、Chrome v55（Chromiumの問題633696）以降に修正されました。

・ **16103**:Android Chromeでは、帯域幅が低い状態で、Uncaught TypeErrorが発生して再生が停止する場合があります。未定義のエラーのプロパティ&#39;programDateTime&#39;を読み取れません。

・ **16265**:HLS VODストリームとライブストリームの場合、非連続性間のシークは機能しません。

・ **16709**:PDTと不連続マーカーを使用してHLS Liveストリームを再開すると、プレーヤーがバッファリングで動作しなくなる場合があります。

## 既知の問題と制限 {#known-issues-and-limitations}

ブラウザーTVSDKの制限事項と既知の問題を以下に示します。

**表16:コア再生機能**

<table> 
 <tbody> 
  <tr> 
   <td><strong>コンテンツタイプ</strong></td> 
   <td><strong>機能</strong></td> 
   <td><strong>Flash</strong></td> 
   <td><strong>Firefox、IE、Chrome、Android ChromeのHTML5</strong></td> 
   <td><strong>HTML5 in Safari、iOS Safari</strong></td> 
   <td><strong>Chromecast（DASH再生のみ）</strong></td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>一般再生（再生、一時停止、シーク）</td> 
   <td><p>・ HLS以外のメディア形式はサポートされていません。</p> <p>8799:Flashのフォールバックでは混合コンテンツは扱われないので、コンテンツ、広告、その他のURLが混合コンテンツ（安全なコンテンツと安全でないコンテンツを一緒に）に結び付かないようにする必要があります。</p> <p>・ 19271:UIフレームワークを介したマルチビュー再生は、Flashフォールバックモードではサポートされていません。</p> <p>・ Windows 7上のMicrosoft Internet Explorer 8および9では、Flashのフォールバックが機能しません。これらのバージョンはSDKでサポートされていません。</p> <p>・ 20262:Flashのフォールバックにより、ターゲット情報リストにカスタムパラメータが追加されます。 また、FlashとMSEの場合、カスタムパラメータの優先順位も異なります。</p> <p>・ 20653：ブラウザーTVSDK Flashフォールバックは、Creators Updateを使用するWin10では機能しません。</p> <p>・ Flash Fallbackは、Flash Playerバージョン23以降で機能します。</p> <p>・ 20087 - Chrome 59ベータ版(</p> <p>Flash 25.0.0.171</p> <p>ベータ版（デフォルト）では、HLS再生がFlashフォールバックモードで動作しません。 カナリアではうまくいっています。</p> </td> 
   <td><p>・ 12563:オーディオコーデックmp4a.40.02を含むダッシュストリームは、MPDのオーディオコーデック文字列がサポートされていないため、Firefoxで再生されません。 オーディオコーデックmp4a.40.2がサポートされています。</p> <p>15029:UIフレームワークのmultiViewでビデオを切り替える際に、再生/一時停止ボタンがそれに応じて更新されない。</p> <p>・ 16034:Windows 8.1 IEで、reset()を呼び出すと、不明なMIMEタイプのエラーが発生します。 再生を再開するには、メディアを再読み込みしてください。</p> <p>・ 18235:広告を含むDASH VODストリームで、特定のシークの問題が発生します。</p> <p>・ 18727:エラーAPIはMSEではサポートされていません</p> <p>18750:SDKとUIの両方のフレームワークおよびUIフレームワークで、リソースの読み込み後に追加されたイベントリスナーのIDLEイベントとInitializing StatusChangeイベントが正しくない場合があります。</p> <p>・ 18889:MediaPlayerがERROR状態の場合、viewオブジェクトは返されません。</p> <p>・ 19039:AdobePSDKの場合。 MediaPlayer. seekToLocal()をEOFより大きい値で使用すると、MSEの場合は再生が最初から開始されます。</p> <p>・ 19049:Chrome、IE、Firefox上のFlash Playerで、再生中にビデオがブロックされた場合にエラー状態が報告されませんでした。</p> <p>・ 17205:オーディオの再生が継続する間、ビデオの再生が数時間、ミュクスされていないストリームの再生で停止する（Chromiumの問題# 664033）。</p> <p>・ 12308:composition_time_offsetが指定されたDASHストリームに、ChromeブラウザーでtimeStampOffsetが適用され、負のデコード時間が発生する場合があり、MEDIA_ERR_SRC_NOT_ SUPPORTEDエラーが発生する（Chromiumの問題#398141）。</p> <p>・ 14126:MSEソースバッファの内部ギャップが原因で、Firefoxでの再生が停止する場合がある（問題番号1316024）。 再生を再開するには、シークを試してみてください。</p> <p>・ 19115:MS EdgeおよびIE 11（Win 8.1および10）は、CORSリダイレクトで「Origin」を「null」に設定しませんが、ヘッダーが「null」でないため、再生エラーが発生するので失敗します。</p> <p>・ 19861：再生済みのメディアのソースバッファに対する追加動作の問題 Chromeは、追加されたフラグメント（moovを含む）を拒否し、その後のデコードエラーの原因となります。 （Chromiumの問題#735335）</p> <p>19921:バッファーが正常に完了した場合でも、特定のHLSコンテンツの再生が停止する（Chromiumの問題#713540）</p> <p>・ 20444:IEおよびEdgeでバッファー範囲の終わりをシークすると、再生が停止する場合があります。</p> <p>・ 20511:広告の有無に関わらず、HLSストリームでシーク拒否が観察される場合があります。</p> <p>・ 20743:Windows 10 Chromeでは、HLS Liveストリームは、MP4プリロール再生の数秒前に再生されます。</p> <p>・ 21043:メタデータがないため、初期読み込み時にビデオディメンションが正しくない可能性があります。</p> <p>・ 21115:プリロール広告がプレイリストのビデオで使用可能な場合、再生を開始するには、Androidユーザージェスチャが必要です。</p> <p>・ HLS Liveはタイムスタンプのロールオーバーをサポートしていません。</p> <p>・ AAC-SSRオーディオはサポートされていません。</p> <p>オーディオコーデックAC3および拡張AC3はサポートされていません。</p> <p>・タイムスタンプの不連続性があるが、不連続なマーカーがないストリームの場合</p> <p>・ジャンプが原因で、再生に問題が発生し、シークが正しく行われない可能性があります。</p> <p>・コンテンツの長さと再生時間が一致しない場合があります。</p> <p>・表示とレンディション間の不連続性は、他の条件と一致すると、同期と停止の問題を引き起こす可能性があります。</p> <p>・キャプションとWebVTTがストリームの終わりの近くに表示されない場合があります。</p> <p>・オーディオコーデックの変更は、タイムスタンプのジャンプに対してはサポートされません。</p> <p>・広告の挿入はサポートされていません。</p> <p>・早送りトリックモードを使用すると、Win 8.1 IE 11で再生ループが発生する場合があります（MSの問題#12446268）。</p> <p>ダッシュ：</p> <p>・ライブストリームの場合 — 動的タイプのライブプロファイルがサポートされています。</p> <p>・ VoDストリームの場合 — 静的タイプのライブプロファイルがサポートされます。</p> <p>VoDストリームの場合 — オンデマンドプロファイルは広告ワークフローに対して認証されていません。</p> </td> 
   <td><p>・ DASH LiveおよびDASH Video on Demandストリームはサポートされていません。</p> <p>・ PIP（ピクチャインピクチャ）ビデオ再生は、iOSのフルスクリーンモードではサポートされていません。</p> <p>Safari（ビデオタグ）拡張で、正しいコンテンツタイプのヘッダーがないとマニフェストが少なくなりません。</p> </td> 
   <td><p>・送信者アプリ内のapplicationIDは、受信者のURLをカスタム受信者アプリとして登録する際に生成されるものと同じである必要があります。</p> <p>・ DASHワークフローに対しては、リファレンスプレイヤーが認定されています。 UIフレームワークが認証されていません。</p> <p>サポートされるメディアコーデックの一覧については、こちらを参照 <a href="https://developers.google.com/cast/docs/media"><em>してくださ</em></a>い。</p> </td> 
  </tr> 
  <tr> 
   <td>FER VOD</td> 
   <td>一般再生（再生、一時停止、シーク）</td> 
   <td> </td> 
   <td>18098:HLS LBA FERストリームで、一部のシークの問題が観察されます。</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>アダプティブビットレート</td> 
   <td><p>・ 2007:バッファー範囲内のシーク時にバッファーを書き換えます。</p> <p>20080:Flash ABRの動作はMSEと一致しません。</p> </td> 
   <td><p>・ ABRストリーム内のオーディオのみのフォールバックバリアントは、バッファーに関する制限のため無視されます。</p> <p>・ 12289:ABR制御パラメーターは、ミュンクス化されていないHLS/DASHストリームの場合は、オーディオに適用されません。</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>608/708キャプション</td> 
   <td> </td> 
   <td><p>・ 7810:Android 4.4.4では、Chromeはプレーヤーが使用する基本的なCSSフォントファミリーをサポートしていないようで、フォントスタイル変更機能が動作しない。</p> <p>・ 608キャプションの場合、CCチャネルは変更できません。</p> <p>・高度なスタイル設定機能は、608キャプションに対してはサポートされていません。</p> <p>埋め込みキャプション(608/708)は、アクセシビリティタグを介して署名されます。</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>WebVTT</td> 
   <td> </td> 
   <td><p>・ 5206:WebVTTファイルの領域タグは、キャプションを表示する際にプレーヤーで無視されます。</p> <p>・ DASH:フラグメント化/セグメント化されたVTTファイルはサポートされていません。</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>マニフェストのフェイルオーバー</td> 
   <td>21056:Flashフォールバックを使用すると、再生中にプライマリストリームが404エラーを返した場合、ライブストリームに対してフェイルオーバーは発生しません。</td> 
   <td>マニフェストのフェイルオーバーは、コンテンツに対してのみ適用され、広告には適用されません。</td> 
   <td>プレイリストのフェイルオーバーが見つからない場合は、HTTPエラーコード404に対してのみSafariで機能します。</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>高度なフェイルオーバー</td> 
   <td> </td> 
   <td><p>・セグメントのフェイルオーバーでは、使用できないセグメントのスキップと再生の継続はサポートされません。</p> <p>20533:プレイリスト内の見つからないセグメントはDiscontinuityとして扱われ、次に使用可能なセグメントから再生が再開されます。</p> <p>21267:フェイルオーバーによるストリームの切り替えは、古いセグメントのダウンロードにつながる場合があります。</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>QoSおよびプレイヤー通知</td> 
   <td>21129:Flashフォールバックの場合、フレームレートは使用できません。</td> 
   <td><p>• 11170:</p> <p>Flashフォールバックを使用するブラウザーTVSDKとは異なり、Timed_Eventは、MSEを使用するブラウザーTVSDKでは使用できません。</p> <p>21129:ライブストリームのフレームレートは計算されません。</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>cookieヘッダーのサポート</td> 
   <td> </td> 
   <td> </td> 
   <td><p>withCredentialsフラグとcookieヘッダーは、Safariではサポートされていません。</p> <p>21051:SafariでCookieを許可するには、環境設定/プライバシーから「CookieとWebサイトのデータ」設定を有効にします。</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>カスタムタグ</td> 
   <td>14763:#で始まるカスタムタグ以外はサポートされません。 現在は、Flashのフォールバック中に、TimedMetadataオブジェクトが作成され、そのタグに対してレポートされます。</td> 
   <td>インバンドのカスタムタグを持つストリームは認証されません。</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>遅延バインディングオーディオ</td> 
   <td> </td> 
   <td><p>・広告挿入は、HLSライブLBAストリームではサポートされていません。</p> <p>・ 17273:HLS VOD LBAストリームは、フェイルオーバー時にデフォルトのレンディションに切り替わり、最後に選択した状態に戻すことはできません。</p> <p>・ 20251:HLSライブLBAストリームがシーク時に停止する場合があります。</p> <p>・ 20497:HLS LBAの無音ストリームに、ストリームの終わり近くにオーディオまたはビデオのフレームがない場合、プレイヤーはバッファリング状態のままになります。</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>302リダイレクト</td> 
   <td> </td> 
   <td><p>15787: 302</p> <p>リダイレクトの最適化は、XMLHttpRequestオブジェクトのresponseURLプロパティをサポートしていないので、Windows EdgeおよびIEブラウザではサポートされません。</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

**表17:高度な再生機能**

<table> 
 <tbody> 
  <tr> 
   <td>コンテンツタイプ</td> 
   <td>機能</td> 
   <td>Flash</td> 
   <td><strong>Firefox、IE、Chrome、Android ChromeのHTML5</strong></td> 
   <td><strong>HTML5 in Safari、iOS Safari</strong></td> 
   <td><strong>Chromecast（DASH再生のみ）</strong></td> 
  </tr> 
  <tr> 
   <td>VOD</td> 
   <td>オフセットでの再生</td> 
   <td><p>特定のオフセット値での再生の開始は、MP4コンテンツをサポートしていません。</p> </td> 
   <td>20492:オフセットの前のミッドロール広告は、コンテンツがオフセット値から再開される前に再生されます。</td> 
   <td>オフセット機能を使用した再生はiOSではサポートされていません。</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD</td> 
   <td>トリック再生</td> 
   <td>iFrameレンディションを持たないストリームでは、スムーズなトリックプレイは機能しません。</td> 
   <td><p>・トリック再生アダプティブはFirefoxおよびInternet Explorerではサポートされていないので、これらのブラウザーでは逆トリックモードを使用できません。</p> <p>・広告と共にコンテンツを再生する場合は、トリックプレイを使用できません。</p> <p>・ 10435:DASH再生中に、Internet Explorerでのフォワードトリック再生時にビデオがフリーズする(Win 8.1)</p> <p>断続的に これは、ビデオ要素playbackRateプロパティをトリック再生の適合なしで使用しているためです。</p> <p>14182:Chromeブラウザーで巻き戻し中にシークイベントが受信されない場合があり、トリックモードが機能しない場合があります。</p> <p>・ 14942:再生速度は、非トリック再生ストリームの場合でもChrome for Androidで設定できますが、設定は適用されず、通常の速度で再生が続行されます。</p> <p>・ 17308:シークはトリック再生モードでは機能しません。</p> <p>・ 17309:Chromeブラウザーでは、逆トリックモードを2秒以上維持することはできません。</p> <p>19272:DASHストリームの場合、Windows 10 Edgeブラウザーでトリック再生がバッファリングから回復しない場合がある。</p> </td> 
   <td>巻き戻しトリックモードはサポートされていません。</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>ID3の解析</td> 
   <td>20346:ID3フレームのテキストエンコーディングバイトも、SDKから返されます。</td> 
   <td><p>オーディオデータ転送ストリーム(ADTS)で使用できるID3タグは、SDKでは無視されます。</p> <p>・ 12378:ID3時間指定メタデータは、MSEをサポートするFlashとブラウザーで異なる時間に解析されるので、参照プレイヤーのタイムラインでの表示動作も異なります。</p> <p>・ 19247:ID3の解析は、UIフレームワークではサポートされていません。</p> </td> 
   <td><p>・ 20323:AACセグメントの最初のサンプルのタイムスタンプを示すために使用されるPRIV ID3タグがSafariで解析されない（Safariの問題#32422733）</p> <p>・ 20350:特定のデバイス（MAC OS X 10.1、iPad10など）では、Safariはトリックモードの場合にキュー変更イベントを提供しないので、ID3フレームを受信しません。 （Safariの問題#32450526）</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>不連続マーカのサポート</td> 
   <td> </td> 
   <td><p>・クライアント側の広告挿入は、不連続性を含むHLSストリームではサポートされません。</p> <p>・オーディオコーデックの変更は、HLSストリームの非連続性を超えて行うことはできません。</p> <p>・オーディオトラックスイッチは、不連続なマーカーを持つHLSストリームに対してはサポートされていません。</p> </td> 
   <td>不連続シーケンス番号は、Safariでの再生に不連続なHLSストリームの要件です。</td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

**表18:コンテンツ保護機能**

<table> 
 <tbody> 
  <tr> 
   <td><strong>コンテンツタイプ</strong></td> 
   <td><strong>機能</strong></td> 
   <td><strong>Flash</strong></td> 
   <td><strong>Firefox、IE、Chrome、Android ChromeのHTML5</strong></td> 
   <td><strong>HTML5 in Safari、iOS Safari</strong></td> 
   <td><strong>Chromecast（DASH再生のみ）</strong></td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>AES-128</td> 
   <td> </td> 
   <td>バイト範囲は、AES-128で暗号化されたコンテンツではサポートされません。</td> 
   <td>12324:HLS AES-128で暗号化されたストリームは、IVタグが指定されていない場合、Safariでの再生に失敗します。</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD</td> 
   <td>DRM</td> 
   <td> </td> 
   <td><p>・ 12660:HTML5プレーヤーが、期限切れのPlayReady暗号化ダッシュコンテンツに対して内部サーバーエラーをスローする。</p> <p>・ 16720:期間タグの開始属性がない場合、DASH DRMで暗号化されたコンテンツは機能しません。</p> <p>・ 18589:DRM保護されたDash VoD MultiperiodストリームのXlinkでの再生はサポートされていません。</p> <p>・ 18653:複数のキーを持つWidevine MultiPeriodコンテンツの再生は、最初の期間で停止し、次の期間に切り替えることはできません。</p> <p>・ 18656:様々なキーで暗号化された、再生可能な複数期間のストリーム。再生は行われません。</p> <p>Dash用のPlayready 2.0は認証されていません。</p> <p> </p> <p> </p> </td> 
   <td>12602:HLS Fairplay DRMメタデータが、SafariのHTML5プレーヤーによって繰り返し更新される</td> 
   <td><p>Bento4でパッケージ化されたDASH Widevine DRMコンテンツを再生できます。 Offline PackagerとShaka Packagerでパッケージ化されたコンテンツは再生されません。 DASH PlayReady DRMはサポートされていません。</p> </td> 
  </tr> 
 </tbody> 
</table>

**表19:コア広告挿入機能(CSAI)**

<table> 
 <tbody> 
  <tr> 
   <td><strong>コンテンツタイプ</strong></td> 
   <td><strong>機能</strong></td> 
   <td><strong>Flash</strong></td> 
   <td><strong>Firefox、IE、Chrome、Android ChromeのHTML5</strong></td> 
   <td><strong>HTML5 in Safari、iOS Safari</strong></td> 
   <td><strong>Chromecast（DASH再生のみ）</strong></td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>前/中/後</td> 
   <td> </td> 
   <td><p>・ HLSライブコンテンツを含むプリロール広告は、デュアルプレーヤーモードで再生されます。</p> <p>・ HLSコンテンツを含むDASH広告とDASHコンテンツを含むHLS広告はサポートされていません。</p> <p>・ 19002:MSE adBreakを含むHTML5プレーヤーの場合。 insertionTypeは、正しい挿入タイプ（クライアントの挿入やサーバーの挿入など）を表す正しい値を返しません。</p> <p>7794:デフォルトのコントロールバーがフルスクリーンモードで表示されるモバイルデバイス（iOS、Chrome 33以前またはネイティブブラウザー搭載のAndroid）では、広告を再生するときにシークバーボタンと早送りボタンを使用できます。</p> <p>・ 11048:広告からHLS Liveコンテンツへの切り替えは、メディアソースの拡張の場合はスムーズではありません。</p> <p>・ 16083:Android 4.4 Chrome v52では、HLSコンテンツを含むHLS広告が、再生を停止した後にパイプラインのデコードエラーを引き起こす場合があります。</p> <p>・ 16097:広告の時間中に発生したエラーは処理されません。メインストリームの再生が停止する可能性があります。</p> <p>・ 18095:MP4広告は、HLSライブコンテンツではサポートされていません。</p> <p>19120:HLSコンテンツを含むHLS広告で複数のシークを行うと、ストリームの再生が停止する場合があります。</p> <p>・ 19131:プリロール広告の時間からコンテンツに切り替える際に、バッファリングオーバーレイが表示される場合があります。</p> <p>・ 20296:HLSライブストリームの場合、DVRウィンドウでシークバックし、解決されたミッドロールをシークオーバーすると、再生が停止する場合があります。</p> <p>・ 20298：ミッドロールが最初のミッドロールで停止し、DVRウィンドウから移動するミッドロールのHLSライブストリーム。</p> <p>・ 20317:広告の時間に複数の広告が含まれている場合、次の広告または広告からコンテンツに切り替えると、HLSライブストリームが停止することがあります。</p> 
    <ul> 
     <li>HLSライブストリームのDVRウィンドウ内の広告は解決されません。</li> 
    </ul> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>VAST 2.0/3.0</td> 
   <td> </td> 
   <td>SDKは、VAST adSourceのVMAP応答内のシーケンス属性を順守しません。</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>VAST 2.0/3.0</td> 
   <td> </td> 
   <td>20779:SDKは、VAST adSourceのVMAP応答内のシーケンス属性を受け入れません。</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>VMAP 1.0</td> 
   <td> </td> 
   <td>12014:VMAPの繰り返し属性はサポートされていません。</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>クリエイティブの再パッケージ化</td> 
   <td> </td> 
   <td>21464:広告の時間内の広告の1つに対してクリエイティブの再パッケージ化が失敗した場合、広告の応答は完全に破棄されます。</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

**表20:高度な広告挿入機能(CSAI)**

<table> 
 <tbody> 
  <tr> 
   <td><strong>コンテンツタイプ</strong></td> 
   <td><strong>機能</strong></td> 
   <td><strong>Flash</strong></td> 
   <td><strong>Firefox、IE、Chrome、Android ChromeのHTML5</strong></td> 
   <td><strong>HTML5 in Safari、iOS Safari</strong></td> 
   <td><strong>Chromecast（DASH再生のみ）</strong></td> 
  </tr> 
  <tr> 
   <td>VOD</td> 
   <td>広告のみ</td> 
   <td> </td> 
   <td>20056:広告のみの再生の場合は空のメインコンテンツに基づくので、プレーヤーの技術プロパティは関連しません。</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>カスタム広告ポリシー</td> 
   <td> </td> 
   <td><p>・広告動作は、MP4広告とMP4コンテンツではサポートされません。</p> <p>・ 13973:カスタム広告動作 — MSEで使用した場合、SKIPポリシーは完了イベントをスローしません。</p> <p>・ 14939:カスタム広告動作ポリシーのスキップおよびスキップ広告の時間がDASHコンテンツに対して機能しない。</p> <p>・ 17131:広告の最初のフレームが表示され、SKIP広告の時間ポリシーの場合はコンテンツが再開されます。</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>コンパニオン広告/バナー広告/クリック可能広告</td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td>リファレンスプレーヤーを使用する場合、バナー広告は表示されません。</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>VPAID 2.0</td> 
   <td> </td> 
   <td><p>・広告動作は、VPAID広告に対してはサポートされていません。</p> <p>・ 15032:広告の時間内にMP4またはHLS広告と組み合わせたVPAID広告はサポートされていません。</p> <p>・ 19001:AndroidおよびiOSで、VPAID広告がメインコンテンツの2重オーディオトラックとして再生される場合、メインコンテンツの1つと広告の1つが聞こえます。</p> <p>・ 20762:VPAID広告は、ピクチャインピクチャ(PIP)ではサポートされません。</p> <p>・ 21172:VPAID広告を含むHLS VODコンテンツに対して、再生完了イベントを受信しない。</p> <p>・ 21173:HLS VODコンテンツおよびポストロールVPAID広告に対してonAdBreakCompleteEventが受信されない。</p> </td> 
   <td>プレイヤーは、VPAID広告とメインコンテンツを切り替えながら、通常モードとフルスクリーンモードを切り替えます。</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

**表21:統合**

| **コンテンツタイプ** | **機能** | **Flash** | **Firefox、IE、Chrome、Android ChromeのHTML5** | **HTML5 in Safari、iOS Safari** | **Chromecast（DASH再生のみ）** |
|---|---|---|---|---|---|
| VOD + Live | Adobe Analytics VHLの統合 |  | 19004:ビデオ分析の追跡は、UIコンフィギュレータツールを通じては使用できません。 |  |  |

## 役立つリソース {#helpful-resources}

* 完全なヘルプドキュメントは、 [Adobe Primetimeのラーニングとサポートページで参照してください](https://helpx.adobe.com/support/primetime.html) 。