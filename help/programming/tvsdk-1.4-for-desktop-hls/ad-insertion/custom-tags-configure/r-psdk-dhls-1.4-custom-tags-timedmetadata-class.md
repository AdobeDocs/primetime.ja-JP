---
description: TVSDK がプレイリスト/マニフェスト内にサブスクライブされたタグを検出すると、プレーヤーは自動的にタグの処理を試み、 TimedMetadata オブジェクトの形式でタグを公開します。
title: 時間指定メタデータクラス
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# 時間指定メタデータクラス{#timed-metadata-class}

TVSDK がプレイリスト/マニフェスト内にサブスクライブされたタグを検出すると、プレーヤーは自動的にタグの処理を試み、 TimedMetadata オブジェクトの形式でタグを公開します。

クラスは、次の要素を提供します。

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
   <td colname="col1"><span class="codeph"> コンテンツ</span> </td> 
   <td colname="col02"> 文字列 </td> 
   <td colname="col2"> 時間指定メタデータの生のコンテンツ。 タイプが TAG の場合、値はキュー/タグの属性リスト全体を表します。 タイプ id3 の場合は null です。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> id</span> </td> 
   <td colname="col02"> 文字列 </td> 
   <td colname="col2"> 時間指定メタデータの一意の識別子。 この値は、通常、キュー/タグ ID 属性から抽出されます。 それ以外の場合は、一意のランダムな値が提供されます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> メタデータ</span> </td> 
   <td colname="col02"> メタデータ </td> 
   <td colname="col2"> プレイリスト/マニフェストカスタムタグから処理/抽出された情報。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> 名前</span> </td> 
   <td colname="col02"> 文字列 </td> 
   <td colname="col2">時間指定メタデータの名前。 タイプが <span class="codeph"> タグ</span>の値は、キュー/タグ名を表します。 タイプが <span class="codeph"> ID3</span>の場合、null です。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> 時間</span> </td> 
   <td colname="col02"> 数値 </td> 
   <td colname="col2"> この時間指定メタデータがストリーム内に存在するメインコンテンツの開始を基準とした時間の位置（ミリ秒）。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> type</span> </td> 
   <td colname="col02"> 文字列 </td> 
   <td colname="col2">時間指定メタデータのタイプ。 
    <ul id="ul_70FBFB33E9F846D8B38592560CCE9560"> 
     <li id="li_739D30561BFB4D9B97DF212E4880BA2C">TAG — 時間指定メタデータがプレイリスト/マニフェスト内のタグから作成されたことを示します。 </li> 
     <li id="li_E785E1DEF1CC4D9DBE7764E5D05EFAFC">ID3 — 時間指定メタデータがメディアストリームの ID3 タグから作成されたことを示します。 </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

<!--<a id="section_737CC47997F74F80A3C5C6171ADE120E"></a>-->

次の点に注意してください。

* TVSDK は、属性リストを自動的にキーと値のペアに抽出し、その属性をメタデータプロパティに格納します。

  >[!TIP]
  >
  >マニフェスト内のカスタムタグの複雑なデータ（特殊文字を含む文字列など）は引用符で囲む必要があります。 例：
  >
  >```
  >#EXT-CUSTOM-TAG:type=SpliceOut,ID=1,time=71819.7222,duration=30.0,url=
  >"www.example.com:8090?parameter1=xyz&parameter2=abc"
  >```
  >

* カスタムタグの形式が原因で抽出が失敗した場合、メタデータプロパティは空になり、アプリケーションは実際の情報を抽出する必要があります。 この場合、エラーはスローされません。

| 要素 | 説明 |
|---|---|
| `TAG, ID3 ID3, TAG` | 時間指定メタデータに使用できるタイプ。 |
| `public function TimedMetadata(type:String, time:Number, id:String, name:String, content:String, metadata:Metadata)` | デフォルトのコンストラクタ（time はローカルストリーム時間）です。 |
| `content:String` | この時間指定メタデータのソースタグの生のコンテンツ。 |
| `time:Number` | メインコンテンツの開始を基準とした時間の位置。このメタデータがストリーム内で挿入されます。 |
| `metadata:Metadata` | ストリームに挿入されたメタデータ。 |
| `type:String` | 時間指定メタデータのタイプを返します。 |
| `id:String` | キュー/タグ属性から抽出された ID を返します。 それ以外の場合は、一意のランダムな値が提供されます。 |
| `name:String` | キューの名前を返します。通常は、HLS タグ名です。 |
