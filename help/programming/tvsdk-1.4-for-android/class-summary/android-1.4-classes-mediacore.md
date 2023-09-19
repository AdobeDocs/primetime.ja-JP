---
description: Primetime Player API を使用して、プレーヤーの動作をカスタマイズできます。
title: Mediacore クラス
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 0%

---

# Mediacore クラス {#mediacore-classes}

Primetime Player API を使用して、プレーヤーの動作をカスタマイズできます。

TVSDK の API に関する完全なドキュメントを参照するには、 [Adobe Primetime API リファレンス](https://help.adobe.com/en_US/primetime/api/index.html#api-Adobe_Primetime_API_References).

メディアプレーヤーとそのリソースを記述するクラスです。
パッケージ： [com.adobe.mediacore](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/package-summary.html)

<table frame="all" colsep="1" rowsep="1" id="table_2801E01282A948E6917910CA2FD1E05C"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> <p>名前 </p> </th> 
   <th colname="2" class="entry"> <p>説明 </p> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/ABRControlParameters.html" format="html" scope="external"> ABRControlParameters</a>  ABRControlParameters</span> </td> 
   <td colname="2"> すべての適応ビットレート制御パラメーターをカプセル化するクラス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/AdClientFactory.html" format="html" scope="external"> AdClientFactory</a> </span> </td> 
   <td colname="2"> オポチュニティディテクターを作成するためのインターフェイス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/AdvertisingFactory.html" format="html" scope="external"> AdvertisingFactory</a> </span> </td> 
   <td colname="2"> 広告判定プロセスのカスタマイズを可能にするファクトリクラス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/BufferControlParameters.html" format="html" scope="external"> BufferControlParameters</a> </span> </td> 
   <td colname="2"> すべてのバッファ制御パラメーターをカプセル化するクラス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/DefaultAdPolicySelector.html" format="html" scope="external"> DefaultAdPolicySelector</a></span> </td> 
   <td colname="2"> 広告の再生動作のデフォルト実装。 アプリケーションが広告の動作をカスタマイズするインターフェイス。</td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/DefaultMediaPlayer.html" format="html" scope="external"> DefaultMediaPlayer</a></span> </td> 
   <td colname="2">のデフォルトクラス実装 <span class="codeph"> MediaPlayer</span> インターフェイス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.html" format="html" scope="external"> MediaPlayer</a> </span> </td> 
   <td colname="2">のパブリックインターフェイス <span class="codeph"> DefaultMediaPlayer</span> クラス。 Event、PlayerState、Visibility の列挙が含まれます。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.AdPlaybackEventListener.html" format="html" scope="external"> MediaPlayer.AdPlaybackEventListener</a></span> </td> 
   <td colname="2"> 広告の再生中に呼び出されるコールバックのインターフェイス定義。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.DRMEventListener.html" format="html" scope="external"> MediaPlayer.DRMEventListener</a></span> </td> 
   <td colname="2"> 保護されたメタデータが使用可能になったときに呼び出されるコールバックのインターフェイス定義。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.EventListener.html" format="html" scope="external"> MediaPlayer.EventListener</a> </span> </td> 
   <td colname="2"> イベントリスナーの登録を統合するために使用するマーカーインターフェイス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html" format="html" scope="external"> MediaPlayer.PlaybackEventListener</a> </span> </td>
   <td colname="2"> 再生中に呼び出されるコールバックのインターフェイス定義。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html" format="html" scope="external"> MediaPlayer.QOSEventListener</a> </span> </td> 
   <td colname="2"> QoS 中に呼び出されるコールバックのインターフェイス定義。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItem.html" format="html" scope="external"> MediaPlayerItem</a> </span> </td> 
   <td colname="2"> オーディオビデオメディアを表すインターフェイス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItemLoader.html" format="html" scope="external"> MediaPlayerItemLoader</a> </span> </td> 
   <td colname="2"> メディアプレーヤーリソースを読み込み、対応する MediaPlayerItem オブジェクトを作成するクラス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItemLoader.LoaderListener.html" format="html" scope="external"> MediaPlayerItemLoader.LoaderListener</a> </span> </td> 
   <td colname="2"> MediaPlayerItemLoader オブジェクトに関連付けられるリスナーメソッドを定義するインターフェイス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerView.html" format="html" scope="external"> MediaPlayerView</a> </span> </td> 
   <td colname="2"> ビデオのレンダリングに MediaPlayer が使用するビューのクラス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaResource.html" format="html" scope="external"> MediaResource</a> </span> </td> 
   <td colname="2"> メディアリソースに関するすべての情報をラップするクラス。 メディアリソースのタイプの列挙を含みます。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/PlacementOpportunityDetector.html" format="html" scope="external"> PlacementOpportunityDetector</a> </span> </td> 
   <td colname="2"> Ad Decisioning プロセスの配置として使用されるマニフェスト内キューの処理に使用されるインターフェイス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/PSDKConfig.html" format="html" scope="external"> PSDKConfig</a> </span> </td> 
   <td colname="2"> デフォルトのキュータグに加えて、広告配置の実行時にメディアプレーヤーが使用するカスタムタグをカプセル化するクラスです。 また、アプリケーションが通知を受け取るタグ名も含まれます。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/TextFormat.html" format="html" scope="external"> TextFormat</a> </span> </td> 
   <td colname="2"> テキストスタイル（クローズドキャプションスタイルなど）を表す様々な属性をカプセル化するインターフェイス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/TextFormatBuilder.html" format="html" scope="external"> TextFormatBuilder</a></span> </td> 
   <td colname="2"> テキストの書式を設定するクラスメソッド。 </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/Version.html" format="html" scope="external"> バージョン</a></span> </td> 
   <td colname="2"> TVSDK のバージョンと説明を提供するクラス。 </td> 
  </tr> 
 </tbody> 
</table>
