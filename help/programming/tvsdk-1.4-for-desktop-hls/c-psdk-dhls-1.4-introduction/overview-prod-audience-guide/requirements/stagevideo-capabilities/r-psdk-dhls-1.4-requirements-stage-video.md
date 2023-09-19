---
description: GPU（ハードウェア）アクセラレーションをサポートするデバイスでは、 flash.media.StageVideo オブジェクトを使用して、デバイスのハードウェア上で直接ビデオを処理できます。
title: StageVideo の最小要件
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---

# StageVideo の最小要件{#stagevideo-minimum-requirements}

GPU（ハードウェア）アクセラレーションをサポートするデバイスでは、 flash.media.StageVideo オブジェクトを使用して、デバイスのハードウェア上で直接ビデオを処理できます。

<!--<a id="section_64DDAA8DB215493E8A7CA6636819D350"></a>-->

様々な要因の組み合わせによって、使用するタイミングと方法が決まります `StageVideo`. 次の表に、StageVideo の使用に関連するいくつかの要件と制限のスナップショットを示します。 これらの要件や制限は、変更される場合があります。

<table id="table_882F4462A5AE47E28A60A39D112164A7"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Platform </th> 
   <th colname="col2" class="entry"> Windows とMac OS </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> Flashプレーヤー </td> 
   <td colname="col2"> 
    <ul id="ul_s42_lm2_jp"> 
     <li id="li_308FA9EC206B437A9EE04C29F9480B73">少なくともFlash10.1 以降 </li> 
     <li id="li_5898EDB0D12A43389076BCC7F4A27A0A">ソフトウェアへのフォールバック機能の場合、Flash15 以降 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1">ブラウザーと <span class="codeph"> wmode</span> 設定 </td> 
   <td colname="col2"> <p><b>Flash15 で</b>，設定 <span class="codeph"> wmode=opaque</span> そのため、HTMLオーバーレイを使用できます。 </p> <p>現在、次のブラウザーはハードウェアアクセラレーションをサポートしていません。 
     <ul id="ul_frv_ykf_jp"> 
      <li id="li_3D407A61FEE042A9B85A6EFACA6D7719">Mozilla Firefox(Microsoft Windows 上 ) </li> 
      <li id="li_39B85AC352564DA8B86EA826638F1F4B">Google Chrome（26 より前）および Windows XP および Vista 上の任意のバージョンの Chrome </li> 
      <li id="li_0042BA6070C849E6B7C4B4BF4333F712">Microsoft Internet Explorer （すべてのバージョン） </li> 
     </ul>その他のブラウザーと OS の組み合わせでは、ハードウェアアクセラレーションへのアクセスが妨げられる場合があります。 このシナリオでは、 <span class="codeph"> StageVideo</span> パフォーマンスに悪影響を及ぼすソフトウェアにフォールバックします。 </p> <p><b>Flash14 以前</b>ブラウザーがハードウェアアクセラレーションをサポートしていない場合、Flashプレーヤーは GPU に直接レンダリングできますが、設定は可能です <span class="codeph"> wmode=direct</span> このレンダリングを有効にします。 <p>ヒント： 2009 より古い GPU ドライバは、ハードウェアアクセラレーションのサポートが不足している可能性があるので、アップデートが必要になる場合があります。 </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> NetStream オブジェクト </td> 
   <td colname="col2">The <span class="codeph"> StageVideoEvent.RENDER_STATE</span> イベントは、 <span class="codeph"> NetStream</span> オブジェクトを <span class="codeph"> StageVideo</span> オブジェクト。 </td> 
  </tr> 
 </tbody> 
</table>
