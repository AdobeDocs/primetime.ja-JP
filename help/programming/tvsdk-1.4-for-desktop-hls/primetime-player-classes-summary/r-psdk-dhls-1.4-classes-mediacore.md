---
description: Primetime Player APIを使用して、プレイヤーの動作をカスタマイズできます。 メディアプレイヤーとそのリソースを記述するクラスです。
seo-description: Primetime Player APIを使用して、プレイヤーの動作をカスタマイズできます。 メディアプレイヤーとそのリソースを記述するクラスです。
seo-title: Mediacoreクラス
title: Mediacoreクラス
uuid: f43d6968-cb08-4a8e-aebd-7934763df680
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d
workflow-type: tm+mt
source-wordcount: '692'
ht-degree: 0%

---


# Mediacoreクラス{#mediacore-classes}

Primetime Player APIを使用して、プレイヤーの動作をカスタマイズできます。 メディアプレイヤーとそのリソースを記述するクラスです。

TVSDKのAPIに関する完全なドキュメントを参照するには、[Adobe PrimetimeAPIリファレンス](https://help.adobe.com/en_US/primetime/api/index.html)を参照してください。

メディアプレイヤーとそのリソースを記述するクラスです。
パッケージ：[com.adobe.mediacore](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/package-detail.html)

<table frame="all" colsep="1" rowsep="1" id="table_2801E01282A948E6917910CA2FD1E05C"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> <p>名前 </p> </th> 
   <th colname="2" class="entry"> <p>説明 </p> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/ABRControlParameters.html" format="html" scope="external"> ABRControlParameters</a> </span> </td> 
   <td colname="2"> すべての可変ビットレート制御パラメーターをカプセル化するクラス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/BufferControlParameters.html" format="html" scope="external"> BufferControlParameters</a></span> </td> 
   <td colname="2"> すべてのバッファー制御パラメーターをカプセル化するクラス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/ClosedCaptionStyles.html" format="html" scope="external"> ClosedCaptionsStyles</a></span> </td> 
   <td colname="2"> クローズドキャプションのテキストのすべてのスタイルプロパティを定義するクラス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/ClosedCaptionsVisibility.html" format="html" scope="external"> ClosedCaptionsVisibility</a></span> </td> 
   <td colname="2"> クローズドキャプションを表示するかどうかを制御するクラス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/ContentFactory.html" format="html" scope="external"> ContentFactory</a> </span> </td> 
   <td colname="2"> 広告ワークフローで使用される様々なコンポーネントを作成および管理するファクトリの基本クラス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/DefaultAdPolicySelector.html" format="html" scope="external"> DefaultAdPolicySelector</a></span> </td> 
   <td colname="2"> 広告再生動作のデフォルト実装。 アプリケーションが広告の動作をカスタマイズできるインターフェイス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/DefaultContentFactory.html" format="html" scope="external"> DefaultContentFactory</a></span> </td> 
   <td colname="2">メタデータと広告解決プロセスの両方をサポートする、<span class="codeph"> MediaPlayerClient</span>ファクトリのデフォルト実装。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/DefaultMediaPlayer.html" format="html" scope="external"> DefaultMediaPlayer</a></span> </td> 
   <td colname="2"><span class="codeph"> MediaPlayer</span>インターフェイスのデフォルトクラス実装。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/DefaultMediaPlayerConfig.html" format="html" scope="external"> DefaultMediaPlayerConfig</a> </span> </td> 
   <td colname="2"> メディアプレイヤーのデフォルト実装の設定クラス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/DefaultMediaPlayerItemConfig.html" format="html" scope="external"> DefaultMediaPlayerItemConfig</a></span> </td> 
   <td colname="2"> デフォルトのメディアプレイヤーアイテム設定クラス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/DefaultMediaPlayerItemLoader.html" format="html" scope="external"> DefaultMediaPlayerItemLoader</a></span> </td> 
   <td colname="2"> 初期設定のメディアプレイヤーアイテムローダー。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayer.html" format="html" scope="external"> MediaPlayer</a></span> </td> 
   <td colname="2"><span class="codeph"> DefaultMediaPlayer</span>クラスのパブリックインターフェイス。 イベント、PlayerState、Visibilityの定義済みリストが含まれます。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayerConfig.html" format="html" scope="external"> MediaPlayerConfig</a> </span> </td> 
   <td colname="2"> メディアプレイヤー設定クラス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayerContext.html" format="html" scope="external"> MediaPlayerContext</a></span> </td> 
   <td colname="2"> 追加のコンテキストをメディアプレイヤーに提供するクラス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayerItem.html" format="html" scope="external"> MediaPlayerItem</a></span> </td> 
   <td colname="2"> オーディオビデオメディアを表すインターフェイス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/DefaultMediaPlayerItemConfig.html" format="html" scope="external"> DefaultMediaPlayerItemConfig</a></span> </td> 
   <td colname="2"> デフォルトのメディアプレイヤーアイテム設定クラス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayerItemLoader.html" format="html" scope="external"> MediaPlayerItemLoader</a></span> </td> 
   <td colname="2">メディアプレイヤーリソースを読み込み、対応する<span class="codeph"> MediaPlayerItem</span>オブジェクトを作成するクラス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayerStatus.html" format="html" scope="external"> MediaPlayerStatus</a></span> </td> 
   <td colname="2"> サポートされているメディアプレイヤーのステータスを含むクラス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayerView.html" format="html" scope="external"> MediaPlayerView</a></span> </td> 
   <td colname="2"><span class="codeph"> MediaPlayer</span>がビデオレンダリングに使用する表示のクラス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaResource.html" format="html" scope="external"> MediaResource</a></span> </td> 
   <td colname="2"> メディアリソースに関するすべての情報をラップするクラス。 メディアリソースの種類の定義済みリストが含まれます。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaResourceType.html" format="html" scope="external"> MediaResourceType</a></span> </td> 
   <td colname="2"> サポートされるメディアリソースタイプを含むクラス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/PSDKConfig.html" format="html" scope="external"> PSDKConfig</a></span> </td> 
   <td colname="2"> デフォルトのキュータグに加え、広告を配置する際にメディアプレイヤーが使用するカスタムタグをカプセル化するクラス。 また、アプリケーションに通知したいタグ名も含まれます。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/TextFormat.html" format="html" scope="external"> TextFormat</a></span> </td> 
   <td colname="2"> テキストスタイル（クローズドキャプションスタイルなど）を記述する様々な属性をカプセル化するインターフェイス。 </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/Version.html" format="html" scope="external"> バージョン</a></span> </td> 
   <td colname="2"> TVSDKのバージョンと説明を提供するクラス。 </td> 
  </tr> 
 </tbody> 
</table>

