---
description: サウンドのボリュームを制御するユーザインターフェイスを設定できます。
seo-description: サウンドのボリュームを制御するユーザインターフェイスを設定できます。
seo-title: ボリューム制御の提供
title: ボリューム制御の提供
uuid: c51e99b6-efd1-414e-9ef7-77bd53e0d6c0
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# ボリューム制御の提供{#provide-volume-control}

サウンドのボリュームを制御するユーザインターフェイスを設定できます。

1. MediaPlayerインスタンスがこのコマンドの有効なステータスになるまで待ちます。

   RELEASED以外の状態はすべて有効です。
1. インスタンスでボリュームセットメソッドを呼び出 `MediaPlayer` して、オーディオのボリュームを設定します。

   ```
   public function set volume(value:Number):void
   ```

   ボリュームの値は、要求されたボリュームを最大ボリュームの割合で表します。0は無音、1は最大ボリュームです。

   <table id="table_144A2B1260374FBE8D976194F602DDC7"> 
   <thead> 
   <tr> 
      <th colname="col1" class="entry"> 指定したボリュームが </th> 
      <th colname="col2" class="entry"> 結果のボリュームは、 </th> 
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
      </ul> <p>ヒント： このロジックは、ボリュームの値の範囲が0 ～ 100のfrases/ <span class="codeph">primetime-sdk-name</span>（以前のバージョン）に基づいて、クライアントから提供される値を処理します。 </p> </td> 
   </tr> 
   </tbody> 
   </table>
