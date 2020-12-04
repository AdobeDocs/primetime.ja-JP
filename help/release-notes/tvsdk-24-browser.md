---
title: Browser TVSDK 2.4リリースノート
seo-title: Browser TVSDK 2.4リリースノート
description: Browser TVSDK 2.4リリースノートでは、Browser TVSDK 2.4の新しい、サポートされている機能およびサポートされていない機能と既知の問題について説明します。
seo-description: Browser TVSDK 2.4リリースノートでは、Browser TVSDK 2.4の新しい、サポートされている機能およびサポートされていない機能と既知の問題について説明します。
uuid: 3a1eb1a5-0e72-4658-beeb-bca8816570e7
contentOwner: dekalra
topic-tags: release-notes
products: SG_PRIMETIME
discoiquuid: d71886cb-f34b-47b2-9df7-168686478106
translation-type: tm+mt
source-git-commit: e644e8497e118e2d03e72bef727c4ce1455d68d6
workflow-type: tm+mt
source-wordcount: '6834'
ht-degree: 0%

---


# ブラウザーTVSDK 2.4リリースノート{#browser-tvsdk-release-notes}

Browser TVSDK 2.4リリースノートでは、Browser TVSDK 2.4の新しい、サポートされている機能およびサポートされていない機能と既知の問題について説明します。

## はじめに{#introduction}

ブラウザーTVSDKは、高度なビデオ再生機能、コンテンツ保護、広告をブラウザーベースのビデオプレーヤーアプリケーションに追加できるツールキットです。

Browser TVSDK 2.4は、ブラウザーベースのビデオアプリケーションを構築するためのJavaScript APIを提供し、次のモードでの再生のサポートを含みます。

* HTML5のみ
* 自動フラッシュフォールバックを伴うHTML5
* Flashが常に

このリリースには、次の情報が含まれています。

・ [ブラウザーTVSDK APIドキュメント](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html)。

・ [ブラウザーTVSDKプログラミングガイド](https://helpx.adobe.com/content/dam/help/en/primetime/programming-guides/psdk_browser-tvsdk.pdf)

・ [1.4 DHLS用のTVSDK for 1.4からブラウザーTVSDK 2.4への移行ガイド](https://helpx.adobe.com/primetime/migration-guides/tvsdk-14-dhls-browser-tvsdk-24.html)

・ [ブラウザーTVSDK 2.4.6からバージョン2.4.7](https://helpx.adobe.com/primetime/conversion-guides/browser-tvsdk-246-to-247-for-javascript.html)に変換しています。

・ビルドに含まれる参照実装。

>[!NOTE]
>
>*このリリースのセキュリティに関する考慮事項のリストについては、セキュリティに関する考慮事項を参照してください。

## 新機能とサポートされる機能{#what-s-new-and-supported-features}

このリリースのBrowser TVSDKは、ビデオアプリケーションを強化するために使用できる新機能を提供します。

**2.4.12アップデートの新機能（ビルド204）**

以下の追加機能は、Browser TVSDK 2.4.12 Update(Build 204)の一部として利用できます。

* 再生がミュートされているときにiOSで自動再生が可能になるように、AdobePSDK.MediaPlayerのボリュームAPIの実装が変更されました。

・新しいAPI `auditudeSettings.ignoreVPAIDAds`が追加され、Auditudeサーバーから受信したVPAID広告を無視できるようになりました。 このAPIはFlashのフォールバックでは動作しません。

**バージョン2.4.11**

Browser TVSDK 2.4.11リリースの一部として、次の機能強化および追加が行われました。

・ HLSライブセグメントフェイルオーバーは、MSEとFlashのフォールバックモードでサポートされています。

・ `AuditudeSettings.creativeRepackagingDomain` APIもMSEでサポートされるようになりました。 以前は、Flashのフォールバックモードでのみサポートされていました。

・このリリースには、お客様の重要な問題に対する修正が含まれています。 *リストを修正した問題*&#x200B;を参照してください。

**バージョン2.4.10**

Browser TVSDK 2.4.10リリースの一部として、次の機能強化および追加が行われました。

・ TVSDKは、ログを有効または無効にするenableLogging()を提供します。 使用方法については、[APIドキュメント](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html)を参照してください。

・ TVSDKは、Adobe Analyticsを使用している場合、デフォルトチャプターをサポートしなくなりました。 アプリケーションを使用して、チャプターを定義および管理します。

・このリリースには、お客様の重要な問題に対する修正が含まれています。 「*修正された問題*aリスト」を参照してください。

**バージョン2.4.9**

Browser TVSDK 2.4.9リリースの一部として、次の機能強化および追加が行われました。

・時間の不連続性があるが、不連続マーカーがないHLS VODおよびLiveストリームがサポートされています。

・ ID3 v2.4.0フレームは、HLS VODおよびライブストリーム用のSafariビデオタグでサポートされています。

・セキュア広告読み込みの実装は、API設定に基づいてセキュアなHTTPにアップグレードされる広告サーバー呼び出しを保証します。 詳しくは、AdobePSDK.AdvertisingMetadataおよびAdobePSDK.ForceHttpsAdConfigurationクラスを参照してください。 この機能は、Flashのフォールバックモードではサポートされていません。

・ VAST 3.0応答に関連付けられた広告ID情報と拡張情報は、TVSDKがアプリケーションで使用できるようになり、広告の測定にMort統合を実装する際に使用できます。 詳しくは、AdobePSDK.NetworkAdInfo APIを参照してください。 これは、Flashのフォールバックモードではサポートされていません。

・ AdobePSDK.ForceHttpsConfigurationクラスは使用できなくなりました。 それは次の方法で成功する

AdobePSDK.ForceHttpsAdConfigurationクラス。

・新しいAPI、AdobePSDK.optimizeFlashCallsを使用して、呼び出しを最適化し、FlashのフォールバックモードでのHLS再生エクスペリエンスを改善できるようになりました。 これはデフォルトで無効です。

**2.4.8アップデートの新機能（ビルド6002）**

このアップデートには、お客様の重要な問題に対する修正が含まれています。 リストについては、*修正された問題*&#x200B;を参照してください。

**バージョン2.4.9**

Browser TVSDK 2.4.8リリースの一部として、次の機能強化および追加が行われました。

・ SDKはChrome EMEに準拠するようになり、Chrome v58以降のベストプラクティスに関する変更が加えられました。 詳しくは、[https://storage.googleapis.com/wvdocs/Chrome_EME_Changes_and_Best_Practices.pdf](https://storage.googleapis.com/wvdocs/Chrome_EME_Changes_and_Best_Practices.pdf)**を参照してください。

・ UIフレームワークで、Flash、広告のみ、ターゲット情報のワークフローでHLS Access DRMがサポートされるようになりました。

・ setDRMAuthenticateData APIがUIフレームワークに追加されます。 AdobeアクセスDRMで保護されたストリームを再生するには、このAPIを呼び出します。 または、drmAuthenticateData属性をプレイヤーで指定できます。 詳しくは、[AdobePSDK.videoBehavior ](https://help.adobe.com/en_US/primetime/api/psdk/btvsdk-ui-framework/VideoBehavior.html)を参照してください。

**バージョン2.4.7**

バージョン2.4.7の新機能：

・ UIフレームワークにUIコンフィギュレータを追加

プレイヤーは、次のいずれかの方法で設定できます。

・ JSONオブジェクトの使用

・ APIの使用

JSONオブジェクトの生成に役立つように、Browser TVSDKは、**UI Configurator **toolを提供します。

このツールでは、様々な設定を選択できます。「**テスト設定**」をクリックして設定を確認し、「**設定をダウンロード**」をクリックして設定をダウンロードします。 ファイルをダウンロードした後、このファイルのコンテンツをJSONオブジェクトとしてptp.videoPlayer APIに渡すことができます。

・ MediaPlayerItemConfig APIをUIフレームワークに追加

advertisingMetadata、advertisingFactory、adSignalingMode、networkConfiguration、customRangeMetadata、useHardwareDecoder、subscribeTags、adTags、thumbnailScrubber、billingMetricsConfigurationなど、様々な機能をMediaPlayerPlayItemConfigを使用して設定できます。 詳しくは、[ブラウザーTVSDK API](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html)* * [ドキュメント](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html)のAdobePSDK.MediaPlayerItemConfigドキュメントを参照してください。

UIフレームワークでは、ネットワーク設定をプレイヤー構成に渡す方法が変更されました。

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

* `AdobePSDK.embedSWFinFullScreenDiv` APIの追加

この新しいAPIは、プレーヤーアプリケーションがFlashFallback.swfファイルを埋め込むことのできるdivを選択する柔軟性を提供します。

* TVSDKバージョン関連情報の`getVersion`APIを`AdobePSDK.MediaPlayer`クラスから`AdobePSDK.Version`クラスに置き換えました。 詳しくは、`AdobePSDK.Version` API [ここ](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/AdobePSDK.Version.html)を参照してください。

**バージョン2.4.6**

バージョン2.4.6の新機能は次のとおりです。

* **Browserifyのサポート**

Browserifyを使用すると、ブラウザーでnode.jsスタイルモジュールを使用できます。 依存関係を定義し、すべてを1つのJavaScriptファイルにバンドルできます。

* **請求**

課金の支援を受けて、ブラウザーTVSDKは、Primetimeのお客様に課金するためのプレイヤー使用状況指標を収集できます。

>[!NOTE]
>
>Enum PSDKErrorCodeの非推奨の列挙MediaPlayer.イベントおよび非推奨の定数は、バージョン2.4.6で削除されました。詳しくは、[ブラウザーTVSDK 2.4.5からバージョン2.4.6](https://helpx.adobe.com/primetime/conversion-guides/browser-tvsdk-245-to-246-for-javascript.html)への変換を参照してください。

**バージョン2.4.5**

バージョン2.4.5の新機能：

* **フルイベントの再生と広告**

   HLS完全なイベント再生(FER)ストリームで、広告の解決と広告の動作がサポートされるようになりました。 このサポートを有効にするには、`MediaPlayerItemConfig`オブジェクトの作成時に広告シグナリングモードを`MANIFEST_CUES`に設定します。

* **MediaplayerView ScalePolicyのサポート**

   アプリケーション開発者は、MediaplayerView scalePolicyプロパティを使用して、表示に対して異なるscalePolicyを指定できるようになりました。

* **アナモルフィックコンテンツのサポート**

   MSEおよびFlash再生を使用する場合に、アナモルフィックコンテンツの再生がサポートされるようになりました。

* **選択的適用`withCredentials`**

`withCredentials`をtrueに設定した場合、`Access-Control-Allow-Origin`ヘッダーをワイルドカードに設定することはできません。 サーバーの応答に応じて、ブラウザーTVSDKは選択的に`withCredentials`属性を設定します。 このサポートについて詳しくは、[ブラウザーTVSDK APIドキュメント](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html)を参照してください。

**バージョン2.4.4**

バージョン2.4.4で追加された新機能：

* **Chromecastサンプルアプリケーション**

このリリースでは、DASH VODストリームおよびDASH Widevineストリームの再生とクライアント側の広告挿入を示す、送信者アプリケーションと受信者アプリケーションのサポートが提供されます。

* **高度なフェイルオーバーのサポート**

このリリースでは、HLS VODストリームの高度なフェイルオーバーの使用例（セグメントおよびサーバーのフェイルオーバー）がサポートされています。

**バージョン2.4.3**

バージョン2.4.3で追加された新機能：

* **DASH VODのカスタムタグ**

   インラインカスタムタグ(イベント)は、TimedMetadataオブジェクトとしてサブスクライブし、受け取ることができます。

* **拡張子のないストリームの再生**

   拡張子のないHLSストリームとDASHストリームがサポートされるようになりました。 マニフェストファイルの場合、リソースの読み込み時にresourceTypeを指定する必要があります。 セグメントおよびVTTファイルの場合、Content-Type応答ヘッダーを使用してコンテンツタイプが決定されます。

**バージョン2.4.2**

バージョン2.4.2で追加された新機能：

* **APIパリティ**

APIパリティの完全なリストについては、[TVSDK for 1.4 DHLS to Browser TVSDK 2.4 Migration Guide](https://helpx.adobe.com/primetime/migration-guides/tvsdk-14-dhls-browser-tvsdk-24.html)を参照してください。

* **サンプル — AESのサポート**

   このリリースでは、MSEでのSample-AES暗号化コンテンツ再生とFlashのフォールバックのサポートが追加されます。 Google Chromeで安全な接触チャネルでAESコンテンツをホストする必要はなくなりました。

* **AACコンテナのサポート**

   .aac拡張子が付いたファイルの再生がサポートされるようになりました。 オーディオ専用ストリームまたは代替オーディオを使用できます。

   >[!NOTE]
   >
   >AC3および拡張AC3コーデックは、まだサポートされていません。

* **トークン化されたストリーム再生**

コンテンツ配信ネットワーク(CDN)経由で配信されるHLSストリームは、マニフェストおよびセグメントリクエストで認証トークンを使用して検証できる場合があります。また、これらのトークンはURLパラメーターまたはcookieヘッダーとして提供できます。 このようなストリームの再生がサポートされるようになりました。

**バージョン2.4.1**

バージョン2.4.1では、次の機能が新たに追加されました。

* **UIフレームワーク**

このフレームワークは、再生/一時停止やボリュームなどの基本的なコントロールを含め、スクラブバーの状態やクローズドキャプションの設定などの要素を簡単に追加または削除するためのAPIで構成され、JavaScriptベースのビデオプレーヤーアプリケーションのUI開発を高速化します。 コントロールに関連付けられた動作を指定したり、カスタムコントロールを作成したり、プレイヤーUIにスキンを適用したりできます。 これはすべてフレームワークを通じて行われ、DOM構造を直接操作する必要はありません。

* **ライブストリームのHLS再生の強化**

このリリースでは、広告挿入による不連続性をサポートしています。 スムーズな再生を実現するために、EXT-プログラム-DATE-TIMEタグの後にEXT-MEDIA-SEQUENCEタグを使用して、アダプティブビットレートプロファイル間で同期します。

* **VPAID 2.0のサポート**

ビデオプレーヤー広告配信インターフェイス定義(VPAID)バージョン2.0は、ユーザーにリッチメディアの操作性を提供し、発行者は、ターゲット広告の改善、広告インプレッションの追跡、ビデオコンテンツの収益化を実現します。 このリリースでは、ビデオオンデマンド(VOD)コンテンツ用のリニアJavaScript VPAID広告がサポートされています。

* **カスタムHLSタグ**

メディアストリームは、プレイリスト/マニフェストファイル内のタグの形式で追加のメタデータを伝達できます。 ブラウザーTVSDKを使用すると、追加のタグを指定およびサブスクライブして、それらのタグがマニフェストに出現したら通知を受けることができます。

* **プレイヤータイムラインに表示される広告マーカー**

このリリースでは、VODコンテンツとLiveコンテンツの両方のプレーヤータイムラインでの広告マーカーの表示がサポートされています。 この動作は、参照プレーヤーで確認できます。

**2.4でサポート**

バージョン2.4では、次の機能が使用できます。

* **MP3オーディオ再生**

   このリリースでは、Media Source Extensions(MSE)が設定されたブラウザーとSafariビデオタグでのMP3オーディオ再生がサポートされています。

* **MP4ビデオ再生**

   次の機能がサポートされています。

   * 単一ストリーム再生
   * 広告動作とトラッキングを含むプリロールおよびポストロールMP4広告
   * 広告動作と追跡を含むプリロールおよびポストロールHLS広告
   * 広告動作と追跡を含むプリロールおよびポストロールDASH広告

## サポートされるプラットフォーム{#supported-platforms}

ブラウザーTVSDKには、実行する必要があるプラットフォームとソフトウェアのレベルに固有の要件があります。 次のプラットフォームとソフトウェアレベルがサポートされています。

### デスクトップ構成{#desktop-configurations}

* Microsoft Windows 7:

   * Internet Explorer 11+
   * Chrome 33+
   * Firefox 38+

* Microsoft Windows 8.1

   * Internet Explorer 11+
   * Chrome 33+
   * Firefox 38+

* Microsoft Windows 10

   * Edge+

* Apple OS X

   * Safari 9+
   * Chrome 33+
   * Firefox 38+

### モバイルWeb設定{#mobile-web-configurations}

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

## 機能マトリックス{#feature-matrix}

このリリースでサポートされる機能とサポートされない機能のリストを次に示します。

* *MP3オーディオ機能 — コア再生*
* *MP4ビデオ機能 — コア再生*
* *MP4ビデオ機能 — コアAd Insertion*

>[!NOTE]
>
>*以下の機能マトリックスの表で「Y」は、この機能が現在のリリースでサポートされていることを意味します。*

### MP3オーディオ機能{#mp-audio-features}

**表1:コア再生{#table-core-playback}**

| カテゴリ | コンテンツタイプ | 機能 | Flash | HTML5:FF、IE、Chrome、Android Chrome | HTML5:Safari、iOS Safari |
|--- |--- |--- |--- |--- |--- |
| 再生 | MP3 VOD | 一般再生（再生、一時停止、シーク） | 非対応 | Y | Y |

1ブラウザーTVSDKのビデオタグは、ストリーミングとDRMをサポートしていません。 コーデックとコンテナのサポートは、すべてのブラウザで同じではありません。

2 Firefoxのデフォルトでは、バージョン41以前のFlash Playerが使用されます。

### MP4オーディオ機能{#mp-audio-features-1}

**表2:コア再生**

| カテゴリ | コンテンツタイプ | 機能 | Flash | HTML5:FF、IE、Chrome、Android Chrome | HTML5:Safari、iOS Safari |
|--- |--- |--- |--- |--- |--- |
| 再生 | MP4 VOD | 一般再生（再生、一時停止、シーク） | 非対応 | Y | Y |

**表3:コアAd Insertion**

| カテゴリ | コンテンツタイプ | 機能 | Flash | HTML5:FF、IE、Chrome、Android Chrome | HTML5:Safari、iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Ad Insertion | MP4 VOD | プリロール(MP4) | 非対応 | Y | Y |
| Ad Insertion | MP4 VOD | ポストロール(MP4) | 非対応 | Y | Y |

HLSまたはDASH機能のサポートについて詳しくは、以下を参照してください。

## HLS機能マトリクス{#hls-feature-matrix}

Browser TVSDKのHLS機能に関する機能一覧を示します。

* *HLSコア再生*
* *HLS高度な再生機能*
* *HLSコンテンツ保護機能*
* *HLSコア広告挿入機能*
* *HLSの高度な広告挿入機能*
* *HLS統合*

>[!NOTE]
>
>*以下の機能マトリックスの表で「Y」は、この機能が現在のリリースでサポートされていることを意味します。*

### HLS機能{#hls-features}

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
   <td><p>一般的な再生（再生、一時停止、シーク）</p> </td> 
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
   <td><p>QoSおよびプレイヤー通知</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>限定的なQoSサポート</p> </td> 
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
   <td><p>バッファー制御パラメーターの設定</p> </td> 
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
   <td>遅延バインディングオーディオ</td> 
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
   <td><p>トークン化されたストリーム</p> </td> 
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
   <td><p>Adobeアクセス</p> </td> 
   <td><p>非対応</p> </td> 
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
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>プリロール(MP4/HLS)</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>ミッドロール(HLS)</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>プラットフォームの制限</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>ポストロール(MP4/HLS)</p> </td> 
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
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>広告のみ</p> </td> 
   <td><p>非対応</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>ターゲット設定パラメーター</p> </td> 
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
   <td><p>非対応</p> </td> 
   <td><p>プラットフォームの制限</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>コンパニオン広告，バナー広告，クリック可能な広告</p> </td> 
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
   <td><p>Adobe AnalyticsVHL統合</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
 </tbody> 
</table>

## DASH機能マトリックス{#dash-feature-matrix}

ブラウザーTVSDKのDASH機能の機能一覧を示します。

・ *DASHコア再生機能*

・ *DASH高度な再生機能*

・ *DASHコンテンツ保護機能*

・ *DASHコア広告挿入機能*

・ *DASH高度な広告挿入機能*

・ *DASH統合*

>[!NOTE]
>
>以下の機能マトリックスの表で、Yは、この機能が現在のリリースでサポートされていることを意味します。

### DASH機能{#dash-features}

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
   <td><p>一般的な再生（再生、一時停止、シーク）</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>再生</p> </td> 
   <td><p>FER VOD</p> </td> 
   <td><p>一般再生（再生、一時停止、シーク）</p> </td> 
   <td><p>非対応</p> </td> 
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
   <td><p>QoSおよびプレイヤー通知</p> </td> 
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
   <td><p>バッファー制御パラメーターの設定</p> </td> 
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
   <td><p>非対応</p> </td> 
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
   <td><p>トークン化されたストリーム</p> </td> 
   <td><p>非対応</p> </td> 
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
   <td><p>非対応</p> </td> 
  </tr> 
  <tr> 
   <td><p>コンテンツ保護</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Sample-AES</p> </td> 
   <td><p>非対応</p> </td> 
  </tr> 
  <tr> 
   <td><p>コンテンツ保護</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>DRM</p> </td> 
   <td><p>・ Chrome、Firefox 47以降、およびChromecast上のWidevine</p> <p>・ Windows 8.1およびEdge上のInternet ExplorerでのPlayReady</p> <p>・ Windows Firefox用のPrimetime DRM（ビデオのみ）</p> </td> 
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
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>プリロール(MP4/DASH)</p> </td> 
   <td><p>VODのみ</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>ミッドロール(DASH)</p> </td> 
   <td><p>VODのみ</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>ポストロール(MP4/DASH)</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>FER VOD</p> </td> 
   <td><p>広告の解像度と動作</p> </td> 
   <td><p>非対応</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>デフォルトの広告ポリシー</p> </td> 
   <td><p>VODのみ</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>VAST 2.0/3.0</p> </td> 
   <td><p>VODのみ</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>VMAP 1.0</p> </td> 
   <td><p>VODのみ</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>クリエイティブの再パッケージング（MP4からDASH）</p> </td> 
   <td><p>非対応</p> </td> 
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
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>広告のみ</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>ターゲット設定パラメーター</p> </td> 
   <td><p>VODのみ</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>カスタムパラメーター</p> </td> 
   <td><p>VODのみ</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>カスタム広告ポリシー</p> </td> 
   <td><p>非対応</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>遅延広告読み込み</p> </td> 
   <td><p>非対応</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>コンパニオン広告，バナー広告，クリック可能な広告</p> </td> 
   <td><p>非対応</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>VPAID 2.0</p> </td> 
   <td><p>非対応</p> </td> 
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
   <td><p>Adobe AnalyticsVHL統合</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
 </tbody> 
</table>

## 修正された問題{#issues-fixed}

**2.4.12アップデート（ビルド204）で修正された問題**

ブラウザーTVSDKバージョン2.4.12の更新（ビルド204）で、次の問題が修正されました。

・ **21647**- TVSDKは、オーディオがミュートになっている場合、iOSデバイスでのビデオの自動再生を許可する必要があります。

・ **21465**- DRM保護されたDASHストリームをDASHライブストリームの再生後に再生すると、エラーキーシステムアクセス拒否が受信されました。

・ **21442** — ユーザーのジェスチャーでプリロール広告を再生した後、iOS Webでコンテンツの自動再生を有効にします。

・ **21240**- Auditude/VMAPから解析したVPAID広告をフィルターするAPIを提供。

**バージョン2.4.11で修正された問題**

Browser TVSDKバージョン2.4.11では、次の問題が修正されました。

**コア再生機能：**

・ **19192**:TVSDKは、TextFormat:bottomInsetとTextFormat:safeAreaを実装するようになりました。 これらの機能強化により、コントロールバーが画面に表示されている場合は、クローズドキャプションの位置を変更できます。

・ **21009**:クローズドキャプションは、新しいキャプションが表示されるまで、不連続部分を越えてシークする場合に、画面上に残ります。

・ **21141**:セグメントの追加中に競合条件が発生したため、シークバックが拒否されました。

・ **21142**:プレイヤーがINITIALIZED状態の場合に、シーク可能な再生範囲を利用できるようにする。 これらの変更により、位置での開始セッションがサポートされるようになりました。

・ **21363**:DASHストリームに広告を挿入した後、608/708クローズドキャプションが同期されなくなる。

**広告挿入機能：**

・ **21179**:ad.primaryAsset.adParametersプロパティを正しく設定することで、VODコンテンツを含むミッドロール関連の問題（長い一時停止、黒いフレーム）が解決されるようになりました。

・ **21257**:MP4が有効なMIMEタイプではなく、クリエイティブの再パッケージ化機能が有効な場合は、ビットレートが最も高いMP4ファイルがトランスコード用に選択されます。

・ **21361**:追加の正規化ルールをサポートするため、TVSDKは、クリエイティブパッケージングリクエストのクエリパラメーターとして、広告システムとクリエイティブIDをVAST応答から渡すようになりました。

**バージョン2.4.10で修正された問題**

Browser TVSDKバージョン2.4.10では、次の問題が修正されました。

**コア再生機能：**

・ **21060**:不連続を含むHLSストリームと、ISO BMFFボックスがストリームの終わりに対して実行されるHLSストリームで、無効なコーデックエラーが発生しました。

・ **21045**:プレイリストの最初のビデオ再生が完了した後、iOSで自動再生が機能しない。

・ **20975**:フレームレートは、ChromeブラウザーのQoSプロバイダーからNaNとして返されます。

・ **20823**:データのないセグメントが発生した場合にサポートされていないコーデックエラーが発生しました。

・ **20769**:SDKは、ABRポリシーに基づいて即座に切り替える代わりに、シーク時に現在のビットレートで開始するようになりました。

・ **20031**:IE11(Windows 8.1)で縦置きモードの場合、ビデオ画面は小さくなります。 コンテンツ保護機能：

・ **19316**:HLS AES-128ストリームの場合、復号化に失敗したセグメントをスキップします。

**バージョン2.4.9で修正された問題**

Browser TVSDKバージョン2.4.9では、次の問題が修正されました。

**コア再生機能：**

・ **13407**:Firefoxが再生中に「ontimeupdate」イベントの送信を停止すると、DASHストリームが停止する場合があります。

・ **16380**:MSEを介した開始時間が一致しないセグメントのMuxed Audio Video Content Playback中に、表現間のオーディオ同期エラーがABRスイッチに蓄積され、最終的にエラーが発生します（Chrom問題#663686）。

・ **17985**:Firefoxブラウザーで特定のISO-BMFFストリームを再生すると、再生が停止する（Firefoxの問題#1342913）。 これはFirefox v53以降で修正されました。

・ **19141**:Uncaught (in promise) ReferenceError:幅が定義されていません。

・ **18997, 19299**:セグメント境界でのビデオのちらつきの問題。 これは、SDKが最後のサンプルのコンポジションの時間オフセットを正しく計算していないために発生していました。

・ **19780**:Firefox v53でのHLSコンテンツとHLS Adの再生に関する開始が発生しない（Firefoxの問題#354653）。

・ **20046**:プログラム日時は、時間指定メタデータオブジェクトとして受け取った場合、値ではなくキーとして受け取られます。

・ **20047**:useDefaultResizeHandlerは、Flashのフォールバックでエラーをスローします。

・ **20179**:Flash Playerv25.0.0.171でFlashフォールバックが機能しない。

・ **20293**:Firefoxは、一部のHLSストリームが停止するとデータのバッファリングを停止します。

・ **20626**:プレイヤーが、時間がゼロのビデオサンプルの誤った処理により、Chromeでメディアデコードエラーをスローします。

・ **20078**:再生がブラウザーエラー「QuotaExceeded」で停止する。

・ **18639**:HLS Liveストリーム608 CCでは、テキストがスペルミスとして表示されることがあります。

・ **20028**:ClosedCaptionsのサイズパラメーターでは、フォントサイズは変更されません。

・ **20613**:クローズドキャプションのボックスは互いに重なり合うので、読みにくくなります。

**コアAd Insertion(CSAI)の機能：**

・ **20043**:複数の広告とサードパーティのリダイレクトを伴う広告インプレッション呼び出しと広告トラッキング呼び出しがない。

・ **20044**:クリエイティブの再パッケージングを使用する場合、広告の時間内のすべての広告を正常に再パッケージ化する必要があります。正常にパッケージ化されないと、広告の時間は完全に破棄されます。

・ **20097**:広告のマニフェストが使用できない場合、広告の再生がスキップされ、メインコンテンツが20秒のタイムアウトを待たずに即座に再開されます。

**バージョン2.4.8アップデートで修正された問題（ビルド6002）**

ブラウザーTVSDKバージョン2.4.8の更新（ビルド6002）で、次の問題が修正されました。

・ **14126:** MSEソースバッファーの内部的なギャップが原因で、Firefoxでの再生が停止する場合があります（問題#1316024）。 再生を再開するには、シークを試みます。

・ **19608:** Auditude VMAP応答からのタイムオフセット値に従うように修正しました。

・ **19635:** Windows 10上のInternet Explorer 11でのビデオの停止を修正しました。

・ **19761:** HLSのABRの問題を修正しました。

・ **19780:** Mozilla Firefox v53で破損していたHLSコンテンツでの広告再生を修正しました。

・ **19877および19744:**&#x200B;この問題により、シーク操作後のビットレート選択の矛盾が修正されました。 シーク時のビットレート選択は、現在のビットレートの低い値になり、開始アップ時のビットレートが低くなります。

・ **19881:**&#x200B;再生が停止し、シークが3 ～ 4回実行された後、無限に長い時間バッファリングオーバーレイが表示されます。

・ **19884:** Chrome 59 Beta Verified Media Path(VMP)要件への準拠を確認します。 bTVSDKは、Chrome 59ベータ版でWidevine DRMコンテンツを再生できました。

・ **19916:** UI-FrameworkでのDRM再生が壊れました。 現在は、メタデータにポリシーがない場合でも、acquireLicenseを呼び出します。

**バージョン2.4.8で修正された問題**

Browser TVSDK 2.4.8リリースでは、次の問題が修正されました。

・ **10075**:タイムラインを前にシークする際に、FirefoxとChromeで再生完了イベントが受信されず、Firefoxでシークイベントが受信されなかった問題を修正しました。

・ **15775**:Windows 8.1 Internet ExplorerでPlay Completeイベントが受信されない。

・ **17306**:SSAIストリームの場合、再生がサポートされます。 ステッチ広告のトラッキングはサポートされていません。

・ **19142**:時には、巻き戻しによってビデオプレーヤーが永久にバッファリング状態を維持する。

・ **19218**:広告マーカーは、UIフレームワークを通じては使用できません。

・ **19219**:広告のみの再生は、UIフレームワークを通じては機能しません。

・ **19222**:AES-128キーはプレイリストに対して1回要求され、以降の要求はキャッシュから供給されます。 以前は、各セグメントに対してリクエストが行われていました。

・ **19597**:&quot;Uncaught TypeError:Chrome Canaryビルドで「未定義のログ」プロパティを読み取れません。

・ **19605**:flashのフォールバックモードでは、adRequestDomainが使用できませんでした。

・ **19608**:HLSライブストリームにVMAP広告が挿入されませんでした。 SDKは、キューマーカーを考慮し、VMAP応答の時間オフセット値に依存しなくなりました。

・ **19637**:広告のみ再生すると、広告の最後にスクリプトエラーが発生します。

・ **19732**:CRSプレイリストの要求が404エラーで失敗していた問題を修正しました。 Browser TVSDKからの1401および1403のリクエストが更新され、この問題が解決されました。

・ **19762**:acquireLicenseは、setAuthenticationTokenの前に呼び出され、トークンの有効性に関係なく有効なライセンスが返されたために使用されていました。 この問題は現在修正され、acquireLicenseはsetAuthenticationToken応答の後でのみ呼び出されます。

**バージョン2.4.7で修正された問題**

バージョン2.4.7では、次の問題が修正されました。

・ **8397**:セグメントがキーフレームと開始しない場合、Adobeメディアサーバーを通じて生成されたHLSライブストリームが再生されないことがあります。

・ **13606**:ChromeブラウザーでのHLSストリームに関する複数のSeek関連の問題が修正されました。

・ **14807**:Chromeブラウザーで、play()の直後にシークまたは一時停止がトリガーされると、再生が次のエラーで停止する場合があります。DOMException:play()要求は呼び出しによって中断されました…（Chromの問題# 593273）

・ **19085**:volume、abrControlParameters、ccStyleなどのMediaPlayerパラメーターは、プレイヤーのリセット時にデフォルトに設定されません。

**バージョン2.4.6で修正された問題**

バージョン2.4.6では、次の問題が修正されました。

・ **18093**:Flash Playerバージョン24をFlashフォールバックモードで使用すると、サブスクライブされたタグの横のタグのTimedMetadataが返されます。

**バージョン2.4.4で修正された問題**

バージョン2.4.4では、次の問題が修正されました。

・ **8711**:MSEの場合、608/708のキャプションはデフォルトで左揃えになります。

・ **13934**:広告のABR設定は、HLSライブストリームを再生する場合には適用されません。

・ **14079**:DVR時間の短いHLSライブストリームの長さは、ネットワークの遅延の問題が原因で再生が遅れる可能性があるので、失敗する場合があります。 再生を再開するには、ライブポイントをクリックします。

・ **15037**:プレイヤーUIフレームワークに付属のサンプルは、Windows 7上のMicrosoft Internet Explorer 10では動作しません。

・ **15913**:HLS VODストリームの場合、Chromeでは、マニフェストの応答が304未変更の場合、ストリームは再生されません。 これは、Chrome v55（Chromiumの問題633696）以降に修正されました。

・ **16103**:Android Chromeでは、低帯域幅の条件では、Uncaught TypeErrorが発生して再生が停止する場合があります。未定義のエラーのプロパティ&#39;programDateTime&#39;を読み取れません。

・ **16265**:HLS VODおよびライブストリームの場合、不連続間のシークは機能しません。

・ **16709**:PDTと不連続マーカーを使用してHLS Liveストリームを再開すると、プレイヤーがバッファリングで動かなくなる可能性があります。

## 既知の問題と制限{#known-issues-and-limitations}

ブラウザーTVSDKの制限事項と既知の問題を以下に示します。

**表16:コア再生機能**

<table> 
 <tbody> 
  <tr> 
   <td><strong>コンテンツタイプ</strong></td> 
   <td><strong>機能</strong></td> 
   <td><strong>Flash</strong></td> 
   <td><strong>Firefox、IE、Chrome、Android ChromeのHTML5</strong></td> 
   <td><strong>SafariのHTML5、iOS Safari</strong></td> 
   <td><strong>Chromecast（DASH再生のみ）</strong></td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>一般再生（再生、一時停止、シーク）</td> 
   <td><p>・ HLS以外のメディア形式はサポートされていません。</p> <p>8799:Flashのフォールバックでは混合コンテンツは扱われないので、コンテンツ、広告および他のURLが混在コンテンツ（安全なコンテンツと安全でないコンテンツを一緒に）に結び付けないようにする必要があります。</p> <p>・ 19271:UIフレームワークを介したマルチビュー再生は、Flashのフォールバックモードではサポートされていません。</p> <p>・ Windows 7上のMicrosoft Internet Explorer 8および9では、これらのバージョンはSDKでサポートされていないので、Flashのフォールバックは機能しません。</p> <p>・ 20262:Flashのフォールバックにより、ターゲティング情報リストにカスタムパラメータが追加されます。 また、FlashとMSEの場合、カスタムパラメータの優先順位も異なります。</p> <p>・ 20653：ブラウザーTVSDKのFlashフォールバックは、Creators Updateを使用するWin10では動作しません。</p> <p>・Flashフォールバックは、Flash Playerバージョン23以降で機能します。</p> <p>・ 20087 - Chrome 59ベータ版（日本未発売）</p> <p>Flash25.0.0.171</p> <p>ベータ版（デフォルト）では、HLS再生がFlashのフォールバックモードで動作しません。 カナリアではうまくいっています。</p> </td> 
   <td><p>・ 12563:オーディオコーデックmp4a.40.02を含むダッシュストリームは、MPDのオーディオコーデック文字列がサポートされていないため、Firefoxで再生されません。 オーディオコーデックmp4a.40.2がサポートされます。</p> <p>15029:UIフレームワークのmultiViewでビデオを切り替える場合、再生/一時停止ボタンは、それに応じて更新されません。</p> <p>・ 16034:Windows 8.1 IEでは、reset()を呼び出すと、不明なMIMEタイプエラーが発生します。 再生を再開するには、メディアを再読み込みしてください。</p> <p>・ 18235:広告を含むDASH VODストリームでは、シークの問題が発生する場合があります。</p> <p>・ 18727:エラーAPIはMSEではサポートされていません</p> <p>18750:SDKとUIの両方のフレームワークおよびUIフレームワークで、リソースの読み込み後に追加されたイベントリスナーのIDLE操作とInitializing StatusChangeイベントが欠けている場合があります。</p> <p>・ 18889:MediaPlayerがERROR状態の場合、表示オブジェクトは返されません。</p> <p>・ 19039:AdobePSDKの場合。 MediaPlayer. seekToLocal()はEOFより大きい値で使用され、MSEの場合は最初から再生開始が使用されます。</p> <p>・ 19049:再生中にビデオがブロックされた場合、Chrome、IE、FirefoxのFlash Playerでエラー状態が報告されません。</p> <p>・ 17205:オーディオの再生が続行する間、ビデオ再生が数時間、ミュクスされていないストリームの再生で停止する（Chromiumの問題# 664033）。</p> <p>・ 12308:composition_time_offsetが指定されたDASHストリームに、timeStampOffsetがChromeブラウザーで適用されている場合があり、その結果、負のデコード時間が発生するので、MEDIA_ERR_ SRC_NOT_ SUPPORTEDエラーが発生する（Chrom問題#398141）。</p> <p>・ 14126:MSEソースバッファーの内部的なギャップが原因で、Firefoxでの再生が停止する場合がある（問題番号1316024）。 再生を再開するには、シークを試みます。</p> <p>・ 19115:MS EdgeおよびIE 11（Win 8.1および10）では、CORSリダイレクトで接触チャネルがnullに設定されず、ヘッダーがnullでないため再生エラーが発生するのに失敗します。</p> <p>・ 19861：既に再生されたメディアのソースバッファに追加動作が発生する問題 Chromeは、追加されたフラグメント（moovを含む）を拒否し、その後のデコードエラーを引き起こします。 （Chromiumの問題#735335）</p> <p>19921:正常にバッファーされた場合でも、特定のHLSコンテンツの再生が停止する（Chromiumの問題#713540）</p> <p>・ 20444:IEとEdgeでバッファー範囲の終わりをシークすると、再生が停止する場合があります。</p> <p>・ 20511:広告のある場合もない場合も、HLSストリームではシーク拒否が観察されることがあります。</p> <p>・ 20743:Windows 10 Chromeでは、HLS Liveストリームは、MP4プリロール再生の前に数秒間再生されます。</p> <p>・ 21043:メタデータがないため、初回の読み込み時にビデオディメンションが正しくない可能性があります。</p> <p>・ 21115:プリロール広告がプレイリストのビデオに使用できる場合、開始の再生にはAndroidユーザージェスチャーが必要です。</p> <p>・ HLS Liveはタイムスタンプのロールオーバーをサポートしていません。</p> <p>・ AAC-SSRオーディオはサポートされていません。</p> <p>オーディオコーデックAC3および拡張AC3はサポートされていません。</p> <p>・タイムスタンプの不連続性があるが、不連続マーカーがないストリームの場合</p> <p>・ジャンプが原因で、再生に問題が発生し、シーク操作が正しくない可能性があります。</p> <p>・コンテンツの長さと再生時間が一致しない場合があります。</p> <p>・表現とレンディション間の不連続性は、他の条件と一致すると、同期と停止の問題を引き起こす可能性があります。</p> <p>・キャプションとWebVTTは、ストリームの終わりの近くに表示されない場合があります。</p> <p>・オーディオコーデックの変更は、タイムスタンプのジャンプに対してはサポートされません。</p> <p>・広告挿入はサポートされていません。</p> <p>・早送りトリックモードが原因で、Win 8.1 IE 11で再生ループが発生する場合があります（MSの問題#12446268）。</p> <p>DASH:</p> <p>・ライブストリームの場合 — 動的タイプのライブプロファイルがサポートされます。</p> <p>・ VoDストリームの場合 — 静的タイプのライブプロファイルがサポートされます。</p> <p>VoDストリームの場合 — オンデマンドプロファイルは広告ワークフローに対して認証されていません。</p> </td> 
   <td><p>・ DASHライブおよびDASH Video on Demandストリームはサポートされていません。</p> <p>・ PIP（ピクチャインピクチャ）ビデオ再生は、フルスクリーンモードのiOSではサポートされていません。</p> <p>Safari（ビデオタグ）の拡張では、正しいコンテンツタイプのヘッダーがないとマニフェストが少なくなります。</p> </td> 
   <td><p>・送信者アプリのapplicationIDは、受信者のURLをカスタム受信者アプリとして登録する際に生成されるものと同じである必要があります。</p> <p>・ DASHワークフローに対しては、リファレンスプレイヤが認証されています。 UIフレームワークが認証されていません。</p> <p>サポートされるメディアコーデックのリストについては、<a href="https://developers.google.com/cast/docs/media"><em>ここ</em></a>を参照してください。</p> </td> 
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
   <td><p>・ 20079:バッファ範囲内のシーク時にバッファーを書き直し</p> <p>20080:FlashABRの動作はMSEと一致しません。</p> </td> 
   <td><p>・ ABRストリーム内のオーディオ専用のフォールバックバリアントは、バッファーに関する制限のため無視されます。</p> <p>・ 12289:ABR制御パラメーターは、ミュークス化されていないHLS/DASHストリームの場合、オーディオには適用されません。</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>608/708キャプション</td> 
   <td> </td> 
   <td><p>・ 7810:Android 4.4.4 Chromeでは、プレイヤーが使用する基本的なCSSフォントファミリーがサポートされていないので、フォントスタイル変更機能が動作しません。</p> <p>・ 608キャプションの場合、CCチャネルは変更できません。</p> <p>・高度なスタイル設定機能は、608キャプションに対してはサポートされていません。</p> <p>埋め込みキャプション(608/708)。アクセシビリティタグを介して署名されます。</p> </td> 
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
   <td>21056:Flashフォールバックを使用した場合、プライマリストリームが再生中に404エラーを返す場合、ライブストリームに対してフェイルオーバーは発生しません。</td> 
   <td>マニフェストのフェイルオーバーは、コンテンツに対してのみ適用され、広告には適用されません。</td> 
   <td>プレイリストのフェイルオーバーが見つからない場合、SafariではHTTPエラーコード404に対してのみ機能します。</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>高度なフェイルオーバー</td> 
   <td> </td> 
   <td><p>・セグメントのフェイルオーバーでは、使用できないセグメントのスキップと再生の継続はサポートされません。</p> <p>20533:プレイリストに見つからないセグメントはDiscontinuityとして扱われ、次に使用可能なセグメントから再生が再開されます。</p> <p>21267:フェールオーバーによるストリームの切り替えは、古いセグメントのダウンロードの原因になる場合があります。</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>QoSおよびプレイヤー通知</td> 
   <td>21129:Flashフォールバックの場合、フレームレートは使用できません。</td> 
   <td><p>・ 11170:</p> <p>Timed_イベントは、MSEを使用するBrowser TVSDKでは、Flashのフォールバックを使用するBrowser TVSDKとは異なり、使用できません。</p> <p>21129:ライブストリームのフレームレートは計算されません。</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>cookieヘッダーのサポート</td> 
   <td> </td> 
   <td> </td> 
   <td><p>withCredentialsフラグとcookieヘッダーはSafariではサポートされていません。</p> <p>21051:SafariでCookieを許可するには、環境設定/プライバシーから「CookieとWebサイトのデータ」設定を有効にします。</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>カスタムタグ</td> 
   <td>14763:#で始まるカスタムタグ以外はサポートされません。 現在、Flashのフォールバック中に、このようなタグに対してTimedMetadataオブジェクトが作成され、レポートされます。</td> 
   <td>インバンドカスタムタグを持つストリームは認証されません。</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>遅延バインディングオーディオ</td> 
   <td> </td> 
   <td><p>・広告挿入は、HLSライブLBAストリームではサポートされていません。</p> <p>・ 17273:HLS VOD LBAストリームは、フェイルオーバー時にデフォルトのレンディションに切り替わります。最後に選択した状態に戻すことはできません。</p> <p>・ 20251:HLSライブLBAストリームは、シーク時に停止する場合があります。</p> <p>・ 20497:HLS LBA無音ストリームで、オーディオまたはビデオのフレームがストリームの終わり近くにない場合、プレイヤーはバッファリング状態のままです。</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>302リダイレクト</td> 
   <td> </td> 
   <td><p>15787:302</p> <p>リダイレクトの最適化は、windows EdgeおよびIEブラウザーでは、XMLHttpRequestオブジェクトのresponseURLプロパティをサポートしていないので、サポートされていません。</p> </td> 
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
   <td><strong>SafariのHTML5、iOS Safari</strong></td> 
   <td><strong>Chromecast（DASH再生のみ）</strong></td> 
  </tr> 
  <tr> 
   <td>VOD</td> 
   <td>オフセットでの再生</td> 
   <td><p>特定のオフセット値での再生の開始は、MP4コンテンツをサポートしていません。</p> </td> 
   <td>20492:オフセットの前のミッドロール広告は、コンテンツがオフセット値から再開される前に再生されます。</td> 
   <td>オフセット機能を使用した再生は、iOSではサポートされていません。</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD</td> 
   <td>トリック再生</td> 
   <td>iFrameレンディションのないストリームでは、スムーズなトリックプレイが機能しません。</td> 
   <td><p>・トリック再生アダプティブはFirefoxおよびInternet Explorerではサポートされていないので、これらのブラウザーでは逆トリックモードを使用できません。</p> <p>・広告と共にコンテンツを再生する場合、トリック再生は利用できません。</p> <p>・ 10435:DASH再生中に、Internet Explorerで前方トリック再生時にビデオがフリーズする(Win 8.1)</p> <p>断続的に これは、トリック再生の適合なしでビデオ要素playbackRateプロパティを使用しているためです。</p> <p>14182:Chromeブラウザーで巻き戻し中に、シークイベントが受け取られない場合があり、トリックモードが機能しないことがあります。</p> <p>・ 14942:非トリック再生ストリームの場合でも、Chrome for Androidでは再生速度を設定できますが、設定は適用されず、通常の速度で再生が続行されます。</p> <p>・ 17308:シークはトリック再生モードでは機能しません。</p> <p>・ 17309:Chromeブラウザーでは、リバーストリックモードを2秒以上維持することはできません。</p> <p>19272:DASHストリームの場合、Windows 10 Edgeブラウザーでトリック再生がバッファリングから回復しない場合がある。</p> </td> 
   <td>巻き戻しトリックモードはサポートされていません。</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>ID3の解析</td> 
   <td>20346:ID3フレームのテキストエンコードバイトも、SDKから返されます。</td> 
   <td><p>オーディオデータトランスポートストリーム(ADTS)で使用できるID3タグは、SDKでは無視されます。</p> <p>・ 12378:ID3時間指定メタデータは、MSEをサポートするFlashーとブラウザーで別々の時間に解析されるので、参照プレイヤーのタイムラインでの表示動作も異なります。</p> <p>・ 19247:ID3の解析はUIフレームワークではサポートされていません。</p> </td> 
   <td><p>・ 20323:AACセグメントの最初のサンプルのタイムスタンプを伝えるために使用するPRIV ID3タグがSafariで解析されない（Safariの問題#32422733）</p> <p>・ 20350:特定のデバイス（MAC OS X 10.1、iPad10など）では、Safariはトリックモードの場合にキュー変更イベントを提供しないので、ID3フレームを受け取りません。 （Safariの問題#32450526）</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>不連続マーカのサポート</td> 
   <td> </td> 
   <td><p>・クライアント側の広告挿入は、不連続性を含むHLSストリームではサポートされません。</p> <p>・オーディオコーデックの変更は、HLSストリームの不連続部分を超えて行うことはできません。</p> <p>・オーディオトラックスイッチは、不連続マーカーを持つHLSストリームに対してはサポートされていません</p> </td> 
   <td>不連続シーケンス番号は、Safariでの再生に不連続なHLSストリームに対する要件です。</td> 
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
   <td><strong>SafariのHTML5、iOS Safari</strong></td> 
   <td><strong>Chromecast（DASH再生のみ）</strong></td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>AES-128</td> 
   <td> </td> 
   <td>バイト範囲は、AES-128暗号化されたコンテンツではサポートされません。</td> 
   <td>12324:IVタグが指定されていない場合、HLS AES-128暗号化されたストリームはSafariでの再生に失敗します。</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD</td> 
   <td>DRM</td> 
   <td> </td> 
   <td><p>・ 12660:HTML5プレーヤーが、期限切れのPlayReady暗号化ダッシュコンテンツに対して内部サーバーエラーをスローする。</p> <p>・ 16720:ピリオドタグの開始属性がない場合、DASH DRMで暗号化されたコンテンツが機能しません。</p> <p>・ 18589:DRM保護されたDash VoD MultiperiodストリームのXlinkでの再生はサポートされていません。</p> <p>・ 18653:複数のキーを持つWidevine MultiPeriodコンテンツの再生は、最初の期間で停止し、次の期間に切り替えることはできません。</p> <p>・ 18656:再生可能な複数期間のストリーム。異なるキーで暗号化され、再生は行われません。</p> <p>Dash用のPlayready 2.0は認証されていません。</p> <p> </p> <p> </p> </td> 
   <td>12602:HLS Fairplay DRMメタデータが、SafariのHTML5プレイヤーによって繰り返し更新される</td> 
   <td><p>Bento4でパッケージ化されたDASH Widevine DRMコンテンツを再生できます。 Offline PackagerとShaka Packagerでパッケージ化されたコンテンツが再生されません。 DASH PlayReady DRMはサポートされていません。</p> </td> 
  </tr> 
 </tbody> 
</table>

**表19:コアAd Insertion機能(CSAI)**

<table> 
 <tbody> 
  <tr> 
   <td><strong>コンテンツタイプ</strong></td> 
   <td><strong>機能</strong></td> 
   <td><strong>Flash</strong></td> 
   <td><strong>Firefox、IE、Chrome、Android ChromeのHTML5</strong></td> 
   <td><strong>SafariのHTML5、iOS Safari</strong></td> 
   <td><strong>Chromecast（DASH再生のみ）</strong></td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>前/中/後</td> 
   <td> </td> 
   <td><p>・ HLSライブコンテンツを含むプリロール広告は、デュアルプレイヤーモードで再生されます。</p> <p>・ HLSコンテンツを含むDASH広告とDASHコンテンツを含むHLS広告はサポートされていません。</p> <p>・ 19002:MSE adBreakを含むHTML5プレイヤーの場合。 insertionTypeは、正しい挿入タイプ（例：クライアントの挿入やサーバーの挿入）を表す正しい値を返しません。</p> <p>7794:デフォルトのコントロールバーがフルスクリーンモードで表示されるモバイルデバイス（iOS、Chrome 33以前またはネイティブブラウザー搭載のAndroid）では、広告を再生時にシークバーボタンと早送りボタンを使用できます。</p> <p>・ 11048:広告からHLS Liveコンテンツへの切り替えは、メディアソースの拡張機能の場合にはスムーズではありません。</p> <p>・ 16083:Android 4.4 Chrome v52では、HLSコンテンツを含むHLS広告が、再生を停止した後にパイプラインデコードエラーになる場合があります。</p> <p>・ 16097:広告の時間中に発生したエラーは処理されません。メインストリームの再生が停止する場合があります。</p> <p>・ 18095:MP4広告は、HLSライブコンテンツではサポートされません。</p> <p>19120:HLSコンテンツを含むHLS広告に対して複数のシークを行うと、ストリームの再生が停止する場合があります。</p> <p>・ 19131:プリロール広告の時間からコンテンツに切り替える際に、バッファリングオーバーレイが表示される場合があります。</p> <p>・ 20296:HLSライブストリームの場合、DVR時間内でシークバックし、解決されたミッドロールをシークオーバーすると、再生が停止する場合があります。</p> <p>・ 20298：ミッドロールを含むHLSライブストリームは、最初のミッドロールが停止し、DVRウィンドウから移動します。</p> <p>・ 20317:広告の時間に複数の広告が含まれる場合、次の広告に切り替えるとHLSライブストリームが停止する場合や、広告からコンテンツに切り替えるとHLSライブストリームが停止する場合があります。</p> 
    <ul> 
     <li>HLSライブストリームのDVR時間枠内の広告は解決されません。</li> 
    </ul> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>VAST 2.0/3.0</td> 
   <td> </td> 
   <td>SDKは、VAST adSourceに対するVMAP応答内のシーケンス属性を無視します。</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>VAST 2.0/3.0</td> 
   <td> </td> 
   <td>20779:SDKは、VAST adSourceに対するVMAP応答内のシーケンス属性を順守しません。</td> 
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
   <td>クリエイティブの再パッケージング</td> 
   <td> </td> 
   <td>21464:広告の時間に含まれる広告の1つに対してクリエイティブの再パッケージングが失敗した場合、広告の応答は完全に破棄されます。</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

**表20:高度なAd Insertion機能(CSAI)**

<table> 
 <tbody> 
  <tr> 
   <td><strong>コンテンツタイプ</strong></td> 
   <td><strong>機能</strong></td> 
   <td><strong>Flash</strong></td> 
   <td><strong>Firefox、IE、Chrome、Android ChromeのHTML5</strong></td> 
   <td><strong>SafariのHTML5、iOS Safari</strong></td> 
   <td><strong>Chromecast（DASH再生のみ）</strong></td> 
  </tr> 
  <tr> 
   <td>VOD</td> 
   <td>広告のみ</td> 
   <td> </td> 
   <td>20056:Playerのテクノロジーのプロパティは、広告のみの再生の場合は空のメインコンテンツに基づいているので、関連しません</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>カスタム広告ポリシー</td> 
   <td> </td> 
   <td><p>・広告動作は、MP4広告とMP4コンテンツではサポートされていません。</p> <p>・ 13973:カスタム広告動作 — MSEで使用する場合、SKIPポリシーは完全なイベントをスローしません。</p> <p>・ 14939:カスタム広告動作ポリシーのスキップとスキップ広告の時間がDASHコンテンツで機能しません。</p> <p>・ 17131:広告の最初のフレームが表示され、SKIP広告ブレークポリシーの場合はコンテンツが再開されます。</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>コンパニオン広告/バナー広告/クリック可能な広告</td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td>リファレンスプレイヤーを使用している場合、バナー広告は表示されません。</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>VPAID 2.0</td> 
   <td> </td> 
   <td><p>・広告動作は、VPAID広告に対してはサポートされていません。</p> <p>・ 15032:広告の時間内にMP4またはHLS広告と組み合わせたVPAID広告はサポートされていません。</p> <p>・ 19001:AndroidおよびiOSで、VPAID広告がメインコンテンツ重複オーディオトラックとして再生されるときに、メインコンテンツの1つと広告の1つが可聴になります。</p> <p>・ 20762:VPAID広告は、ピクチャインピクチャ(PIP)ではサポートされません。</p> <p>・ 21172:VPAID広告を含むHLS VODコンテンツに対して、再生完了のイベントが受信されません。</p> <p>・ 21173:HLS VODコンテンツおよびポストロールVPAID広告に対して、onAdBreakCompleteEventを受け取りません。</p> </td> 
   <td>プレイヤーは、VPAID広告とメインコンテンツを切り替えながら、通常モードとフルスクリーンモードを切り替えます。</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

**表21:統合**

| **コンテンツタイプ** | **機能** | **Flash** | **Firefox、IE、Chrome、Android ChromeのHTML5** | **SafariのHTML5、iOS Safari** | **Chromecast（DASH再生のみ）** |
|---|---|---|---|---|---|
| VOD + Live | Adobe AnalyticsVHL統合 |  | 19004:Video Analyticsのトラッキングは、UIコンフィギュレーターツールでは使用できません。 |  |  |

## 役立つリソース{#helpful-resources}

* [Adobe Primetimeラーニングとサポート](https://helpx.adobe.com/support/primetime.html)のページにある完全なヘルプドキュメントを参照してください。