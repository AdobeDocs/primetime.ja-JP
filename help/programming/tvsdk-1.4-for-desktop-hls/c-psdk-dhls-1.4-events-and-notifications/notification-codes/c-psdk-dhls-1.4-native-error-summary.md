---
title: NATIVE_ERROR通知の詳細
description: NATIVE_ERROR通知の詳細
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---


# NATIVE_ERROR通知{#details-for-the-native-error-notification}の詳細

TVSDKは、ネイティブエラーを処理する際に、以下のメタデータキーの値の一部またはすべてを設定します。

<table id="table_86A21619515B435DBB65DC4DFBB64B29"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> メタデータキー名 </th> 
   <th colname="col2" class="entry"> メタデータ値 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> RUNTIME_CODE  </span> </td> 
   <td colname="col2"> 
    <pre>
      Flash Playerのネイティブエラーコードです。 
    </pre> これらのコードは、次を表します。 
    <ul id="ul_330C626DE27B45A09E8851CC24768A07"> 
     <li id="li_0845A9BBB55545BDB49BD4F4802C0E54">DRMエラー（コード3300 ～ 3367）。 これらは、同等のFlash Playerエラーコードと同じです。 </li> 
     <li id="li_98A571480C154CF0AE1DC101FF0834C4">ビデオ再生エラー(-1 ～ 89)。 </li> 
     <li id="li_D7C19955DEF94DA88B822C8C57D6D2F4">暗号化エラー(300 ～ 307)。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> RUNTIME_CODE_MESSAGE  </span> </td> 
   <td colname="col2"> エラー名を含む文字列。例えば、<span class="codeph"> AAXS_InvalidVoucher </span>や<span class="codeph"> DECODER_FAILED </span>です。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> RUNTIME_SUBERROR_CODE  </span> </td> 
   <td colname="col2"> DRMエラーの場合、サブエラーコードも返されます。 これらのコードは、Flash Playerが返す<span class="codeph"> DRMErrorEvents </span>サブエラーコードに対応します。 Adobeにレポートエラーが発生した場合は、トラブルシューティングのために、この数値を含めてください。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> DRM_ERROR_STRING  </span> </td> 
   <td colname="col2"> DRMの場合、これはDRMサーバーデプロイメント（定義した場合）のカスタムエラー文字列です。 Adobeにレポートエラーが発生した場合も含めます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> 説明  </span> </td> 
   <td colname="col2"> エラーを説明する文字列。 通常はメディアのURLです。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> RESOURCE_URL  </span> </td> 
   <td colname="col2"> メディアのURL。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> RESOURCE_TYPE  </span> </td> 
   <td colname="col2"> メディアのタイプ(HLS)。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> RESOURCE_ID  </span> </td> 
   <td colname="col2"> メディアのID。 </td> 
  </tr> 
 </tbody> 
</table>

TVSDKは、これらのエラーコードと文字列をビデオエンジンから受け取ります。

>[!IMPORTANT]
>
>Adobe PrimetimeDRMクライアントのエラーコードの完全なリストについては、[DRM Client Error Message Reference](https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_client_error_message_reference.pdf)を参照してください。