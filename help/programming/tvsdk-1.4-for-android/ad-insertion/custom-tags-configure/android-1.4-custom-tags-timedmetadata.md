---
description: TVSDKは、プレイリスト/マニフェスト内にサブスクライブされたタグを検出すると、タグを自動的に処理して、TimedMetadataオブジェクトの形式で公開しようとします。
title: 時間指定メタデータクラス
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '358'
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
   <td colname="col1"> <span class="codeph"> id  </span> </td> 
   <td colname="col02"> long </td> 
   <td colname="col2"> 時間指定メタデータを表す一意の識別子です。 この値は通常、キュー/タグID属性から抽出されます。 それ以外の場合は、一意のランダム値が提供されます。 <span class="codeph"> getId </span>を使用します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> metadata  </span> </td> 
   <td colname="col02"> メタデータ </td> 
   <td colname="col2"> プレイリスト/マニフェストカスタムタグから処理/抽出された情報。 <span class="codeph"> getMetadata </span>を使用します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> name </span> </td> 
   <td colname="col02"> 文字列 </td> 
   <td colname="col2"> 時間指定メタデータの名前。 タイプが<span class="codeph"> TAG </span>の場合、値はキュー/タグ名を表します。 型が<span class="codeph"> ID3 </span>の場合、値はnullです。 <span class="codeph"> getName </span>を使用します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> time  </span> </td> 
   <td colname="col02"> long </td> 
   <td colname="col2"> この時間指定メタデータがストリーム内で存在するメインコンテンツの開始に対する位置（ミリ秒）。 <span class="codeph"> getTime </span>を使用します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> type  </span> </td> 
   <td colname="col02"> タイプ </td> 
   <td colname="col2"> 時間指定メタデータのタイプ。 <span class="codeph"> getType </span>を使用します。 
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
   >#EXT-CUSTOM-TAG:type=SpliceOut,ID=1,time=71819.7222,duration=30.0, 
   >url="www.example.com:8090?parameter1=xyz&parameter2=abc"
   >```

* カスタムタグの形式が原因で抽出が失敗した場合、メタデータプロパティは空になり、アプリケーションで実際の情報を抽出する必要があります。 この場合、エラーはスローされません。

| 要素 | 説明 |
|---|---|
| `public enum Type { TAG, ID3}` | 時間指定メタデータに使用できるタイプ。 |
| `public TimedMetadata(Type type, long time, long id, String name, Metadata metadata);` | デフォルトコンストラクター（timeはローカルストリーム時間です）。 |
| `public long getTime();` | このメタデータが挿入されるストリーム内での位置を、メインコンテンツの開始を基準とした時間で表します。 |
| `public Metadata getMetadata();` | ストリームに挿入されるメタデータ。 |
| `public Type getType();` | 時間指定メタデータのタイプを返します。 |
| `public long getId();` | キュー/タグ属性から抽出されたIDを返します。 それ以外の場合は、一意のランダム値が提供されます。 |
| `public String getName();` | キューの名前を返します。通常はHLSタグ名です。 |

