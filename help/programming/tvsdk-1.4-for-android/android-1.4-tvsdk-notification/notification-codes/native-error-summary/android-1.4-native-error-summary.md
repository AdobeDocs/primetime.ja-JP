---
seo-title: NATIVE_ERROR通知の詳細
title: NATIVE_ERROR通知の詳細
uuid: 18c4da57-59de-41a8-a2ea-fef800565207
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# NATIVE_ERROR通知の詳細 {#details-for-the-native-error-notification}

TVSDKは、ネイティブエラーを処理する際に、次のメタデータキーの値の一部またはすべてを設定します。

<table id="table_86A21619515B435DBB65DC4DFBB64B29"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> メタデータキー名 </th> 
   <th colname="col2" class="entry"> メタデータ値 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> NATIVE_ERROR_CODE </span> </td> 
   <td colname="col2"> 
    <ph>
      AVEのネイティブエラーコード。 
    </ph> これらのコードは、次を表します。 
    <ul id="ul_330C626DE27B45A09E8851CC24768A07"> 
     <li id="li_0845A9BBB55545BDB49BD4F4802C0E54">DRMエラー（コード3300 ～ 3367）。 これらは、同等のFlash Playerエラーコードと同じです。 </li> 
     <li id="li_98A571480C154CF0AE1DC101FF0834C4">ビデオ再生エラー(-1 ～ 89)。 </li> 
     <li id="li_D7C19955DEF94DA88B822C8C57D6D2F4">暗号化エラー(300 ～ 307)。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> NATIVE_ERROR_NAME </span> </td> 
   <td colname="col2"> エラー名を含む文字列。例えば、 <span class="codeph"> AAXS_InvalidVoucherや </span> DECODER_FAILEDなどです <span class="codeph"></span>。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> NATIVE_SUBERROR_CODE </span> </td> 
   <td colname="col2"> DRMエラーの場合、サブエラーコードも返されます。 これらのコードは、Flash Playerから返 <span class="codeph"> されるDRMErrorEvents </span> サブエラーコードに対応しています。 エラーをアドビに報告する際は、トラブルシューティングのために、この数値を含めてください。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> DRM_ERROR_STRING </span> </td> 
   <td colname="col2"> DRMの場合、これはDRMサーバーデプロイメントのカスタムエラー文字列です（定義している場合）。 アドビにエラーを報告する際にも含めます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> 説明 </span> </td> 
   <td colname="col2"> エラーの説明を示す文字列。 通常、メディアのURL。 </td> 
  </tr> 
 </tbody> 
</table>

TVSDKは、これらのエラーコードと文字列をビデオエンジンから受け取ります。

>[!IMPORTANT]
>
>Adobe Primetime DRMクライアントのエラーコードの完全なリストについては、『 [DRM Client Error Message Reference』を参照してください](https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_client_error_message_reference.pdf)。