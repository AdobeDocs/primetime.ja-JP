---
description: メディアプレイヤーとそのリソースを記述するクラスです。
seo-description: メディアプレイヤーとそのリソースを記述するクラスです。
seo-title: Media Playerクラス
title: Media Playerクラス
uuid: 6b59dcff-9722-4a84-9049-f6f10f7b3e82
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---


# メディアプレイヤクラス{#media-player-classes}

Primetime Player Objective-C APIを使用して、プレイヤーの動作をカスタマイズできます。

メディアプレイヤーとそのリソースを記述するクラスです。

<table frame="all" colsep="1" rowsep="1" id="table_bm2_wl2_2m"> 
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><b>クラス</b> </td> 
   <td colname="2"><b>説明</b> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTABRControlParameters.html" format="html" scope="external"> PTABRControlParameters</a></span> </td> 
   <td colname="2">すべての可変ビットレート制御パラメーターをカプセル化します。 次のパラメーターがサポートされています。 
    <ul id="ul_pnh_hm2_2m"> 
     <li id="li_46572FE1EB514AFF8C9F731E44DAF30B"><span class="codeph"> minBitRate</span> </li> 
     <li id="li_A10C75C9A5234241A5B84A4139F4D143"><span class="codeph"> maxBitRate</span> </li> 
     <li id="li_4E77E367A2E848D2B3E1A9C52209A7B2"><span class="codeph"> initialBitRate</span> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTDefaultMediaPlayerClientFactory.html" format="html" scope="external"> PTDefaultMediaPlayerClientFactory</a></span> </td> 
   <td colname="2"> TVSDKでの<span class="codeph"> PTMediaPlayerClientFactory</span>のデフォルト実装。 使用可能な<span class="codeph"> PTOpportunityResolver</span>、<span class="codeph"> PTContentResolver</span>、<span class="codeph"> PTAdPolicySelector</span>の各インスタンスを提供します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaPlayer.html" format="html" scope="external"> PTMediaPlayer</a></span> </td> 
   <td colname="2">Primetime Playerフレームワークのルートコンポーネントを定義します。 <p>アプリケーションは、このクラスのインスタンスを作成してメディアを再生します。 このコンポーネントは、通知をディスパッチして、特定の時点でのプレイヤーのステータスをアプリケーションに知らせます。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Protocols/PTMediaPlayerClientFactory.html" format="html" scope="external"> PTMediaPlayerClientFactory</a></span> </td> 
   <td colname="2"> 使用可能な<span class="codeph"> PTOpportunityResolver</span> 、<span class="codeph"> PTContentResolver</span>および<span class="codeph"> PTAdPolicySelector</span>インスタンスを提供するためにカスタムメディアプレイヤークライアントファクトリが実装する必要があるメソッドを記述するプロトコル。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaPlayerItem.html" format="html" scope="external"> PTMediaPlayerItem</a></span> </td> 
   <td colname="2"> 特定のオーディオビデオメディアを表します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaPlayerView.html" format="html" scope="external"> PTMediaPlayerView</a></span> </td> 
   <td colname="2"> Primetime Playerフレームワークの表示コンポーネントを管理します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaProfile.html" format="html" scope="external"> PTMediaProfile</a></span> </td> 
   <td colname="2"> バリアントプレイリストの単一ストリームのプロファイルを表します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTMediaSelectionOption.html" format="html" scope="external"> PTMediaSelectionOption</a></span> </td> 
   <td colname="2">様々な言語設定、アクセシビリティ要件またはカスタムアプリケーション設定に対応するためのオーディオビジュアルメディアリソースを表します。 有効なオプションの種類： 
    <ul id="ul_p2q_gn2_2m"> 
     <li id="li_46BE5AE49732481FB6D336FFF896E5AD">サブタイトル(<span class="codeph"> PTMediaSelectionOptionTypeSubtitle</span>) </li> 
     <li id="li_6CEADCA12D4A48B7AE4A539985F32119">代替オーディオ(<span class="codeph"> PTMediaSelectionOptionTypeAudio</span>) </li> 
     <li id="li_248D3D997F8A4B6E9B48869F84060D1F"> <p>未定義(<span class="codeph"> PTMediaSelectionOptionTypeUndefined</span>) </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTOpportunityResolver.html" format="html" scope="external"> PTOpportunityResolverclass、</a> </span>  <span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Protocols/PTOpportunityResolver.html" format="html" scope="external"> </a> PTOpportunityResolverprotocol</span> </td> 
   <td colname="2"> Adobe Primetimead decisioningプロセスの場所として使用されるマニフェスト内キューを処理するために使用されるクラス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Protocols/PTOpportunityResolverDelegate.html" format="html" scope="external"> PTOpportunityResolverDelegate</a></span> </td> 
   <td colname="2"> オポチュニティ解決の状態を委譲するための通信にカスタムオポチュニティリゾルバー(<span class="codeph"> PTOpportunityResolver</span>)が使用する必要があるメソッドを記述するプロトコル。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTSDK.html" format="html" scope="external"> PTSDK</a></span> </td> 
   <td colname="2"> TVSDKのバージョンとその機能について説明します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTSDKConfig.html" format="html" scope="external"> PTSDKConfig</a></span> </td> 
   <td colname="2"> TVSDKのグローバル設定を公開し、アプリケーションがカスタムHLSタグをサブスクライブできるようにします。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTTextStyleRule.html" format="html" scope="external"> PTTextStyleRule</a></span> </td> 
   <td colname="2"> ルールの辞書を形成するテキストスタイル属性キーを表す定数を定義します。 </td> 
  </tr> 
 </tbody> 
</table>

