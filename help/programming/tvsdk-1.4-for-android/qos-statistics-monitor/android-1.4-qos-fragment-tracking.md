---
description: サービス品質 (QoS) により、ビデオエンジンのパフォーマンスに関する詳細な情報が得られます。 TVSDK は、再生、バッファリング、デバイスに関する詳細な統計情報を提供します。
title: 読み込み情報を使用してフラグメントレベルで追跡
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# 読み込み情報を使用してフラグメントレベルで追跡{#track-at-the-fragment-level-using-load-information}

サービス品質 (QoS) により、ビデオエンジンのパフォーマンスに関する詳細な情報が得られます。 TVSDK は、再生、バッファリング、デバイスに関する詳細な統計情報を提供します。

TVSDK は、以下のダウンロードされたリソースに関する情報も提供します。

1. プレイリスト/マニフェストファイル
1. ファイルフラグメント
1. ファイルのトラッキング情報

   フラグメントやトラックなど、ダウンロードされたリソースに関する Quality of Service(QoS) 情報を、 `LoadInfo` クラス。

1. の実装 `onLoadInfo` コールバックイベントリスナー。
1. フラグメントがダウンロードされるたびに TVSDK が呼び出すイベントリスナーを登録します。
1. 関心のあるデータを `LoadInfo` コールバックに渡されるパラメーター。

   <table id="table_06BD536A23AB4A73B510998426BAE143"> 
    <thead> 
      <tr> 
      <th colname="col01" class="entry"> プロパティ </th> 
      <th colname="col1" class="entry"> タイプ </th> 
      <th colname="col2" class="entry"> 説明 </th> 
      </tr> 
    </thead>
    <tbody> 
      <tr> 
      <td colname="col01"> <span class="codeph"> downloadDuration </span> </td> 
      <td colname="col1"> <span class="codeph"> long </span> </td> 
      <td colname="col2"> <p>ダウンロードの時間（ミリ秒）。 </p> <p>TVSDK は、クライアントがサーバーに接続するのに要した時間と、フラグメント全体のダウンロードに要した時間を区別しません。 例えば、10 MB のセグメントのダウンロードに 8 秒かかる場合、 TVSDK はその情報を提供しますが、最初のバイトまで 4 秒かかり、フラグメント全体のダウンロードに 4 秒かかったとは通知しません。 </p> </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> mediaDuration </span> </td> 
      <td colname="col1"> <span class="codeph"> long </span> </td> 
      <td colname="col2"> ダウンロードされたフラグメントのメディア時間（ミリ秒）。 </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> periodIndex </span> </td> 
      <td colname="col1"> <span class="codeph"> int </span> </td> 
      <td colname="col2"> ダウンロードされたリソースに関連付けられたタイムライン期間インデックス。 </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> サイズ </span> </td> 
      <td colname="col1"> <span class="codeph"> long </span> </td> 
      <td colname="col2"> ダウンロードされたリソースのサイズ（バイト単位）。 </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> trackIndex </span> </td> 
      <td colname="col1"> <span class="codeph"> int </span> </td> 
      <td colname="col2"> 対応するトラックのインデックス（わかっている場合）。それ以外の場合は 0。 </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> trackName </span> </td> 
      <td colname="col1"> <span class="codeph"> 文字列 </span> </td> 
      <td colname="col2"> 対応するトラックの名前（わかっている場合）。それ以外の場合は null。 </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> trackType </span> </td> 
      <td colname="col1"> <span class="codeph"> 文字列 </span> </td> 
      <td colname="col2"> 対応するトラックのタイプ（わかっている場合）。それ以外の場合は null。 </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> type </span> </td> 
      <td colname="col1"> <span class="codeph"> 文字列 </span> </td> 
      <td colname="col2"> TVSDK がダウンロードした内容。 次のいずれかを実行します。 
      <ul id="ul_9C3BDEBD878544DA95C7FF81114F9B5C"> 
      <li id="li_A093552B492A44FD8B30785E465F6886">MANIFEST — プレイリスト/マニフェスト </li> 
      <li id="li_DEF9AC71AA564F9BB4C5D4E834432EE5">フラグメント — フラグメント </li> 
      <li id="li_57821F47B6F04CD38570BCE6447A01B8">TRACK — 特定のトラックに関連付けられたフラグメント </li> 
      </ul> リソースのタイプを検出できない場合があります。 この場合、FILE が返されます。 </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> url </span> </td> 
      <td colname="col1"> <span class="codeph"> 文字列 </span> </td> 
      <td colname="col2"> ダウンロードされたリソースを指す URL。 </td> 
      </tr> 
    </tbody> 
   </table>
