---
seo-title: ライセンスサーバーのプロパティファイル
title: ライセンスサーバーのプロパティファイル
uuid: bede307a-2060-451f-baf5-d058702c0a7e
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---


# ライセンスサーバーのプロパティファイル{#license-server-properties-file}

[!DNL flashaccess-refimpl.properties]ファイルを使用して、参照実装のLicense Serverコンポーネントを設定します。 少なくとも、Transport CredentialとLicense Serverの秘密鍵証明書に関連するプロパティを設定する必要があります。 秘密鍵証明書ファイルの場所は、`config.resourcesDirectory`プロパティで指定されたディレクトリを基準に指定する必要があります。 このファイルには、コンテンツのパッケージ化に関連するいくつかのプロパティも含まれています。これらのプロパティは、FlashMediaRights ManagementServer 1.xのメタデータ変換にのみ使用されます。 このプロパティファイルの値のいずれかを変更した場合、変更を有効にするには、ライセンスサーバーを再起動する必要があります。

Adobeアクセスでリモートキー配信のライセンスをiOSクライアントに対して生成できるようにするには、[!DNL flashaccess-refimpl.properties]にキーサーバー証明書を指定する必要があります。

Adobeアクセスに次のプロパティが追加されました。

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_xz2_lwy_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">プロパティ </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">説明 </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> HandlerConfiguration.KeyServerCertificate</span> </td> 
   <td colname="2" class="- topic/entry "> Adobeが発行するキーサーバーのライセンスサーバー証明書。 この証明書は、メタデータがキーサーバーが必要であることを示している場合に、iOSデバイスのライセンスを生成するために使用されます。 </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> RefImpl.HSM.HandlerConfiguration.\ KeyServerCertificate.Alias</span> </td> 
   <td colname="2" class="- topic/entry ">HSMに保存されているキーサーバーのAdobe発行ライセンスサーバー証明書のエイリアス。 HSMが有効な場合は、<span class="codeph"> HandlerConfiguration.KeyServerCertificate</span>の代わりに、このプロパティを使用します。 </td> 
  </tr> 
 </tbody> 
</table>

