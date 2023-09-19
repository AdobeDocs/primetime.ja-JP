---
title: 保護されたコンテンツの再生に必要なデバイス機能
description: 保護されたコンテンツの再生に必要なデバイス機能
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---

# 保護されたコンテンツの再生に必要なデバイス機能 {#device-capabilities-required-to-play-protected-content}

必要なデバイス機能は、コンテンツへのアクセスに必要なハードウェア機能を指定します。 ポートキットを使用するデバイスでは、ハードウェア機能に関する情報を利用できます。

次の属性でデバイスの機能を識別できます。

<table id="table_v3n_fks_n4"> 
 <tbody> 
  <tr> 
   <td><b>属性</b> </td> 
   <td><b>サポートされている値</b> </td> 
   <td><b>一致条件</b> </td> 
   <td><b>説明</b> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">ユーザーがアクセスできないバス </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">"true"または"false" </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">完全一致 </p> </td> 
   <td colname="4" class="- topic/entry "> <p class="- topic/p ">true の場合、デバイスにユーザーがアクセスできるバスを持つことはできません。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">信頼のハードウェアルート </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">"true"または"false" </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">完全一致 </p> </td> 
   <td colname="4" class="- topic/entry "> <p class="- topic/p ">true の場合、デバイスは信頼のハードウェアルートを持つ必要があります。 </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>この使用ルールは、Adobe Primetime DRM クライアントバージョン 2.0.2 以降でサポートされています。 古いクライアントでの動作は、ライセンスサーバーでサポートされる最小クライアントバージョンによって異なります。
>
>詳しくは、 [最小クライアントバージョン](../../../../protecting-content/setting-up-the-sdk/setup-dev-env.md).
