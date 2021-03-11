---
description: ブラウザーTVSDKは、プレイリスト/マニフェスト内にサブスクライブされたタグを検出すると、タグを自動的に処理して、TimedMetadataオブジェクトとして公開しようとします。
title: 時間指定メタデータクラス
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---


# 時間指定メタデータクラス{#timed-metadata-class}

ブラウザーTVSDKは、プレイリスト/マニフェスト内にサブスクライブされたタグを検出すると、タグを自動的に処理して、TimedMetadataオブジェクトとして公開しようとします。

`TimedMetadata`クラスは次の要素を提供します。

<table id="table_5827A0626EDC45F68DC3E7644F3EFF69"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> プロパティ </th> 
   <th colname="col02" class="entry"> タイプ </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>type </p> </td> 
   <td colname="col02"> <p><span class="codeph"> TimedMetadataType</span> </p> </td> 
   <td colname="col2"> <p>時間指定メタデータのタイプを次に示します。 
     <ul id="ul_E79C375A54C64BF09A927EE8983E98E3"> 
      <li id="li_F1907521CDBE47E282A87AF0A7A1477A">TAG — 時間指定メタデータは、プレイリスト/マニフェスト内のタグから作成されました。 </li> 
      <li id="li_5B0C0B0F247144709F86E6654A5AB500">ID3 — 時間指定メタデータは、メディアストリームのID3タグから作成されました。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>time </p> </td> 
   <td colname="col02"> <p>数値 </p> </td> 
   <td colname="col2"> <p>この時間指定メタデータがストリーム内で存在するメインコンテンツの開始に対するローカル時間の位置（ミリ秒）。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>id </p> </td> 
   <td colname="col02"> <p>文字列 </p> </td> 
   <td colname="col2"> <p>時間指定メタデータの一意の識別子。 </p> <p>通常、キュー/タグID属性（存在する場合）から抽出されます。 それ以外の場合は、一意のランダム値になります。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>name </p> </td> 
   <td colname="col02"> <p>数値 </p> </td> 
   <td colname="col2"> <p>時間指定メタデータの名前。 </p> <p>タイプがTAGの場合、値はキュー/タグ名を表します。 typeがID3の場合、値はnullです。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>content </p> </td> 
   <td colname="col02"> <p>文字列 </p> </td> 
   <td colname="col2"> <p>時間指定メタデータの生コンテンツ。 </p> <p>typeがTAGの場合、値はキュー/タグの属性リスト全体を表します。 タイプid ID3の場合、値はnullです。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>metadata </p> </td> 
   <td colname="col02"> <p><span class="codeph"> メタデータ</span> </p> </td> 
   <td colname="col2"> <p>プレイリスト/マニフェストカスタムタグから処理/抽出された情報。 </p> </td> 
  </tr> 
 </tbody> 
</table>

