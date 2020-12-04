---
description: ブラウザーTVSDKは、ビデオアプリケーションに機能を追加するために実装できる多数のDASH機能をサポートしています。
seo-description: ブラウザーTVSDKは、ビデオアプリケーションに機能を追加するために実装できる多数のDASH機能をサポートしています。
seo-title: サポートされるDASH機能
title: サポートされるDASH機能
uuid: 299516a4-09ed-4b8a-b0bf-a04f204f385a
translation-type: tm+mt
source-git-commit: 5df9a8b98baaf1cd1803581d2b60c7ed4261a0e8
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---


# サポートされるDASH機能{#supported-dash-features}

ブラウザーTVSDKは、ビデオアプリケーションに機能を追加するために実装できる多数のDASH機能をサポートしています。

* [DASHコア再生機能](#dash-core-playback)
* [DASH高度な再生機能](#dash-advanced-playback)
* [DASHコンテンツ保護機能](#dash-content-protection)
* [DASHコア広告挿入機能](#dash-core-ad-insertion)
* [DASH Advanced広告挿入機能](#dash-advanced-insertion-features)
* [DASH統合](#dash-integrations)

>[!TIP]
>
>以下の機能マトリクステーブルに![](assets/supported15.png)
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

## DASH統合{#dash-integrations}

| カテゴリ | コンテンツタイプ | 機能 | HTML5 FF、IE、Chrome、Android Chrome |
|---|---|---|---|
| 統合 | VOD + Live | Adobe AnalyticsVHL統合 | ![](assets/supported15.png) |
| 統合 | VOD + Live | 請求 | ![](assets/supported15.png) |
| 統合 | VOD + Live | Browserify | ![](assets/supported15.png) |

## DASHの高度な広告挿入機能(CSAI) {#dash-advanced-insertion-features}

| カテゴリ | コンテンツタイプ | 機能 | HTML5 FF、IE、Chrome、Android Chrome |
|---|---|---|---|
| Ad Insertion | VOD | 広告のみ | 非対応 |
| Ad Insertion | VOD | ターゲット設定パラメーター | VODのみ |
| Ad Insertion | VOD | カスタムパラメーター | VODのみ |
| Ad Insertion | VOD + Live | カスタム広告ポリシー | 非対応 |
| Ad Insertion | VOD + Live | 遅延広告読み込み | 非対応 |
| Ad Insertion | VOD | コンパニオン広告、バナー広告、クリック可能な広告 | 非対応 |
| Ad Insertion | VOD | VPAID 2.0 | 非対応 |

## DASHコア広告挿入機能(CSAI) {#dash-core-ad-insertion}

| カテゴリ | コンテンツタイプ | 機能 | HTML5 FF、IE、Chrome、Android Chrome |
|---|---|---|---|
| Ad Insertion | VOD + Live | プリロール | VODのみ |
| Ad Insertion | VOD + Live | ミッドロール | VODのみ |
| Ad Insertion | VOD + Live | ポストロール | VODのみ |
| Ad Insertion | FER VOD | 広告の解像度と動作 | 非対応 |
| Ad Insertion | VOD + Live | デフォルトの広告ポリシー | VODのみ |
| Ad Insertion | VOD + Live | VAST 2.0/3.0 | VODのみ |
| Ad Insertion | VOD + Live | VMAP 1.0 | VODのみ |
| Ad Insertion | VOD + Live | CRS v3.1 | VODのみ |

## DASHコンテンツ保護機能{#dash-content-protection}

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
   <td colname="col6"> 非対応 </td>
  </tr> 
  <tr> 
   <td colname="col1"> コンテンツ保護 </td> 
   <td colname="col2"> VOD + Live </td> 
   <td colname="col3"> Sample-AES </td> 
   <td colname="col6"> 非対応 </td> 
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
       <li id="li_855146E4AC3A48E69B65F0022E1C0156">Firefox 47+ </li> 
       <li id="li_BC06B0A6EAAC4FC991C713775A8BB4DA">Chromecast </li> 
      </ul> </li> 
     <li id="li_D48B51C2208F423CB85D08886C2E1C66">Windows 8.1およびEdge上のInternet ExplorerでのPlayReady </li> 
     <li id="li_2786AC19387241A296E015EE6FD07F2D">Windows FirefoxのAdobeアクセス（ビデオのみ） </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## DASH高度な再生機能{#dash-advanced-playback}

| カテゴリ | コンテンツタイプ | 機能 | HTML5、FF、IE、Chrome、Android Chrome |
|---|---|---|---|
| 再生 | VOD | オフセットでの再生 | ![](assets/supported15.png) |
| 再生 | VOD | オーディオのみの再生 | ![](assets/supported15.png) |
| 再生 | VOD | トリック再生 | ![](assets/supported15.png) |
| 再生 | VOD | スムーズトリック再生 | ![](assets/supported15.png) |
| 再生 | VOD + Live | ID3の解析 | 非対応 |
| 再生 | VOD | 複数期間のサポート | VODのみ |
| 再生 | VOD + Live | トークン化されたストリーム | 非対応 |
| 再生 | VOD + Live | 請求 | ![](assets/supported15.png) |
| 再生 | VOD + Live | Browserify | ![](assets/supported15.png) |

## DASHコア再生機能{#dash-core-playback}

| カテゴリ | コンテンツタイプ | 機能 | HTML5 FF、IE、Chrome、Android Chrome |
|---|---|---|---|
| 再生 | VOD + Live | 一般再生（再生、一時停止、シーク） | ![](assets/supported15.png) |
| 再生 | FER VOD | 一般再生（再生、一時停止、シーク） | 非対応 |
| 再生 | VOD + Live | 可変ビットレート | ![](assets/supported15.png) |
| 再生 | VOD + Live | 608/708キャプション | ![](assets/supported15.png) |
| 再生 | VOD + Live | WebVTT | VODのみ |
| 再生 | VOD + Live | フェイルオーバー | VODのみ |
| 再生 | VOD + Live | QoSおよびプレイヤー通知 | ![](assets/supported15.png) |
| 再生 | VOD + Live | cookieヘッダーのサポート | ![](assets/supported15.png) |
| 再生 | VOD + Live | バッファー制御パラメーターの設定 | ![](assets/supported15.png) |
| 再生 | VOD + Live | 可変ビットレートコントロールの設定 | ![](assets/supported15.png) |
| 再生 | VOD + Live | カスタムタグ(EventStream) | VODのみ（インライン） |
| 再生 | VOD + Live | 遅延バインディングオーディオ | VODのみ |
| 再生 | VOD + Live | 302リダイレクト | VODのみ |