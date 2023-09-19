---
title: 設定ファイルのプロパティ
description: 設定ファイルのプロパティ
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---

# 設定ファイルのプロパティ {#configuration-file-properties}

Media Packager を実行する前に、Media Packager のプロパティの値を指定します。 設定ファイルで、次のプロパティを指定します。 * n*を含むプロパティ名の場合、 *n* は、プロパティの各インスタンスに対して 1 から始まり増加する整数を表します。

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
   <td colname="2" class="- topic/entry ">FLV でスクリプトデータを暗号化するかどうかを示します。 <i class="+ topic/ph hi-d/i ">onMetaData</i> および <i class="+ topic/ph hi-d/i ">onXMP</i> スクリプトデータタグは、このオプションが有効になっている場合でも暗号化されません。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.video.level</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ビデオの暗号化レベルを示します。 値が high の場合はすべてのビデオコンテンツを暗号化し、medium と low の場合は H.264 コンテンツを含む F4V ファイルのビデオコンテンツの一部を暗号化します。 </p> <p class="- topic/p ">値= <span class="codeph"> 高 |中 | low</span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.secondsUnencrypted</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">値が 0 より大きい場合、ファイルの開始時のコンテンツの指定秒数は暗号化されません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.asymmetric.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">キーの暗号化に使用するライセンスサーバー証明書ファイルです。 The <span class="codeph"> encrypt.keys.asymmetric.certfile</span> プロパティは、証明書のみを含むファイルを指定します（PEM または DER 形式が使用可能）。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">encrypt.keys.policyFile.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">このプロパティは、コンテンツに適用するポリシーのリストを作成するために繰り返し使用されます。 <span class="codeph"> n</span> は 1 以上の整数です。 クライアントは、デフォルトで最初のインスタンスを使用します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.serverurl</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスサーバーの URL。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.servercert</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスサーバーのトランスポート証明書です。 このプロパティは、 <span class="filepath"> .cer</span> 証明書のみを含むファイル（PEM または DER 形式が使用可能）。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.sign.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コンテンツに署名するためのパッケージャ資格情報を含む PKCS12 ファイル。 The <span class="codeph"> encrypt.sign.certfile</span> は、 <span class="filepath"> .pfx</span> 証明書と秘密鍵を含むファイル。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.sign.certpass</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">指定したファイルの保護に使用するパスワード <span class="codeph"> encrypt.sign.certfile</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.minServerVersion</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">パッケージ化するコンテンツのライセンスを発行するために必要な最小のサーバーバージョンを設定します。 x (Adobeアクセス x.0) を指定します。x =メジャーリリース番号です。 Adobeアクセス 3.0 より前のサーバーは、この設定をサポートしていません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">encrypt.keys.policyFile.n.domain.transportcert</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ポリシーの場合 <span class="+ topic/ph pr-d/codeph codeph"> encrypt.keys.policyFile.n</span> では、で指定されたものとは異なるトランスポート証明書を使用するサーバーとのドメイン登録が必要です <span class="+ topic/ph pr-d/codeph codeph"> encrypt.license.servercert</span>の場合は、ドメイントランスポート証明書を指定する必要があります。 </p> <p class="- topic/p ">このプロパティは、証明書のみを含むファイルを指定します（PEM または DER 形式が使用可能）。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.licenseKey</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスキーを指定します。 キーが指定されていない場合、キーはランダムに生成されます。 キーのローテーションが有効でない場合、このキーがコンテンツの暗号化に使用されます。 </p> <p class="- topic/p ">キーの回転が有効な場合、このキーは回転キーを保護するために使用されます。 キーの長さは 16 バイトで、16 進数値で指定する必要があります。 16 進数値の間の空白はオプションです。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.rotation.enable</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">キーの回転を有効にするかどうかを指定します。 false（デフォルト）に設定した場合、キーのローテーションは無効になり、マスター CEK を使用してコンテンツ内のすべてのサンプルが暗号化されます。 </p> <p class="- topic/p ">true に設定すると、キーのローテーションが有効になり、異なるキーを使用してコンテンツの一部を暗号化できます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">encrypt.keys.rotation.key.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">キーのローテーションが有効な場合に、コンテンツの暗号化に使用するキーを回転したシーケンス。 キーが指定されていない場合、キーはランダムに生成されます。 キーの長さは 16 バイトで、16 進数値で指定する必要があります。 </p> <p class="- topic/p ">16 進数値の間の空白はオプションです。 <i class="+ topic/ph hi-d/i ">n</i> は、1 から始まる単調に増加する必要があります。 複数のキーを指定した場合、キーは指定された順序で順番に切り替えられます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.rotation.interval</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">回転キーを使用してコンテンツサンプルを暗号化する間隔（秒）を指定します。 </p> <p class="- topic/p ">コンテンツ内のこの時間が暗号化された後、次のローテーションキーが使用されます。 キーの回転が有効で間隔が指定されていない場合、キーは 15 分ごとに回転されます。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.serverless</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">true の場合、ライセンスを取得できるライセンスサーバはありません。 ライセンスを埋め込むか、帯域外で取得する必要があります。 指定しない場合のデフォルト値は false です。 Adobe Access Professionalでのみサポートされています。 </p> </td> 
  </tr> 
 </tbody> 
</table>
