---
description: 広告シグナリングモードは、ビデオストリームが広告情報を取得する必要がある場所を指定します。
seo-description: 広告シグナリングモードは、ビデオストリームが広告情報を取得する必要がある場所を指定します。
seo-title: 広告シグナリングモード
title: 広告シグナリングモード
uuid: 6e6e72cf-4de4-4ac1-9726-7521e47ccd83
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---


# 広告シグナリングモード{#ad-signaling-mode}

広告シグナリングモードは、ビデオストリームが広告情報を取得する必要がある場所を指定します。

有効な値は`PTAdSignalingModeDefault`、`PTAdSignalingModeManifestCues`、`PTAdSignalingModeServerMap`です。

次の表に、様々なHLSストリームタイプに対する`AdSignalingMode`値の効果を示します。

<table frame="all" colsep="1" rowsep="1" id="table_AdSignalingMode"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> </th> 
   <th colname="2" class="entry"><b>デフォルト</b></th> 
   <th colname="3" class="entry"><b>マニフェストキュー</b></th> 
   <th colname="4" class="entry"><b>広告サーバーマップ</b></th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> ビデオオンデマンド(VOD) </td> 
   <td colname="2"> 
    <ul id="ul_E79DA79107364D0D8B46A1859CA75B5C"> 
     <li id="li_B259ED87743F463095071F58DC840E39"> <p>サーバーマップを使用して配置を検出する </p> </li> 
     <li id="li_8957E4151466467BA6C954E5010E34EA"> <p>広告が挿入される </p> </li> 
    </ul> </td> 
   <td colname="3"> 
    <ul id="ul_D462C76717D94DE09915BDF6E9B3FB68"> 
     <li id="li_FB46108F4AD9457D99D2618ABEF7DBD1"> <p>インストリームキューを使用して配置を検出する </p> </li> 
     <li id="li_C3F7FBB98F524CEF97D17318C292E9EA"> <p>プリロール広告がメインストリームに挿入される </p> </li> 
     <li id="li_A56E1545F84840DFA6D065DA60E98C31"> <p>ミッドロール広告でメインストリームを置換 </p> </li> 
    </ul> </td> 
   <td colname="4"> 
    <ul id="ul_F10192B1B6F745CBB0D4C1A6D52A57B4"> 
     <li id="li_2ADACF71FA5F4A08A00A3399F5593420"> <p>サーバーマップを使用して配置を検出する </p> </li> 
     <li id="li_1201085B9C554A4BBD471E7EB2E363AC"> <p>広告が挿入される </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> ライブ/リニア </td> 
   <td colname="2"> 
    <ul id="ul_82AAC9EE056F49E999F809536A96C2F8"> 
     <li id="li_73BAD2BAA95F4592808B77F8DA436237"> <p>マニフェストキューを使用して配置を検出する </p> </li> 
     <li id="li_A97B6F61078D4149A984B2412021E103"> <p>広告でメインストリームを置換 </p> </li> 
    </ul> </td> 
   <td colname="3"> 
    <ul id="ul_CAED2D4F46334D76AE025482881BF843"> 
     <li id="li_A8023845A037482DBFDEF7EF247FECFD"> <p>インストリームキューを使用して配置を検出する </p> </li> 
     <li id="li_62A3CDAD249344EB89043B2AE0F4D7FF"> <p>広告でメインストリームを置換 </p> </li> 
    </ul> </td> 
   <td colname="4"> 非対応 </td> 
  </tr> 
 </tbody> 
</table>