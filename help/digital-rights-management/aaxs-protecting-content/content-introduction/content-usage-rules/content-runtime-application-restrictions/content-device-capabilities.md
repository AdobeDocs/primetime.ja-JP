---
seo-title: 保護されたコンテンツの再生に必要なデバイス機能
title: 保護されたコンテンツの再生に必要なデバイス機能
uuid: 16ed73d9-e02f-4c86-bf15-2d3e7122bf5a
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# 保護されたコンテンツの再生に必要なデバイス機能 {#device-capabilities-required-to-play-protected-content}

コンテンツへのアクセスに必要なハードウェア機能を指定します。 ハードウェア機能に関する情報は、移植キットを使用するデバイスで利用できます。

デバイスの機能は、次の表に示す属性で識別できます。

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
   <td colname="4" class="- topic/entry "> <p class="- topic/p ">trueの場合、デバイスにユーザーがアクセス可能なバスが存在しない。 </p> </td> 
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
>この使用ルールは、Adobe Accessクライアントバージョン2.0.2以降でサポートされています。 古いクライアントでの動作は、ライセンスサーバーでサポートされている最小限のクライアントバージョンによって異なります。 「最小クライアン [トバージョン](../../../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md)」を参照。

