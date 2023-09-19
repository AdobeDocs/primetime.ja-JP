---
description: 異なる広告シグナリングモードと広告メタデータの組み合わせを使用して、VOD ストリーム内の時間範囲をマーク、削除および置換できます。 シグナリングモードとメタデータの組み合わせが異なると、動作が異なります。
title: 広告シグナリングモードと広告メタデータの組み合わせからの広告挿入および削除に対する影響
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# 広告シグナリングモードと広告メタデータの組み合わせからの広告挿入および削除に対する影響{#effect-on-ad-insertion-and-deletion-from-ad-signaling-mode-and-ad-metadata-combinations}

異なる広告シグナリングモードと広告メタデータの組み合わせを使用して、VOD ストリーム内の時間範囲をマーク、削除および置換できます。 シグナリングモードとメタデータの組み合わせが異なると、動作が異なります。

>[!NOTE]
>
>時間範囲と広告シグナリングモードの間に競合が発生した場合、 TVSDK は時間範囲を優先します。

**表 3：シグナリングモード/メタデータの組み合わせの動作**

<table>  
 <thead> 
  <tr> 
   <th class="entry"> 広告シグナリングモード </th> 
   <th class="entry"> 広告メタデータ </th> 
   <th class="entry"> 作成されたリゾルバー </th> 
   <th class="entry"><span class="codeph"> PlacementInformations</span> 作成済み </th> 
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
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.Mode)</span> </td> 
   <td> 範囲が削除されました </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> 削除、Auditude </td> 
   <td> 削除、Auditude </td> 
   <td> 
    <ul> 
     <li><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.Mode), </span> </li> 
     <li><span class="codeph"> PlacementInfo (Type.SERVER_MAP, Mode.INSERT)</span> </li> 
    </ul> </td> 
   <td> 範囲が削除され、広告が挿入されました </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Auditude </td> 
   <td> Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.SERVER_MAP, Mode.INSERT)</span> </td> 
   <td> 広告が挿入されました </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> 置換、Auditude </td> 
   <td> 削除、Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.Mode), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)</span> </td> 
   <td> 範囲が置き換えられました </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> トンボ </td> 
   <td> CustomAd </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> 範囲がマークされました </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> マーク、Auditude </td> 
   <td> CustomAd、Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> 範囲がマークされ、広告は挿入されません </td> 
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
   <td> 広告が挿入されました </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> 削除、Auditude </td> 
   <td> 削除、Auditude </td> 
   <td> 
    <ul> 
     <li><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.Mode)</span> </li> 
     <li><span class="codeph"> PlacementInfo (Type.PRE_ROLL, Mode.INSERT)</span> </li> 
    </ul> </td> 
   <td> 範囲が削除され、広告が挿入されました </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> マーク、Auditude </td> 
   <td> マーク、Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> 範囲がマークされ、広告は挿入されません </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> 削除 </td> 
   <td> 削除 </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.Mode)</span> </td> 
   <td> 範囲が削除されました </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> トンボ </td> 
   <td> CustomAd </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> 範囲がマークされました </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> 置換、Auditude </td> 
   <td> 削除、Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.Mode), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)</span> </td> 
   <td> 範囲が置き換えられました </td> 
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
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.Mode)</span> </td> 
   <td> 範囲が削除されました </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> 削除、Auditude </td> 
   <td> 削除、Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.Mode)</span> </td> 
   <td> 範囲が削除され、広告が挿入されません </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Auditude </td> 
   <td> Auditude </td> 
   <td> なし </td> 
   <td> 広告が挿入されていません </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> 置換、Auditude </td> 
   <td> 削除、Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.Mode), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)</span> </td> 
   <td> 範囲が広告で置き換えられました </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> トンボ </td> 
   <td> CustomAd </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> 範囲がマークされました </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> マーク、Auditude </td> 
   <td> カスタム広告、Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> 範囲がマークされ、広告は挿入されません </td> 
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
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.Mode)</span> </td> 
   <td> 範囲が削除されました </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> 削除、Auditude </td> 
   <td> 削除、Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.Mode), PlacementInfo (Type.SERVER_MAP, Mode.INSERT)</span> </td> 
   <td> 範囲が削除され、広告が挿入されました </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> Auditude </td> 
   <td> Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.SERVER_MAP, Mode.INSERT)</span> </td> 
   <td> 広告が挿入されました </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> 置換、Auditude </td> 
   <td> 削除、Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.Mode), PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.REPLACE)</span> </td> 
   <td> 範囲が広告で置き換えられました </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> トンボ </td> 
   <td> CustomAd </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> 範囲がマークされました </td> 
  </tr> 
  <tr> 
   <td></td> 
   <td> マーク、Auditude </td> 
   <td> CustomAd、Auditude </td> 
   <td><span class="codeph"> PlacementInfo (Type.CUSTOM_TIME_RANGE, Mode.MARK)</span> </td> 
   <td> 範囲がマークされました </td> 
  </tr> 
 </tbody> 
</table>
