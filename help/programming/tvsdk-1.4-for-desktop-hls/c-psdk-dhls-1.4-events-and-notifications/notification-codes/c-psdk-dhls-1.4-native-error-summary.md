---
title: NATIVE_ERROR 通知の詳細
description: NATIVE_ERROR 通知の詳細
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# NATIVE_ERROR 通知の詳細 {#details-for-the-native-error-notification}

TVSDK は、ネイティブエラーを処理する際に、以下のメタデータキーの値の一部またはすべてを設定します。

<table id="table_86A21619515B435DBB65DC4DFBB64B29"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> メタデータキー名 </th> 
   <th colname="col2" class="entry"> メタデータ値 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> RUNTIME_CODE </span> </td> 
   <td colname="col2"> 
    <pre>
      Flash Playerのネイティブエラーコード。 
    </pre> これらのコードは、次を表します。 
    <ul id="ul_330C626DE27B45A09E8851CC24768A07"> 
     <li id="li_0845A9BBB55545BDB49BD4F4802C0E54">DRM エラー（コード 3300 ～ 3367）。 これらは、同等のエラーコードFlash Playerと同じです。 </li> 
     <li id="li_98A571480C154CF0AE1DC101FF0834C4">ビデオ再生エラー (-1 ～ 89)。 </li> 
     <li id="li_D7C19955DEF94DA88B822C8C57D6D2F4">暗号化エラー (300 ～ 307)。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> RUNTIME_CODE_MESSAGE </span> </td> 
   <td colname="col2"> エラーの名前を含む文字列。例： <span class="codeph"> AAXS_InvalidVoucher </span> または <span class="codeph"> DECODER_FAILED </span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> RUNTIME_SUBERROR_CODE </span> </td> 
   <td colname="col2"> DRM エラーの場合は、サブエラーコードも返されます。 これらのコードは、 <span class="codeph"> DRMErrorEvents </span> Flash Playerが返すサブエラーコード。 エラーをAdobeに報告する場合は、この数値をトラブルシューティングの支援に使用します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> DRM_ERROR_STRING </span> </td> 
   <td colname="col2"> DRM の場合、これは DRM サーバーデプロイメント（定義している場合）のカスタムエラー文字列です。 エラーをAdobeに報告する場合も含めます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> 説明 </span> </td> 
   <td colname="col2"> エラーの文字列の説明。 通常はメディアの URL です。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> RESOURCE_URL </span> </td> 
   <td colname="col2"> メディアの URL。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> RESOURCE_TYPE </span> </td> 
   <td colname="col2"> メディアのタイプ (HLS)。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> RESOURCE_ID </span> </td> 
   <td colname="col2"> メディアの ID。 </td> 
  </tr> 
 </tbody> 
</table>

TVSDK は、ビデオエンジンからこれらのエラーコードと文字列を受け取ります。

>[!IMPORTANT]
>
>Adobe Primetime DRM クライアントのエラーコードの完全なリストについては、 [DRM クライアントエラーメッセージの参照](https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_client_error_message_reference.pdf).
