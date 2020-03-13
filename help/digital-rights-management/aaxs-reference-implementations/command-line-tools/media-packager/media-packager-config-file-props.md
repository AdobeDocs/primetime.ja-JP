---
seo-title: 設定ファイルのプロパティ
title: 設定ファイルのプロパティ
uuid: f0d36240-e5fa-4bf9-9a82-7e963d03cdd0
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# 設定ファイルのプロパティ {#configuration-file-properties}

Media Packagerを実行する前に、Media Packagerのプロパティの値を指定します。 設定ファイルでは、次のプロパティを指定します。 * n*を含むプロパティ名の場合、 *n* は1から始まり、プロパティの各インスタンスに対して増加する整数を表します。

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_dx4_mpy_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">プロパティ </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">説明 </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.video</span> </td> 
   <td colname="2" class="- topic/entry "> ビデオコンテンツを暗号化するかどうかを示します。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.audio</span> </td> 
   <td colname="2" class="- topic/entry "> オーディオを暗号化するかどうかを示します。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.script</span> </td> 
   <td colname="2" class="- topic/entry ">FLVのスクリプトデータを暗号化するかどうかを示します。 <i class="+ topic/ph hi-d/i ">onMetaDataと</i> onXMP <i class="+ topic/ph hi-d/i ">Scriptのデータタグは</i> 、このオプションが有効になっている場合でも暗号化されません。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.video.level</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ビデオの暗号化レベルを示します。 highの値はすべてのビデオコンテンツを暗号化するのに使用され、mediumとlowの値はH.264コンテンツを含むF4Vファイルのビデオコンテンツの一部を暗号化するのに使用されます。 </p> <p class="- topic/p ">value = <span class="codeph"> high| medium|低</span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.secondsUnencrypted</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">この値が0より大きい場合、ファイルの先頭の指定された秒数の内容は暗号化されません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.asymmetric.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">キーの暗号化に使用するライセンスサーバー証明書ファイル。 encrypt.keys. <span class="codeph"> asymmetric.certfileプロパティは、証明書のみを含むファイルを指定します</span> （PEMまたはDER形式を使用できます）。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">encrypt.keys.policyFile.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">このプロパティは、コンテンツに適用するポリシーのリストを作成するために繰り返し使用されます。 <span class="codeph"> nは</span> 1以上の整数です。 クライアントはデフォルトで最初のインスタンスを使用します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.serverurl</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスサーバーのURL。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.servercert</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスサーバーのトランスポート証明書。 このプロパティは、証明 <span class="filepath"> 書のみを含む</span> .cerファイルを指定します（PEMまたはDER形式を使用できます）。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.sign.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コンテンツに署名するためのパッケージャーの資格情報を含むPKCS12ファイルです。 encrypt.sign.certfile <span class="codeph"> は、証明書と秘密鍵を含む</span> .pfx <span class="filepath"></span> (.pfx)ファイルを参照する必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.sign.certpass</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">encrypt.sign.certfileで指定したファイルの保護に使 <span class="codeph"> 用されるパスワード</span>。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.minServerVersion</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">パッケージ化するコンテンツのライセンスの発行に必要な最小サーバーバージョンを設定します。 x(Adobe Access x.0)を指定します。xはメジャーリリース番号です。 Adobe Access 3.0より前のサーバーでは、この設定はサポートされていません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">encrypt.keys.policyFile.n.domain.transportcert</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ポリシー <span class="+ topic/ph pr-d/codeph codeph"> encrypt.keys.policyFile.nで</span><span class="+ topic/ph pr-d/codeph codeph"></span>、encrypt.license.servercertで指定されたのとは異なるトランスポート証明書を使用するサーバーとのドメイン登録が必要な場合は、ドメイントランスポート証明書を指定する必要があります。 </p> <p class="- topic/p ">このプロパティは、証明書のみを含むファイルを指定します（PEMまたはDER形式を使用できます）。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.licenseKey</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスキーを指定します。 キーが指定されていない場合、キーはランダムに生成されます。 キーの回転が有効になっていない場合、コンテンツの暗号化に使用されるキーです。 </p> <p class="- topic/p ">キーの回転が有効な場合、このキーは回転キーの保護に使用されます。 キーは16バイトの長さで、16進数値で指定する必要があります。 16進数値の間の空白はオプションです。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.rotation.enable</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">キーの回転を有効にするかどうかを指定します。 false（デフォルト）に設定した場合、キーの回転は無効になり、マスターCEKを使用してコンテンツ内のすべてのサンプルが暗号化されます。 </p> <p class="- topic/p ">trueに設定すると、キーの回転が有効になり、異なるキーを使用してコンテンツの一部を暗号化できます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">encrypt.keys.rotation.key.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">キーの回転が有効な場合に、コンテンツの暗号化に使用される回転したキーのシーケンス。 キーが指定されていない場合、キーはランダムに生成されます。 キーの長さは16バイトで、16進数値で指定します。 </p> <p class="- topic/p ">16進数値の間の空白はオプションです。 <i class="+ topic/ph hi-d/i ">nは</i> 、1から始まる単調に増加する必要があります。 複数のキーを指定した場合、キーは指定された順序で循環されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.rotation.interval</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コンテンツサンプルの暗号化に回転キーを使用する間隔（秒）を指定します。 </p> <p class="- topic/p ">コンテンツ内のこの時間が暗号化された後、次のローテーションキーが使用されます。 キーの回転が有効で間隔が指定されていない場合、キーは15分ごとに回転されます。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.serverless</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">trueの場合、ライセンスを取得できるライセンスサーバはありません。 ライセンスは、埋め込むか、帯域外で取得する必要があります。 指定しない場合の初期設定はfalseです。 Adobe Access Professionalでのみサポートされます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

