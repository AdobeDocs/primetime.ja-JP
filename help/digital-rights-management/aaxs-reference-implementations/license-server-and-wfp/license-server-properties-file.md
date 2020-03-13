---
seo-title: ライセンスサーバーのプロパティファイル
title: ライセンスサーバーのプロパティファイル
uuid: bede307a-2060-451f-baf5-d058702c0a7e
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# ライセンスサーバーのプロパティファイル {#license-server-properties-file}

このファイルを [!DNL flashaccess-refimpl.properties] 使用して、参照実装のLicense Serverコンポーネントを設定します。 少なくとも、Transport CredentialとLicense Server Credentialに関連するプロパティを必ず設定してください。 秘密鍵証明書ファイルの場所は、プロパティで指定されたディレクトリを基準に指定する必要があ `config.resourcesDirectory` ります。 また、このファイルには、コンテンツのパッケージ化に関連するいくつかのプロパティが含まれています。これらのプロパティは、Flash Media Rights Management Server 1.xメタデータの変換にのみ使用されます。 このプロパティファイルの値を変更した場合は、変更を有効にするには、ライセンスサーバーを再起動する必要があります。

Adobe AccessでiOSクライアントへのリモートキー配信のライセンスの生成をサポートするには、でキーサーバー証明書を指定する必要がありま [!DNL flashaccess-refimpl.properties]す。

次のプロパティがAdobe Accessに追加されました。

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
   <td colname="2" class="- topic/entry "> 鍵サーバーのライセンスサーバー証明書（アドビが発行）。 この証明書は、メタデータがキーサーバーが必要であることを示している場合に、iOSデバイスのライセンスを生成するために使用されます。 </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> RefImpl.HSM.HandlerConfiguration.\ KeyServerCertificate.Alias</span> </td> 
   <td colname="2" class="- topic/entry ">HSMに保存されるキーサーバーのアドビ発行ライセンスサーバー証明書のエイリアス。 HSMが有効な場合は、HandlerConfiguration.KeyServerCertificateの代わりにこのプロパティを使用 <span class="codeph"> します</span>。 </td> 
  </tr> 
 </tbody> 
</table>

