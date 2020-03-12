---
description: 'null'
seo-description: 'null'
seo-title: 保護されたコンテンツの再生に必要なデバイス機能
title: 保護されたコンテンツの再生に必要なデバイス機能
uuid: 1490711b-65d9-4716-8779-ae1da7d2c82c
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# 保護されたコンテンツの再生に必要なデバイス機能 {#device-capabilities-required-to-play-protected-content}

必要なデバイス機能は、コンテンツへのアクセスに必要なハードウェア機能を指定します。 ハードウェア機能に関する情報は、移植キットを使用するデバイスで利用できます。

次の属性で、デバイスの機能を識別できます。

<table id="table_v3n_fks_n4"> 
 <tbody> 
  <tr> 
   <td><b>属性</b> </td> 
   <td><b>サポートされる値</b> </td> 
   <td><b>一致条件</b> </td> 
   <td><b>説明</b> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">非ユーザーアクセスバス </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">"true"または"false" </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">完全一致 </p> </td> 
   <td colname="4" class="- topic/entry "> <p class="- topic/p ">trueの場合、デバイスにはユーザーアクセス可能なバスがない。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">信頼のハードウェアルート </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">"true"または"false" </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">完全一致 </p> </td> 
   <td colname="4" class="- topic/entry "> <p class="- topic/p ">trueの場合、デバイスには信頼のハードウェアルートが必要です。 </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>この使用ルールは、Adobe Primetime DRMクライアントバージョン2.0.2以降でサポートされています。 古いクライアントでの動作は、ライセンスサーバーでサポートされている最小限のクライアントバージョンによって異なります。
>
>「最小クライ [アントバージョン](../../../../protecting-content/setting-up-the-sdk/setup-dev-env.md)」を参照。

