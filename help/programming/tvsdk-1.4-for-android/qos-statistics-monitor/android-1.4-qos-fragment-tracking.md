---
description: サービス品質(QoS)オファーは、ビデオエンジンの動作状況に関する詳細な表示です。 TVSDKは、再生、バッファリング、デバイスに関する詳細な統計情報を提供します。
title: 読み込み情報を使用したフラグメントレベルでの追跡
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---


# 読み込み情報{#track-at-the-fragment-level-using-load-information}を使用してフラグメントレベルで追跡

サービス品質(QoS)オファーは、ビデオエンジンの動作状況に関する詳細な表示です。 TVSDKは、再生、バッファリング、デバイスに関する詳細な統計情報を提供します。

TVSDKは、以下のダウンロードされたリソースに関する情報も提供します。

1. プレイリスト/マニフェストファイル
1. ファイルフラグメント
1. ファイルの追跡情報

   フラグメントやトラックなど、ダウンロードされたリソースに関するQoS(Quality Of Service)情報を`LoadInfo`クラスから読み取ることができます。

1. `onLoadInfo`コールバックイベントリスナーを実装します。
1. フラグメントがダウンロードされるたびにTVSDKが呼び出すイベントリスナーを登録します。
1. コールバックに渡される`LoadInfo`パラメーターから、目的のデータを読み取ります。

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
      <td colname="col01"> <span class="codeph"> downloadDuration  </span> </td> 
      <td colname="col1"> <span class="codeph"> long  </span> </td> 
      <td colname="col2"> <p>ダウンロード時間（ミリ秒）。 </p> <p>TVSDKは、クライアントがサーバーに接続するのに要した時間と、フラグメント全体のダウンロードに要した時間を区別しません。 例えば、10 MBのセグメントのダウンロードに8秒かかる場合、TVSDKはこの情報を提供しますが、最初のバイトまでに4秒かかり、フラグメント全体のダウンロードに4秒かかるとは通知しません。 </p> </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> mediaDuration  </span> </td> 
      <td colname="col1"> <span class="codeph"> long  </span> </td> 
      <td colname="col2"> ダウンロードされたフラグメントのメディア時間（ミリ秒）。 </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> periodIndex  </span> </td> 
      <td colname="col1"> <span class="codeph"> int  </span> </td> 
      <td colname="col2"> ダウンロードされたリソースに関連付けられているタイムライン期間インデックス。 </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> size  </span> </td> 
      <td colname="col1"> <span class="codeph"> long  </span> </td> 
      <td colname="col2"> ダウンロードされたリソースのサイズ（バイト単位）。 </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> trackIndex  </span> </td> 
      <td colname="col1"> <span class="codeph"> int  </span> </td> 
      <td colname="col2"> 対応するトラックのインデックス（わかる場合）。それ以外の場合は、0。 </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> trackName  </span> </td> 
      <td colname="col1"> <span class="codeph"> 文字列  </span> </td> 
      <td colname="col2"> 対応するトラックの名前（わかる場合）。それ以外の場合はnull。 </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> trackType  </span> </td> 
      <td colname="col1"> <span class="codeph"> 文字列  </span> </td> 
      <td colname="col2"> 対応するトラックのタイプ（わかる場合）。それ以外の場合はnull。 </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> type  </span> </td> 
      <td colname="col1"> <span class="codeph"> 文字列  </span> </td> 
      <td colname="col2"> TVSDKがダウンロードした内容。 次のいずれかです。 
      <ul id="ul_9C3BDEBD878544DA95C7FF81114F9B5C"> 
      <li id="li_A093552B492A44FD8B30785E465F6886">MANIFEST — プレイリスト/マニフェスト </li> 
      <li id="li_DEF9AC71AA564F9BB4C5D4E834432EE5">FRAGMENT — フラグメント </li> 
      <li id="li_57821F47B6F04CD38570BCE6447A01B8">TRACK — 特定のトラックに関連付けられたフラグメント </li> 
      </ul> リソースの種類を検出できない場合があります。 この場合、FILEが返されます。 </td> 
      </tr> 
      <tr> 
      <td colname="col01"> <span class="codeph"> url  </span> </td> 
      <td colname="col1"> <span class="codeph"> 文字列  </span> </td> 
      <td colname="col2"> ダウンロードされたリソースを指すURLです。 </td> 
      </tr> 
    </tbody> 
   </table>
