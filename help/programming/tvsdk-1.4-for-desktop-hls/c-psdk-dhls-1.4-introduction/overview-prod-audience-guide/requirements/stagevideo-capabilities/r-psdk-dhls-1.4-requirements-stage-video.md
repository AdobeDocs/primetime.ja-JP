---
description: GPU（ハードウェア）アクセラレーションをサポートするデバイスでは、flash.media.StageVideoオブジェクトを使用して、デバイスのハードウェア上でビデオを直接処理できます。
seo-description: GPU（ハードウェア）アクセラレーションをサポートするデバイスでは、flash.media.StageVideoオブジェクトを使用して、デバイスのハードウェア上でビデオを直接処理できます。
seo-title: StageVideoの最小要件
title: StageVideoの最小要件
uuid: 8916dbac-33e0-4efd-8105-9ddbc85f0a3f
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---


# StageVideoの最小要件{#stagevideo-minimum-requirements}

GPU（ハードウェア）アクセラレーションをサポートするデバイスでは、flash.media.StageVideoオブジェクトを使用して、デバイスのハードウェア上でビデオを直接処理できます。

<!--<a id="section_64DDAA8DB215493E8A7CA6636819D350"></a>-->

様々な要因の組み合わせによって、`StageVideo`をいつ、どのように使用できるかが決まります。 次の表に、StageVideoの使用に関連する要件の一部と制限のスナップショットを示します。 これらの要件と制限は、変更される場合があります。

<table id="table_882F4462A5AE47E28A60A39D112164A7"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> プラットフォーム </th> 
   <th colname="col2" class="entry"> WindowsとMac OS </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> Flashプレーヤー </td> 
   <td colname="col2"> 
    <ul id="ul_s42_lm2_jp"> 
     <li id="li_308FA9EC206B437A9EE04C29F9480B73">Flash10.1以降 </li> 
     <li id="li_5898EDB0D12A43389076BCC7F4A27A0A">ソフトウェアへのフォールバック機能の場合は、Flash15以降 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1">ブラウザーと<span class="codeph"> wmode</span>設定 </td> 
   <td colname="col2"> <p><b>Flash15で</b>、 <span class="codeph"> wmode=</span> opaquesoを設定し、HTMLオーバーレイを使用できるようにします。 </p> <p>次のブラウザは、現在、ハードウェアアクセラレーションをサポートしていません。 
     <ul id="ul_frv_ykf_jp"> 
      <li id="li_3D407A61FEE042A9B85A6EFACA6D7719">Microsoft Windows上のMozilla Firefox </li> 
      <li id="li_39B85AC352564DA8B86EA826638F1F4B">Google Chrome 26より前のバージョン、およびWindows XPおよびVista上の任意のバージョンのChrome </li> 
      <li id="li_0042BA6070C849E6B7C4B4BF4333F712">Microsoft Internet Explorer（全バージョン） </li> 
     </ul>その他のブラウザーとOSの組み合わせでは、ハードウェアアクセラレーションにアクセスできない場合があります。 これらのシナリオでは、<span class="codeph"> StageVideo</span>がソフトウェアにフォールバックされ、パフォーマンスに悪影響が出ます。 </p> <p><b>Flash14以前では</b>、ブラウザーがハードウェアアクセラレーションをサポートしていない場合、FlashプレイヤーはGPUに直接レンダリングできますが、 <span class="codeph"> wmode=</span> directに設定してこのレンダリングを有効にします。 <p>ヒント： 2009より古いGPUドライバーは、ハードウェアアクセラレーションをサポートしていない可能性があるので、アップデートが必要になる場合があります。 </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> NetStreamオブジェクト </td> 
   <td colname="col2"><span class="codeph"> StageVideoEvent.RENDER_STATE</span>イベントは、<span class="codeph"> NetStream</span>オブジェクトを<span class="codeph"> StageVideo</span>オブジェクトにアタッチしない限り、ディスパッチされません。 </td> 
  </tr> 
 </tbody> 
</table>

