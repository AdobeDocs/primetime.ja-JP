---
title: 設定ファイルのプロパティ
description: 設定ファイルのプロパティ
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---


# 構成ファイルのプロパティ{#configuration-file-properties}

Media Packagerを実行する前に、Media Packagerのプロパティの値を指定します。 設定ファイルでは、次のプロパティを指定します。 * n*を含むプロパティ名の場合、*n*&#x200B;は、プロパティの各インスタンスの1から始まり増加する整数を表します。

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
   <td colname="2" class="- topic/entry ">FLV内のスクリプトデータを暗号化するかどうかを示します。 <i class="+ topic/ph hi-d/i "></i> onMetaDataおよびonXMPscript <i class="+ topic/ph hi-d/i "></i> のデータタグは、このオプションが有効になっている場合でも、暗号化されません。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.video.level</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ビデオ暗号化レベルを示します。 値highはすべてのビデオコンテンツを暗号化するために使用され、値mediumとlowはH.264コンテンツを含むF4Vファイルのビデオコンテンツの一部を暗号化するために使用されます。 </p> <p class="- topic/p ">値= <span class="codeph">高 | medium | low</span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.secondsUnencrypted</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">この値が0より大きい場合、ファイルの先頭のコンテンツの指定秒数は暗号化されません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.asymmetric.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">キーの暗号化に使用するライセンスサーバー証明書ファイルです。 <span class="codeph"> encrypt.keys.asymmetric.certfile</span>プロパティは、証明書のみを含むファイルを指定します（PEM形式またはDER形式を使用できます）。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">encrypt.keys.policyFile.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">このプロパティは、コンテンツに適用するポリシーのリストを繰り返し作成するために使用されます。 <span class="codeph"> nis</span> は1以上の整数です。クライアントはデフォルトで最初のインスタンスを使用します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.serverurl</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスサーバーのURLです。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.servercert</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスサーバーのトランスポート証明書です。 このプロパティは、証明書のみを含む<span class="filepath"> .cer</span>ファイルを指定します（PEM形式またはDER形式を使用できます）。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.sign.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コンテンツに署名するためのパッケージャーの秘密鍵証明書を含むPKCS12ファイルです。 <span class="codeph"> encrypt.sign.certfile</span>は、証明書と秘密鍵を含む<span class="filepath"> .pfx</span>ファイルを参照する必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.sign.certpass</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p "><span class="codeph"> encrypt.sign.certfile</span>で指定されたファイルの保護に使用されるパスワードです。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.minServerVersion</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">パッケージ化するコンテンツのライセンスを発行するのに必要な最小限のサーバーバージョンを設定します。 x (Adobeアクセスx.0)を指定します。x =メジャーリリース番号 Adobeアクセス3.0より前のサーバーは、この設定をサポートしていません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">encrypt.keys.policyFile.n.domain.transportcert</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ポリシー<span class="+ topic/ph pr-d/codeph codeph"> encrypt.keys.policyFile.n</span>で、<span class="+ topic/ph pr-d/codeph codeph"> encrypt.license.servercert</span>で指定されているのとは異なるトランスポート証明書を使用するサーバーとのドメイン登録が必要な場合は、ドメイントランスポート証明書を指定する必要があります。 </p> <p class="- topic/p ">このプロパティは、証明書のみを含むファイルを指定します（PEM形式またはDER形式を使用できます）。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.licenseKey</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスキーを指定します。 キーが指定されていない場合、キーはランダムに生成されます。 キーの回転が有効になっていない場合は、コンテンツの暗号化に使用するキーです。 </p> <p class="- topic/p ">キーの回転が有効な場合、このキーを使用して回転キーが保護されます。 キーは16バイトの長さで、16進数値で指定する必要があります。 16進数値の間に空白文字を入力することは省略可能です。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.rotation.enable</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">キーの回転を有効にするかどうかを指定します。 false（デフォルト）に設定した場合、キーの回転は無効になり、マスターCEKを使用してコンテンツ内のすべてのサンプルが暗号化されます。 </p> <p class="- topic/p ">trueに設定すると、キーの回転が有効になり、別のキーを使用してコンテンツの一部を暗号化できます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">encrypt.keys.rotation.key.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">キーの回転が有効な場合に、コンテンツの暗号化に使用される回転したキーのシーケンス。 キーが指定されていない場合、キーはランダムに生成されます。 キーは16バイトの長さで、16進数値で指定する必要があります。 </p> <p class="- topic/p ">16進数値の間に空白文字を入力することは省略可能です。 <i class="+ topic/ph hi-d/i ">1</i> から始まる単調に増加する必要があります。複数のキーを指定した場合、キーは指定された順序で循環します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.rotation.interval</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コンテンツサンプルの暗号化に回転キーを使用する間隔（秒）を指定します。 </p> <p class="- topic/p ">コンテンツ内のこの時間が暗号化された後、次のローテーションキーが使用されます。 キーの回転が有効で間隔が指定されていない場合、キーは15分ごとに回転します。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.serverless</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">trueの場合、ライセンスを取得できるライセンスサーバはありません。 ライセンスは、埋め込むか、帯域外で取得する必要があります。 指定しない場合の初期設定はfalseです。 Adobe Access Professionalでのみサポート。 </p> </td> 
  </tr> 
 </tbody> 
</table>

