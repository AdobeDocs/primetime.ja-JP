---
description: サウンドの音量を制御するユーザインターフェイスを設定できます。
title: ボリューム制御の提供
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---


# ボリューム制御{#provide-volume-control}を提供

サウンドの音量を制御するユーザインターフェイスを設定できます。

1. MediaPlayerインスタンスがこのコマンドに対して有効なステータスになるまで待ちます。

   RELEASED以外の状態はすべて有効です。
1. `MediaPlayer`インスタンスのボリューム設定メソッドを呼び出して、オーディオのボリュームを設定します。

   ```
   public function set volume(value:Number):void
   ```

   ボリュームの値は、要求されたボリュームを最大ボリュームの割合で表します。0は無音、1は最大です。

   <table id="table_144A2B1260374FBE8D976194F602DDC7"> 
   <thead> 
   <tr> 
      <th colname="col1" class="entry"> 指定したボリュームが </th> 
      <th colname="col2" class="entry"> 結果のボリュームは </th> 
   </tr> 
   </thead>
   <tbody> 
   <tr> 
      <td colname="col1"> 0未満 </td> 
      <td colname="col2"> 0 </td> 
   </tr> 
   <tr> 
      <td colname="col1"> 0 ～ 1 </td> 
      <td colname="col2"> 指定したボリューム </td> 
   </tr> 
   <tr> 
      <td colname="col1"> 1より大きい </td> 
      <td colname="col2"> 値を100で割って、次のいずれかの値に設定します。 
      <ul id="ul_8C2282F0EDC44A408820F5768709214F"> 
      <li id="li_B00BC6F4812D4000891358F762C8E492">0 ～ 1の場合の結果 </li> 
      <li id="li_03B7F30662554F299320040CAC2DEB7A">結果が1より大きい場合は1 </li> 
      </ul> <p>ヒント： このロジックは、 
      <span class="codeph">frases/primetime-sdk-name</span>。ボリューム値の範囲は0 ～ 100です。 </p> </td> 
   </tr> 
   </tbody> 
   </table>
