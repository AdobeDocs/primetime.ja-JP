---
description: 様々な広告シグナリングモードと広告メタデータの組み合わせを使用して、VODストリームの時間範囲をマーク、削除および置換できます。 シグナリングモードとメタデータの組み合わせが異なると、動作が異なります。
seo-description: 様々な広告シグナリングモードと広告メタデータの組み合わせを使用して、VODストリームの時間範囲をマーク、削除および置換できます。 シグナリングモードとメタデータの組み合わせが異なると、動作が異なります。
seo-title: 広告シグナリングモードと広告メタデータの組み合わせからの広告挿入および削除に対する影響
title: 広告シグナリングモードと広告メタデータの組み合わせからの広告挿入および削除に対する影響
uuid: 7b2a5588-110d-4ce5-aa9c-706d357f211d
translation-type: tm+mt
source-git-commit: 21d1eae53cea303221de00765724e787cf6e84ef

---


# 広告シグナリングモードと広告メタデータの組み合わせからの広告挿入および削除に対する影響 {#effect-on-ad-insertion-and-deletion-from-ad-signaling-mode-and-ad-metadata-combinations}

様々な広告シグナリングモードと広告メタデータの組み合わせを使用して、VODストリームの時間範囲をマーク、削除および置換できます。 シグナリングモードとメタデータの組み合わせが異なると、動作が異なります。

>[!TIP]
>
>時間範囲と広告シグナリングモードの間に競合がある場合、TVSDKは時間範囲を優先します。

次の表に、シグナリングモードとメタデータの組み合わせの動作の詳細を示します。

<table id="table_6044AA1ACFA244FA814EA2D0766C6D12"> 
 <thead> 
  <tr> 
   <th class="entry"> 広告シグナリングモード </th> 
   <th class="entry"> 広告メタデータ </th> 
   <th class="entry"> 作成されたリゾルバー </th> 
   <th class="entry"><span class="codeph"> 作成されたPlacementInformations</span> </th> 
   <th class="entry"> 結果の動作 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="1"> <p><b>サーバーマップ</b> </p> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td> 削除 </td> 
   <td> 削除 </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)</span> </td> 
   <td> 範囲の削除 </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Delete、Auditude </td> 
   <td> Delete、Auditude </td> 
   <td> 
    <ul id="ul_E0A2F885E93B4D23A486C37B305E17D8"> 
     <li id="li_D977B398D3904A44AFEC4B05AB0E3340"><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), </span> </li> 
     <li id="li_439886CB38AA46239C2E40352443888A"><span class="codeph"> PlacementInfo (Type.SERVER_MAP, Mode.INSERT)</span> </li> 
    </ul> </td> 
   <td> 範囲の削除、広告の挿入 </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Auditude </td> 
   <td> Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.SERVER_MAP, Mode.INSERT)</span> </td> 
   <td> 広告の挿入 </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Replace、Auditude </td> 
   <td> Delete、Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)、PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)</span> </td> 
   <td> 範囲の置換 </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> マーク </td> 
   <td> CustomAd </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> 範囲がマークされる </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Mark、Auditude </td> 
   <td> CustomAd、Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> 範囲がマークされ、広告が挿入されない </td> 
  </tr> 
  <tr> 
   <td colname="1"> <p><b>マニフェストキュー</b> </p> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Auditude </td> 
   <td> Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.PRE_ROLL, Mode.INSERT)</span> </td> 
   <td> 広告の挿入 </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Delete、Auditude </td> 
   <td> Delete、Auditude </td> 
   <td> 
    <ul id="ul_2DD298538E9344B9BAB882485BB57747"> 
     <li id="li_F39A69EFA7ED45C18978A2C462AF7641"><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)</span> </li> 
     <li id="li_8CCDA3B1C63F4BC396F28F443D8C42F8"><span class="codeph"> PlacementInfo (Type.PRE_ROLL, Mode.INSERT)</span> </li> 
    </ul> </td> 
   <td> 範囲の削除、広告の挿入 </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Mark、Auditude </td> 
   <td> Mark、Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> 範囲がマークされ、広告が挿入されない </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> 削除 </td> 
   <td> 削除 </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)</span> </td> 
   <td> 範囲の削除 </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> マーク </td> 
   <td> CustomAd </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> 範囲がマークされる </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Replace、Auditude </td> 
   <td> Delete、Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)、PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)</span> </td> 
   <td> 範囲の置換 </td> 
  </tr> 
  <tr> 
   <td colname="1"> <p><b>カスタム時間範囲</b> </p> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> 削除 </td> 
   <td> 削除 </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)</span> </td> 
   <td> 範囲の削除 </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Delete、Auditude </td> 
   <td> Delete、Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)</span> </td> 
   <td> 範囲が削除され、広告が挿入されない </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Auditude </td> 
   <td> Auditude </td> 
   <td> なし </td> 
   <td> 広告は挿入されません </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Replace、Auditude </td> 
   <td> Delete、Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)、PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)</span> </td> 
   <td> 範囲が広告で置換される </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> マーク </td> 
   <td> CustomAd </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> 範囲がマークされる </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Mark、Auditude </td> 
   <td> カスタム広告、Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> 範囲がマークされ、広告が挿入されない </td> 
  </tr> 
  <tr> 
   <td colname="1"> <p><b>未設定（デフォルト）</b> </p> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> 削除 </td> 
   <td> 削除 </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)</span> </td> 
   <td> 範囲の削除 </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Delete、Auditude </td> 
   <td> Delete、Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)、PlacementInfo (Type.SERVER_MAP, Mode.INSERT)</span> </td> 
   <td> 範囲の削除、広告の挿入 </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Auditude </td> 
   <td> Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.SERVER_MAP, Mode.INSERT)</span> </td> 
   <td> 広告の挿入 </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Replace、Auditude </td> 
   <td> Delete、Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)、PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)</span> </td> 
   <td> 範囲が広告で置換される </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> マーク </td> 
   <td> CustomAd </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> 範囲がマークされる </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Mark、Auditude </td> 
   <td> CustomAd、Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> 範囲がマークされる </td> 
  </tr> 
 </tbody> 
</table>

