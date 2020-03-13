---
description: Primetime Player APIを使用して、プレイヤーの動作をカスタマイズできます。
seo-description: Primetime Player APIを使用して、プレイヤーの動作をカスタマイズできます。
seo-title: Mediacoreクラス
title: Mediacoreクラス
uuid: 2d4e41e6-e689-4f79-9021-1ab8ce0fe40d
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Mediacoreクラス {#mediacore-classes}

Primetime Player APIを使用して、プレイヤーの動作をカスタマイズできます。

TVSDKのAPIに関する完全なドキュメントを参照するには、 [Adobe Primetime APIリファレンスを参照してください](https://help.adobe.com/en_US/primetime/api/index.html#api-Adobe_Primetime_API_References)。

メディアプレイヤーとそのリソースを記述するクラスです。
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
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/ABRControlParameters.html" format="html" scope="external"> ABRControlParameters</a> ABRControlParameters</span> </td> 
   <td colname="2"> すべての可変ビットレート制御パラメーターをカプセル化するクラス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/AdClientFactory.html" format="html" scope="external"> AdClientFactory</a></span> </td> 
   <td colname="2"> オポチュニティディテクターを作成するためのインターフェイス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/AdvertisingFactory.html" format="html" scope="external"> AdvertisingFactory</a></span> </td> 
   <td colname="2"> ad decisioningプロセスのカスタマイズを可能にするファクトリクラス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/BufferControlParameters.html" format="html" scope="external"> BufferControlParameters</a></span> </td> 
   <td colname="2"> すべてのバッファー制御パラメーターをカプセル化するクラス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/DefaultAdPolicySelector.html" format="html" scope="external"> DefaultAdPolicySelector</a></span> </td> 
   <td colname="2"> 広告再生動作のデフォルトの実装。 アプリケーションが広告動作をカスタマイズできるインターフェイス。</td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/DefaultMediaPlayer.html" format="html" scope="external"> DefaultMediaPlayer</a></span> </td> 
   <td colname="2">MediaPlayerインターフェイスのデフォルトの <span class="codeph"> クラス実装</span> 。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.html" format="html" scope="external"> MediaPlayer</a></span> </td> 
   <td colname="2">DefaultMediaPlayerクラスのパブリックインタ <span class="codeph"> ーフェイス</span> 。 Event、PlayerState、Visibilityの列挙を含みます。 </td> 
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
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.EventListener.html" format="html" scope="external"> MediaPlayer.EventListener</a></span> </td> 
   <td colname="2"> イベントリスナーの登録を統合するために使用するマーカーインターフェイス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html" format="html" scope="external"> MediaPlayer.PlaybackEventListener</a></span> </td>
   <td colname="2"> 再生中に呼び出されるコールバックのインターフェイス定義。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.QOSEventListener.html" format="html" scope="external"> MediaPlayer.QOSEventListener</a></span> </td> 
   <td colname="2"> QoS中に呼び出されるコールバックのインターフェイス定義。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItem.html" format="html" scope="external"> MediaPlayerItem</a></span> </td> 
   <td colname="2"> オーディオビデオメディアを表すインターフェイス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItemLoader.html" format="html" scope="external"> MediaPlayerItemLoader</a></span> </td> 
   <td colname="2"> メディアプレイヤーリソースを読み込み、対応するMediaPlayerItemオブジェクトを作成するクラス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerItemLoader.LoaderListener.html" format="html" scope="external"> MediaPlayerItemLoader.LoaderListener</a></span> </td> 
   <td colname="2"> MediaPlayerItemLoaderオブジェクトに関連付けられたリスナーメソッドを定義するインターフェイス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerView.html" format="html" scope="external"> MediaPlayerView</a></span> </td> 
   <td colname="2"> ビデオのレンダリングにMediaPlayerが使用するビューのクラス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaResource.html" format="html" scope="external"> MediaResource</a></span> </td> 
   <td colname="2"> メディアリソースに関するすべての情報をラップするクラス。 メディアリソースのタイプの列挙を含みます。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/PlacementOpportunityDetector.html" format="html" scope="external"> PlacementOpportunityDetector</a></span> </td> 
   <td colname="2"> Ad Decisioningプロセスの配置として使用されるマニフェスト内キューの処理に使用されるインターフェイス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/PSDKConfig.html" format="html" scope="external"> PSDKConfig</a></span> </td> 
   <td colname="2"> デフォルトのキュータグに加え、広告配置の実行時にメディアプレイヤーが使用するカスタムタグをカプセル化するクラス。 また、アプリケーションが通知を受け取るタグ名も含まれます。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/TextFormat.html" format="html" scope="external"> TextFormat</a></span> </td> 
   <td colname="2"> テキストスタイル（クローズドキャプションスタイルなど）を記述する様々な属性をカプセル化するインターフェイス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/TextFormatBuilder.html" format="html" scope="external"> TextFormatBuilder</a></span> </td> 
   <td colname="2"> テキストの形式設定を行うクラスメソッド。 </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/Version.html" format="html" scope="external"> バージョン</a></span> </td> 
   <td colname="2"> TVSDKのバージョンと説明を提供するクラス。 </td> 
  </tr> 
 </tbody> 
</table>
