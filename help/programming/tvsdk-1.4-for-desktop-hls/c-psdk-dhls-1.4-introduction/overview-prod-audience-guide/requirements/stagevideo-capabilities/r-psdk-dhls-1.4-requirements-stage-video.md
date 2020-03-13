---
description: GPU（ハードウェア）アクセラレーションをサポートするデバイスでは、flash.media.StageVideoオブジェクトを使用して、デバイスのハードウェア上でビデオを直接処理できます。
seo-description: GPU（ハードウェア）アクセラレーションをサポートするデバイスでは、flash.media.StageVideoオブジェクトを使用して、デバイスのハードウェア上でビデオを直接処理できます。
seo-title: StageVideoの最小要件
title: StageVideoの最小要件
uuid: 8916dbac-33e0-4efd-8105-9ddbc85f0a3f
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# StageVideoの最小要件{#stagevideo-minimum-requirements}

GPU（ハードウェア）アクセラレーションをサポートするデバイスでは、flash.media.StageVideoオブジェクトを使用して、デバイスのハードウェア上でビデオを直接処理できます。

<!--<a id="section_64DDAA8DB215493E8A7CA6636819D350"></a>-->

様々な要因の組み合わせによって、使用するタイミングと方法が決まりま `StageVideo`す。 次の表に、StageVideoの使用に関連する要件と制限の一部のスナップショットを示します。 これらの要件と制限は、変更される可能性があります。

<table id="table_882F4462A5AE47E28A60A39D112164A7"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> プラットフォーム </th> 
   <th colname="col2" class="entry"> WindowsとMac OS </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> Flash Player </td> 
   <td colname="col2"> 
    <ul id="ul_s42_lm2_jp"> 
     <li id="li_308FA9EC206B437A9EE04C29F9480B73">Flash 10.1以降 </li> 
     <li id="li_5898EDB0D12A43389076BCC7F4A27A0A">ソフトウェアへのフォールバック機能の場合は、Flash 15以降 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1">ブラウザーと <span class="codeph"> wmodeの設定</span> </td> 
   <td colname="col2"> <p><b>Flash 15では</b>、 <span class="codeph"> wmode=opaqueと設定して</span> 、HTMLオーバーレイを使用できます。 </p> <p>次のブラウザは、現在、ハードウェアアクセラレーションをサポートしていません。 
     <ul id="ul_frv_ykf_jp"> 
      <li id="li_3D407A61FEE042A9B85A6EFACA6D7719">Microsoft Windows上のMozilla Firefox </li> 
      <li id="li_39B85AC352564DA8B86EA826638F1F4B">Windows XPおよびVista上のGoogle Chromeおよび任意のバージョンのChrome </li> 
      <li id="li_0042BA6070C849E6B7C4B4BF4333F712">Microsoft Internet Explorer（すべてのバージョン） </li> 
     </ul>その他のブラウザーとOSの組み合わせでは、ハードウェアアクセラレーションにアクセスできない場合があります。 このようなシナリオでは、StageVideo <span class="codeph"> は</span> 、パフォーマンスに悪影響を与えるソフトウェアにフォールバックします。 </p> <p><b>Flash 14以前では</b>、ブラウザがハードウェアアクセラレーションをサポートしていない場合、Flash PlayerはGPUに直接レンダリングできますが、 <span class="codeph"> wmode=directを設定してこのレンダリングを有効にします</span> 。 <p>ヒント： 2009より古いGPUドライバーは、ハードウェアアクセラレーションのサポートがない可能性があるので、更新が必要な場合があります。 </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> NetStreamオブジェクト </td> 
   <td colname="col2">StageVideoEvent.RENDER_STATE <span class="codeph"> イベントは</span> 、NetStreamオブジェクトをStageVideoオブジェクトにアタッチしない限り、ディスパッチ <span class="codeph"></span><span class="codeph"></span> されません。 </td> 
  </tr> 
 </tbody> 
</table>

