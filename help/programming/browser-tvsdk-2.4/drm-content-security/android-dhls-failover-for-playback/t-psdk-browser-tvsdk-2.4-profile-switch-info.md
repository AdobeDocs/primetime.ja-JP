---
description: メディアプレイヤーが現在のプロファイルを新しいプロファイルに切り替えると、いつ切り替えられたか、幅と高さの情報、異なるビットレートが使用された理由など、切り替えに関する情報を取得できます。
seo-description: メディアプレイヤーが現在のプロファイルを新しいプロファイルに切り替えると、いつ切り替えられたか、幅と高さの情報、異なるビットレートが使用された理由など、切り替えに関する情報を取得できます。
seo-title: プロファイルスイッチに関する情報の取得
title: プロファイルスイッチに関する情報の取得
uuid: 0ff1aeac-882a-4209-b19f-1aa3141404d9
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---


# プロファイルスイッチ{#get-information-about-profile-switch}に関する情報を取得します

メディアプレイヤーが現在のプロファイルを新しいプロファイルに切り替えると、いつ切り替えられたか、幅と高さの情報、異なるビットレートが使用された理由など、切り替えに関する情報を取得できます。

1. `AdobePSDK.PSDKEventType.PROFILE_CHANGED`イベントをリッスンします。

   ネットワークまたはコンピューターの状態が原因で、可変ビットレート切り替えアルゴリズムが別のプロファイルに切り替わると、Browser TVSDKメディアプレイヤーがこのイベントをディスパッチします。 （ビットレートまたは期間が変更された場合）。
1. イベントが発生した場合は、次のプロパティを確認してスイッチに関する情報を確認します。

   * `profile`:使用中の新しいプロファイルの識別子。
   * `time`:切り替えが発生したストリーム時間。
   * `description`:キー/値のペアをセミコロンで区切った文字列として、ビットレートの変更理由をテキストで説明した文字列。最大1個の`Reason`と1個の`Bitrate`が含まれます。 情報が利用できない場合、またはビットレートが変更されなかった場合、この文字列は空です。

   <table id="table_E400FD9C57FF40CBAC14AF6847CD8301"> 
    <thead> 
      <tr> 
      <th colname="col1" class="entry"> キー名 </th> 
      <th colname="col2" class="entry"> 可能な値 </th> 
      </tr> 
    </thead>
    <tbody> 
      <tr> 
      <td colname="col1"> <span class="codeph"> 理由  </span> </td> 
      <td colname="col2"> 
        <ul id="ul_37DDE3F297634ED6B47DF5D73F969369"> 
        <li id="li_E374B029E1AF40689D70A9D30E057C5B">ネットワーク適応 </li> 
        <li id="li_753862EEF1C9474EA8E20C89F5EF5D8D">シーク </li> 
        <li id="li_EC14923F92CF4D11A47928A8D2DE6D8B">プロファイルがサポートされていません </li> 
        <li id="li_695AB4A89C9D4833AF6D8B6424FC912B">フェイルオーバー </li> 
        </ul> </td> 
      </tr> 
      <tr> 
      <td colname="col1"> <span class="codeph"> Bitrate  </span> </td> 
      <td colname="col2"> 
        <ul id="ul_1B49BD90A91147359712E1AFD8877E23"> 
        <li id="li_1C8E593C65D34742B14A8D0EAD43E0A9"> <span class="codeph"> 上 </span>:ビットレートが増加した </li> 
        <li id="li_B1A00E3985A849B6855E15CF70D79BB8"> <span class="codeph"> down  </span>:ビットレートが減少した </li> 
        </ul> </td> 
      </tr> 
    </tbody> 
    </table>

   返される`description`文字列の例を以下に示します。

   ```
   "Bitrate::=up;Reason::=Network Adaptation;" 
   
   "Bitrate::=down;Reason::=Failover;"
   ```

   * `width`:幅をピクセル単位で示す整数です。
   * `height`:高さをピクセル単位で示す整数です。

   >[!NOTE]
   >
   >幅と高さのデータは、M3U8マニフェストの`RESOLUTION`タグに含まれている場合にのみ使用できます。 情報がM3U8に含まれていない場合、widthとheightの各プロパティは0に設定されます。これらのプロパティはプロファイル情報の一部ではないためです。
