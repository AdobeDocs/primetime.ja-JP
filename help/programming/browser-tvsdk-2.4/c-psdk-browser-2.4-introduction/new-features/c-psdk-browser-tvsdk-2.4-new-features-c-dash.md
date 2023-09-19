---
description: ブラウザー TVSDK は、ビデオアプリケーションに機能を追加するために実装できる多数の DASH 機能をサポートしています。
title: サポートされる DASH 機能
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# サポートされる DASH 機能{#supported-dash-features}

ブラウザー TVSDK は、ビデオアプリケーションに機能を追加するために実装できる多数の DASH 機能をサポートしています。

* [DASH コア再生機能](#dash-core-playback)
* [DASH 高度な再生機能](#dash-advanced-playback)
* [DASH コンテンツ保護機能](#dash-content-protection)
* [DASH コア広告挿入機能](#dash-core-ad-insertion)
* [DASH の高度な広告挿入機能](#dash-advanced-insertion-features)
* [DASH 統合](#dash-integrations)

>[!TIP]
>
>以下の機能マトリックスの表では、  ![](assets/supported15.png)
>は、この機能が現在のリリースでサポートされていることを意味します。

次の機能がサポートされています。

<!-- 

<table id="table_lrb_p2g_xx"> 
 <title>DASH integrations</title> 
 <tgroup cols="4"> 
  <colspec colnum="1" colname="col1" colwidth="*" /> 
  <colspec colnum="2" colname="col2" colwidth="*" /> 
  <colspec colnum="3" colname="col3" colwidth="*" /> 
  <colspec colnum="4" colname="col6" colwidth="*" /> 
  <thead> 
   <tr> 
    <th colname="col1" class="entry"> Category </th> 
    <th colname="col2" class="entry"> Content type </th> 
    <th colname="col3" class="entry"> Feature </th> 
    <th colname="col6" align="center" class="entry"> 
     <lines>
       HTML5 FF, IE, Chrome, Android Chrome
     </lines> </th> 
   </tr> 
  </thead> 
  <tbody> 
   <tr> 
    <td colname="col1"> Integrations </td> 
    <td colname="col2"> VOD + Live </td> 
    <td colname="col3"> Adobe Analytics VHL integration </td> 
    <td colname="col6" valign="middle" align="center"><img href="assets/supported15.png" id="image_14D9248BD1D8410E83AD27DB4AB3B6ED" /> </td> 
   </tr> 
   <tr> 
    <td colname="col1"> Integrations </td> 
    <td colname="col2"> VOD + Live </td> 
    <td colname="col3"> Nielsen support </td> 
    <td colname="col6" valign="middle" align="center"><img href="assets/supported15.png" id="image_EFA853CB763446B3B37F2CF6BCC53EE1" /> </td> 
   </tr> 
   <tr> 
    <td colname="col1"> Integrations </td> 
    <td colname="col2"> VOD + Live </td> 
    <td colname="col3"> Billing </td> 
    <td colname="col6" valign="middle" align="center"><img href="assets/supported15.png" id="image_B3A4E5937CEC4052977C08767219BC2B" /> </td> 
   </tr> 
   <tr> 
    <td colname="col1"> Integrations </td> 
    <td colname="col2"> VOD + Live </td> 
    <td colname="col3"> Browserify </td> 
    <td colname="col6" valign="middle" align="center"><img href="assets/supported15.png" id="image_3330E81B86C84AD391AEBFDFE911A47F" /> </td> 
   </tr> 
  </tbody> 
 </tgroup> 
</table>

 -->

## DASH 統合 {#dash-integrations}

| カテゴリ | コンテンツタイプ | 機能 | HTML5 FF、IE、Chrome、Android Chrome |
|---|---|---|---|
| 統合 | VOD + Live | Adobe Analytics VHL 統合 | ![](assets/supported15.png) |
| 統合 | VOD + Live | 請求 | ![](assets/supported15.png) |
| 統合 | VOD + Live | Browserify | ![](assets/supported15.png) |

## DASH の高度な広告挿入機能 (CSAI) {#dash-advanced-insertion-features}

| カテゴリ | コンテンツタイプ | 機能 | HTML5 FF、IE、Chrome、Android Chrome |
|---|---|---|---|
| Ad Insertion | VOD | 広告のみ | サポート対象外 |
| Ad Insertion | VOD | ターゲティングパラメーター | VOD のみ |
| Ad Insertion | VOD | カスタムパラメーター | VOD のみ |
| Ad Insertion | VOD + Live | カスタム広告ポリシー | サポート対象外 |
| Ad Insertion | VOD + Live | 遅延広告読み込み | サポート対象外 |
| Ad Insertion | VOD | コンパニオン広告、バナー広告、クリック可能な広告 | サポート対象外 |
| Ad Insertion | VOD | VPAID 2.0 | サポート対象外 |

## DASH コア広告挿入機能 (CSAI) {#dash-core-ad-insertion}

| カテゴリ | コンテンツタイプ | 機能 | HTML5 FF、IE、Chrome、Android Chrome |
|---|---|---|---|
| Ad Insertion | VOD + Live | プリロール | VOD のみ |
| Ad Insertion | VOD + Live | ミッドロール | VOD のみ |
| Ad Insertion | VOD + Live | ポストロール | VOD のみ |
| Ad Insertion | FER VOD | 広告の解像度と動作 | サポート対象外 |
| Ad Insertion | VOD + Live | デフォルトの広告ポリシー | VOD のみ |
| Ad Insertion | VOD + Live | VAST 2.0/3.0 | VOD のみ |
| Ad Insertion | VOD + Live | VMAP 1.0 | VOD のみ |
| Ad Insertion | VOD + Live | CRS v3.1 | VOD のみ |

## DASH コンテンツ保護機能 {#dash-content-protection}

<table id="table_hrb_p2g_xx">  
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> カテゴリ </th> 
   <th colname="col2" class="entry"> コンテンツタイプ </th> 
   <th colname="col3" class="entry"> 機能 </th> 
   <th colname="col6" class="entry"> HTML5 FF、IE、Chrome、Android Chrome</th>
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> コンテンツ保護 </td> 
   <td colname="col2"> VOD + Live </td> 
   <td colname="col3"> AES-128 </td> 
   <td colname="col6"> サポート対象外 </td>
  </tr> 
  <tr> 
   <td colname="col1"> コンテンツ保護 </td> 
   <td colname="col2"> VOD + Live </td> 
   <td colname="col3"> Sample-AES </td> 
   <td colname="col6"> サポート対象外 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> コンテンツ保護 </td> 
   <td colname="col2"> VOD </td> 
   <td colname="col3"> DRM </td> 
   <td colname="col6"> 
    <ul id="ul_irb_p2g_xx"> 
     <li id="li_C4643F2978BC4C8ABDB3E6C72C75A468">Widevine on 
      <ul id="ul_7047EA49AA3F40FE8F90E0ED6C028D83"> 
       <li id="li_B575735388D74D789D56BF373A470A6D">クロム </li> 
       <li id="li_855146E4AC3A48E69B65F0022E1C0156">Firefox 47 以降 </li> 
       <li id="li_BC06B0A6EAAC4FC991C713775A8BB4DA">Chromecast </li> 
      </ul> </li> 
     <li id="li_D48B51C2208F423CB85D08886C2E1C66">Windows 8.1 および Edge 上の Internet Explorer での PlayReady </li> 
     <li id="li_2786AC19387241A296E015EE6FD07F2D">Windows Firefox のAdobeアクセス（ビデオのみ） </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## DASH の高度な再生機能 {#dash-advanced-playback}

| カテゴリ | コンテンツタイプ | 機能 | HTML5、FF、IE、Chrome、Android Chrome |
|---|---|---|---|
| 再生 | VOD | オフセットでの再生 | ![](assets/supported15.png) |
| 再生 | VOD | オーディオのみの再生 | ![](assets/supported15.png) |
| 再生 | VOD | トリック再生 | ![](assets/supported15.png) |
| 再生 | VOD | 滑らかなトリック再生 | ![](assets/supported15.png) |
| 再生 | VOD + Live | ID3 の解析 | サポート対象外 |
| 再生 | VOD | 複数期間のサポート | VOD のみ |
| 再生 | VOD + Live | トークン化ストリーム | サポート対象外 |
| 再生 | VOD + Live | 請求 | ![](assets/supported15.png) |
| 再生 | VOD + Live | Browserify | ![](assets/supported15.png) |

## DASH コア再生機能 {#dash-core-playback}

| カテゴリ | コンテンツタイプ | 機能 | HTML5 FF、IE、Chrome、Android Chrome |
|---|---|---|---|
| 再生 | VOD + Live | 一般的な再生（再生、一時停止、シーク） | ![](assets/supported15.png) |
| 再生 | FER VOD | 一般的な再生（再生、一時停止、シーク） | サポート対象外 |
| 再生 | VOD + Live | 適応ビットレート | ![](assets/supported15.png) |
| 再生 | VOD + Live | 608/708キャプション | ![](assets/supported15.png) |
| 再生 | VOD + Live | WebVTT | VOD のみ |
| 再生 | VOD + Live | フェイルオーバー | VOD のみ |
| 再生 | VOD + Live | QoS とプレーヤーの通知 | ![](assets/supported15.png) |
| 再生 | VOD + Live | cookie ヘッダーのサポート | ![](assets/supported15.png) |
| 再生 | VOD + Live | バッファ制御パラメータの設定 | ![](assets/supported15.png) |
| 再生 | VOD + Live | アダプティブビットレートコントロールの設定 | ![](assets/supported15.png) |
| 再生 | VOD + Live | カスタムタグ (EventStream) | VOD のみ（インライン） |
| 再生 | VOD + Live | 遅延バインディングオーディオ | VOD のみ |
| 再生 | VOD + Live | 302 リダイレクト | VOD のみ |
