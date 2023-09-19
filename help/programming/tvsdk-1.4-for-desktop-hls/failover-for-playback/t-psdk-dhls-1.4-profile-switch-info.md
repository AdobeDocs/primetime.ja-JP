---
description: メディアプレーヤーが現在のプロファイルを新しいプロファイルに切り替えたとき、切り替えのタイミング、幅と高さの情報、異なるビットレートが使用された理由など、切り替えに関する情報を取得できます。
title: プロファイルの切り替えに関する情報を取得します
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# プロファイルの切り替えに関する情報を取得します{#get-information-about-profile-switch}

メディアプレーヤーが現在のプロファイルを新しいプロファイルに切り替えたとき、切り替えのタイミング、幅と高さの情報、異なるビットレートが使用された理由など、切り替えに関する情報を取得できます。

1. をリッスンします。 `ProfileEvent.PROFILE_CHANGED` イベント。

   TVSDK メディアプレーヤーは、ネットワークまたはマシンの状態が原因で、アダプティブビットレート切り替えアルゴリズムが別のプロファイルに切り替えると、このイベントをディスパッチします。 （ビットレートまたは期間が変更された場合）
1. イベントが発生したら、スイッチに関する次のプロパティを確認します。

   * `profile`：使用する新しいプロファイルの識別子。
   * `time`：切り替えが発生したストリーム時間。
   * `description`：キーと値のペアをセミコロンで区切った文字列として、ビットレートの変更理由をテキストで説明したもの。 最大 1 つを含む `Reason` 一つ `Bitrate`. 情報が利用できない場合や、ビットレートが変更されなかった場合、この文字列は空になります。

     <table id="table_E400FD9C57FF40CBAC14AF6847CD8301"> 
       <thead> 
         <tr> 
         <th colname="col1" class="entry"> キー名 </th> 
         <th colname="col2" class="entry"> 可能な値 </th> 
         </tr> 
       </thead>
       <tbody> 
         <tr> 
         <td colname="col1"> <span class="codeph"> 理由 </span> </td> 
         <td colname="col2"> 
          <ul id="ul_37DDE3F297634ED6B47DF5D73F969369"> 
          <li id="li_E374B029E1AF40689D70A9D30E057C5B">ネットワーク適応 </li> 
          <li id="li_753862EEF1C9474EA8E20C89F5EF5D8D">シーク </li> 
          <li id="li_EC14923F92CF4D11A47928A8D2DE6D8B">プロファイルはサポートされていません </li> 
          <li id="li_695AB4A89C9D4833AF6D8B6424FC912B">フェイルオーバー </li> 
          </ul> </td> 
         </tr> 
         <tr> 
         <td colname="col1"> <span class="codeph"> ビットレート </span> </td> 
         <td colname="col2"> 
          <ul id="ul_1B49BD90A91147359712E1AFD8877E23"> 
          <li id="li_1C8E593C65D34742B14A8D0EAD43E0A9"> <span class="codeph"> up </span>：ビットレートが増加しました。 </li> 
          <li id="li_B1A00E3985A849B6855E15CF70D79BB8"> <span class="codeph"> down </span>：ビットレートが減少しました。 </li> 
          </ul> </td> 
         </tr> 
       </tbody> 
       </table>

     次に、返される例を示します。 `description` 文字列：

     ```
     "Bitrate::=up;Reason::=Network Adaptation;" 
     
     "Bitrate::=down;Reason::=Failover;"
     ```

   * `width`：幅をピクセル単位で示す整数。
   * `height`：高さをピクセル単位で示す整数。

     >[!NOTE]
     >
     >幅と高さのデータは、 `RESOLUTION` タグを M3U8 マニフェスト内に追加します。 情報が M3U8 に含まれていない場合、プロファイル情報の一部ではないので、width と height の各プロパティは 0 に設定されます。

<!--<a id="example_A713D420AE2E4E3CB7B78C6BC732BE90"></a>-->

例：

```
_player.addEventListener(ProfileEvent.PROFILE_CHANGED, onProfileChange); 
private function onProfileChange(event:ProfileEvent):void { 
    _logger.info("#onProfileChange Current profile/bitrate has changed.  
      {0} for reason {1} of resolution [ {2} , {3} ]",  
      event.profile, event.description, event.width, event.height); 
}
```
