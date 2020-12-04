---
description: TVSDKは、プレイリスト/マニフェスト内にサブスクライブされたタグを検出すると、タグを自動的に処理して、TimedMetadataオブジェクトの形式で公開しようとします。
seo-description: TVSDKは、プレイリスト/マニフェスト内にサブスクライブされたタグを検出すると、タグを自動的に処理して、TimedMetadataオブジェクトの形式で公開しようとします。
seo-title: 時間指定メタデータクラス
title: 時間指定メタデータクラス
uuid: 827a3bcf-a584-4032-aa19-4fc7730778cc
translation-type: tm+mt
source-git-commit: 5df9a8b98baaf1cd1803581d2b60c7ed4261a0e8
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---


# 時間指定メタデータクラス{#timed-metadata-class}

TVSDKは、プレイリスト/マニフェスト内にサブスクライブされたタグを検出すると、タグを自動的に処理して、TimedMetadataオブジェクトの形式で公開しようとします。

このクラスは次の要素を提供します。

<table id="table_FFC56AC5B1E04DA99C9309C0223ABA90"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> プロパティ </th> 
   <th colname="col02" class="entry"> タイプ </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> content</span> </td> 
   <td colname="col02"> 文字列 </td> 
   <td colname="col2"> 時間指定メタデータの生コンテンツ。 typeがTAGの場合、値はキュー/タグの属性リスト全体を表します。 タイプid ID3の場合はnullです。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> id</span> </td> 
   <td colname="col02"> 文字列 </td> 
   <td colname="col2"> 時間指定メタデータを表す一意の識別子です。 この値は通常、キュー/タグID属性から抽出されます。 それ以外の場合は、一意のランダム値が提供されます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> metadata</span> </td> 
   <td colname="col02"> メタデータ </td> 
   <td colname="col2"> プレイリスト/マニフェストカスタムタグから処理/抽出された情報。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> name</span> </td> 
   <td colname="col02"> 文字列 </td> 
   <td colname="col2">時間指定メタデータの名前。 タイプが<span class="codeph"> TAG</span>の場合、値はキュー/タグ名を表します。 タイプが<span class="codeph"> ID3</span>の場合はnullです。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> time</span> </td> 
   <td colname="col02"> 数値 </td> 
   <td colname="col2"> この時間指定メタデータがストリーム内で存在するメインコンテンツの開始に対する位置（ミリ秒）。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> type</span> </td> 
   <td colname="col02"> 文字列 </td> 
   <td colname="col2">時間指定メタデータのタイプ。 
    <ul id="ul_70FBFB33E9F846D8B38592560CCE9560"> 
     <li id="li_739D30561BFB4D9B97DF212E4880BA2C">TAG — 時間指定メタデータがプレイリスト/マニフェスト内のタグから作成されたことを示します。 </li> 
     <li id="li_E785E1DEF1CC4D9DBE7764E5D05EFAFC">ID3 — 時間指定メタデータがメディアストリームのID3タグから作成されたことを示します。 </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

<!--<a id="section_737CC47997F74F80A3C5C6171ADE120E"></a>-->

次の点に注意してください。

* TVSDKは、属性リストを自動的にキーと値のペアに抽出し、属性をメタデータプロパティに保存します。

   >[!TIP]
   >
   >マニフェスト内のカスタムタグに含まれる複雑なデータ（特殊文字を含む文字列など）は、引用符で囲む必要があります。 例：
   >
   >
   ```
   >#EXT-CUSTOM-TAG:type=SpliceOut,ID=1,time=71819.7222,duration=30.0,url=
   >"www.example.com:8090?parameter1=xyz&parameter2=abc"
   >```

* カスタムタグの形式が原因で抽出が失敗した場合、メタデータプロパティは空になり、アプリケーションで実際の情報を抽出する必要があります。 この場合、エラーはスローされません。

| 要素 | 説明 |
|---|---|
| `TAG, ID3 ID3, TAG` | 時間指定メタデータに使用できるタイプ。 |
| `public function TimedMetadata(type:String, time:Number, id:String, name:String, content:String, metadata:Metadata)` | デフォルトコンストラクター（timeはローカルストリーム時間です）。 |
| `content:String` | この時間指定メタデータのソースタグの生コンテンツ。 |
| `time:Number` | このメタデータが挿入されるストリーム内での位置を、メインコンテンツの開始を基準とした時間で表します。 |
| `metadata:Metadata` | ストリームに挿入されるメタデータ。 |
| `type:String` | 時間指定メタデータのタイプを返します。 |
| `id:String` | キュー/タグ属性から抽出されたIDを返します。 それ以外の場合は、一意のランダム値が提供されます。 |
| `name:String` | キューの名前を返します。通常はHLSタグ名です。 |

