---
description: 様々な広告シグナリングモードと広告メタデータの組み合わせを使用して、VODストリームの時間範囲をマーク、削除および置換できます。 シグナリングモードとメタデータの組み合わせが異なると、動作が異なります。
seo-description: 様々な広告シグナリングモードと広告メタデータの組み合わせを使用して、VODストリームの時間範囲をマーク、削除および置換できます。 シグナリングモードとメタデータの組み合わせが異なると、動作が異なります。
seo-title: 広告シグナリングモードと広告メタデータの組み合わせからの広告挿入および削除に対する影響
title: 広告シグナリングモードと広告メタデータの組み合わせからの広告挿入および削除に対する影響
uuid: c2ae8148-889d-46ae-848a-5f45d993a0e2
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# 広告シグナリングモードと広告メタデータの組み合わせからの広告挿入および削除に対する影響{#effect-on-ad-insertion-and-deletion-from-ad-signaling-mode-and-ad-metadata-combinations}

様々な広告シグナリングモードと広告メタデータの組み合わせを使用して、VODストリームの時間範囲をマーク、削除および置換できます。 シグナリングモードとメタデータの組み合わせが異なると、動作が異なります。

>[!NOTE]
>
>時間範囲と広告シグナリングモードの間に競合がある場合、TVSDKは時間範囲を優先します。

**表4:シグナリングモード/メタデータの組み合わせの動作**

<table>  
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
   <td> <b>サーバーマップ</b> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
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
    <ul> 
     <li><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE), </span> </li> 
     <li><span class="codeph"> PlacementInfo (Type.SERVER_MAP, Mode.INSERT)</span> </li> 
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
   <td> <b>マニフェストキュー</b> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
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
    <ul> 
     <li><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.DELETE)</span> </li> 
     <li><span class="codeph"> PlacementInfo (Type.PRE_ROLL, Mode.INSERT)</span> </li> 
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
   <td> <b>カスタム時間範囲</b> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
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
   <td> <b>未設定（デフォルト）</b> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
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

