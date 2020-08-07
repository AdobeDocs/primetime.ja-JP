---
description: 'null'
seo-description: 'null'
seo-title: 保護されたコンテンツの再生に必要なデバイス機能
title: 保護されたコンテンツの再生に必要なデバイス機能
uuid: 1490711b-65d9-4716-8779-ae1da7d2c82c
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%

---


# 保護されたコンテンツの再生に必要なデバイス機能 {#device-capabilities-required-to-play-protected-content}

必要なデバイス機能は、コンテンツへのアクセスに必要なハードウェア機能を指定します。 ハードウェア機能に関する情報は、ポーティングキットを使用するデバイスで利用できます。

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
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">ユーザーアクセス不可のバス </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">"true"または"false" </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">完全一致 </p> </td> 
   <td colname="4" class="- topic/entry "> <p class="- topic/p ">trueの場合、デバイスにユーザーアクセス可能なバスを持つことはできません。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">信頼のハードウェアルート </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">"true"または"false" </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">完全一致 </p> </td> 
   <td colname="4" class="- topic/entry "> <p class="- topic/p ">trueの場合、デバイスは信頼のハードウェアルートを持つ必要があります。 </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>この使用ルールは、Adobe PrimetimeDRMクライアントバージョン2.0.2以降でサポートされています。 古いクライアントでの動作は、ライセンスサーバーでサポートされている最小クライアントバージョンによって異なります。
>
>「 [最小クライアントバージョン](../../../../protecting-content/setting-up-the-sdk/setup-dev-env.md)」を参照してください。

