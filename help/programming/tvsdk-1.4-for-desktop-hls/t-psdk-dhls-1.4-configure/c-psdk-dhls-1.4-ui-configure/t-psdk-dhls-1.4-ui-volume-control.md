---
description: サウンドボリュームのユーザインターフェイスコントロールを設定できます。
title: ボリューム制御を提供
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---

# ボリューム制御を提供{#provide-volume-control}

サウンドボリュームのユーザインターフェイスコントロールを設定できます。

1. MediaPlayer インスタンスがこのコマンドで有効なステータスになるのを待ちます。

   RELEASED を除く状態はすべて有効です。
1. のボリュームセットメソッドを呼び出します。 `MediaPlayer` インスタンス：オーディオのボリュームを設定します。

   ```
   public function set volume(value:Number):void
   ```

   ボリュームの値は、要求されたボリュームを最大ボリュームの比率で表します。0 は無音、1 は最大ボリュームです。

   <table id="table_144A2B1260374FBE8D976194F602DDC7"> 
   <thead> 
   <tr> 
      <th colname="col1" class="entry"> 指定したボリュームが </th> 
      <th colname="col2" class="entry"> 結果のボリュームは次のようになります。 </th> 
   </tr> 
   </thead>
   <tbody> 
   <tr> 
      <td colname="col1"> 0 未満 </td> 
      <td colname="col2"> 0 </td> 
   </tr> 
   <tr> 
      <td colname="col1"> 0 ～ 1 </td> 
      <td colname="col2"> 指定したボリューム </td> 
   </tr> 
   <tr> 
      <td colname="col1"> 1 より大きい </td> 
      <td colname="col2"> 値を 100 で割って、次の値のいずれかに設定します。 
      <ul id="ul_8C2282F0EDC44A408820F5768709214F"> 
      <li id="li_B00BC6F4812D4000891358F762C8E492">0 ～ 1 の範囲の場合の結果 </li> 
      <li id="li_03B7F30662554F299320040CAC2DEB7A">結果が 1 より大きい場合は 1 </li> 
      </ul> <p>ヒント：このロジックでは、クライアントから提供される値を、以前のバージョンの 
      <span class="codeph">frases/primetime-sdk-name</span>ボリューム値の範囲は 0 ～ 100 です。 </p> </td> 
   </tr> 
   </tbody> 
   </table>
