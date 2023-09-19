---
title: 概要
description: 概要
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1315'
ht-degree: 0%

---

# DRM Media Packager {#media-packager}

Media Packager ( [!DNL AdobePackager.jar]) を使用して、コンテンツに適用する DRM ポリシーを指定したり、暗号化するコンテンツの一部を指定したりできます。 例えば、パッケージャーがビデオデータを暗号化するが、オーディオデータは暗号化しないように指定できます。

実行する前に [!DNL AdobePackager.jar]を設定する場合は、設定ファイルの「 Media Packager のプロパティ」セクションでプロパティを設定する必要があります。

>[!NOTE]
>
>また、すべての Media Packager プロパティをコマンドラインから指定することもできます。

## Media Packager のコマンドラインの使用 {#media-packager-command-line-usage}

**1 つのファイルをパッケージ化：**

```
java -jar AdobePackager.jar  
<i class="+ topic ph hi-d="" i "="">
  source  
 <i class="+ topic ph hi-d="" i "="">
   dest [ 
  <i class="+ topic ph hi-d="" i "="">
    options] 
  </i class="+ topic> 
 </i class="+ topic> 
</i class="+ topic>
```

* `source`  — 暗号化するファイルの名前。
* `dest`  — 生成される暗号化ファイルの名前。

  ディレクトリを指定した場合、暗号化されたファイルは、ソースファイルと同じファイル名で指定されたディレクトリに自動的に保存されます。 ただし、ソースファイルを含む宛先ディレクトリは指定できません。

**同じキーで複数のファイルをパッケージ化** （マルチビットレートサポートの場合）:

```
java -jar AdobePackager.jar  
<i class="+ topic ph hi-d="" i "="">
  sourcefiles  
 <i class="+ topic ph hi-d="" i "="">
   dest-directory [ 
  <i class="+ topic ph hi-d="" i "="">
    options] 
  </i class="+ topic> 
 </i class="+ topic> 
</i class="+ topic>
```

* `sourcefiles`  — 暗号化するファイルの空白区切りのソースエントリの一連。
* `dest-directory`  — 暗号化されたコンテンツを書き込む宛先ディレクトリ。 暗号化されたファイルは、ソースファイルと同じファイル名を使用して、このディレクトリに自動的に保存されます。 ただし、宛先ディレクトリにソースファイルを含めることはできません。

**暗号化されたファイルに関する情報を表示します。**

```
java -jar AdobePackager.jar -d  
<i class="+ topic ph hi-d="" i "="">
  encryptedfile [-e] [-m] 
</i class="+ topic>
```

**メタデータファイルに関する情報の表示：**

```
java -jar AdobePackager.jar -dm <metadatafile> [-e]
```

* `metadatafile` は [!DNL .metadata] DRM メタデータを含むファイル。

>[!NOTE]
>
>パッケージ化中に、Media Packager で [!DNL .header] ファイルに書き込まれます。 次の手順で [!DNL .header] ファイルを使用する場合は、 `-h` オプションを選択します。

**表 3：オプション**

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_wgz_spy_n4">  
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">コマンドラインオプション </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">説明 </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-c <span class="+ topic/ph pr-d/codeph codeph"> configfile </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">設定ファイルの名前と場所を指定します。 </p> <p class="- topic/p ">名前や場所を指定しない場合、DRM Media Packager は <span class="filepath"> flashaccesstools.properties </span> 現在の作業ディレクトリ内。 </p> <p>注：コマンドラインで指定するオプションは、設定ファイルで指定するオプションよりも優先されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-d <span class="+ topic/ph pr-d/codeph codeph"> encryptedfile </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">既にパッケージ化されているファイルに関する情報を表示できます。 </p> <p class="- topic/p ">ソースファイルと宛先ファイルは不要です。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-dm <span class="+ topic/ph pr-d/codeph codeph"> metadatafile </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">既存のメタデータに関する情報を表示できます。 </p> <p class="- topic/p ">ソースファイルと宛先ファイルは不要です。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-e </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">このオプションを <span class="codeph"> -d </span> オプション。 </p> <p class="- topic/p ">ファイルは、暗号化されたファイルがファイル名と DRM ポリシー識別子を使用して配置されるのと同じディレクトリに自動的に作成されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-h </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">このオプションを <span class="codeph"> -d </span> オプション。 </p> <p class="- topic/p ">ファイルは、暗号化されたファイルと同じディレクトリに自動的に作成され、ファイル名と拡張子が付きます <span class="filepath"> .header </span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-i <span class="+ topic/ph pr-d/codeph codeph"> contentID </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コンテンツのこのセグメントの一意の識別子を指定します。 </p> <p class="- topic/p ">識別子を指定しない場合、宛先ファイル名が自動的に適用されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-k <span class="+ topic/ph pr-d/codeph codeph"> key </span>= <span class="+ topic/ph pr-d/codeph codeph"> 値 </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コンテンツメタデータに追加するカスタムキー/値を指定します。 </p> <p class="- topic/p ">複数の <span class="codeph"> -k </span> オプション。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-m </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">このオプションを <span class="codeph"> -d </span> オプション。 </p> <p class="- topic/p ">ファイルは、暗号化されたファイルと同じディレクトリに、ファイル名と <span class="codeph"> .metadata </span> 拡張子。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-noprompt </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">宛先ファイルを上書きするかどうかを確認しないでください。 </p> <p class="- topic/p ">宛先ファイルが既に存在し、 <span class="codeph"> -o </span> が設定されていない場合、エラーが発生します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-o </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">既に存在しない限り、プロンプトを表示せずに宛先ファイルを上書きします。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-p <span class="+ topic/ph pr-d/codeph codeph"> filename [domain-transport-cert] </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">DRM ポリシーを含むファイルの名前を指定します。 </p> <p class="- topic/p ">DRM ポリシーで、プロパティファイルで指定したもの以外のトランスポート証明書を使用するサーバーとのドメイン登録が必要な場合は、ドメイントランスポート証明書を指定する必要があります。 </p> <p class="- topic/p ">複数の <span class="codeph"> -p </span> オプション。 クライアントは、デフォルトでは常に最初のオプションを適用します。 コマンドラインで指定した値は、設定ファイルで指定した値よりも優先されます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 設定プロパティ {#configuration-properties}

<!--<a id="section_3081C60BE54D47569FD1E3793513A2D9"></a>-->

>[!NOTE]
>
>* n*を含むプロパティ名の場合、 *n* は、プロパティの各インスタンスに対して 1 から始まり増加する整数を表します。

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
   <td colname="2" class="- topic/entry "> <p>mp4s でスクリプトデータを暗号化するかどうかを示します。 </p> <p><i class="+ topic/ph hi-d/i ">onMetaData</i> および <i class="+ topic/ph hi-d/i ">onXMP</i> このオプションを有効にしても、スクリプトデータタグは暗号化されません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.video.level</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ビデオの暗号化レベルを示します。 </p> <p class="- topic/p ">値： <span class="codeph"> 高</span> はすべてのビデオコンテンツを暗号化するために使用され、の値は <span class="codeph"> medium</span> および <span class="codeph"> 低</span> は、H.264 コンテンツを含む mp4 ファイルのビデオコンテンツの一部を暗号化するために使用されます。 </p> <p class="- topic/p ">値= <span class="codeph"> 高 |中 | low</span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.secondsUnencrypted</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">値が 0 より大きい場合、ファイルの先頭のコンテンツの指定秒数は暗号化されません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.asymmetric.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">キーの暗号化に使用するライセンスサーバー証明書ファイルです。 </p> <p class="- topic/p ">The <span class="codeph"> encrypt.keys.asymmetric.certfile</span> プロパティは、証明書のみを含むファイルを指定します（PEM または DER 形式が使用可能）。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">encrypt.keys.policyFile.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">このプロパティは、コンテンツに適用する DRM ポリシーのリストを作成するために繰り返し使用されます。 <span class="codeph"> n</span> は、1 以上の値を持つ整数を表します。 クライアントは、デフォルトで最初のインスタンスを使用します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.serverurl</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスサーバーの URL </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.servercert</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスサーバーのトランスポート証明書です。 </p> <p class="- topic/p ">このプロパティは、 <span class="filepath"> .cer</span> 証明書のみを含むファイル（PEM または DER 形式が使用可能）。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.sign.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コンテンツに署名するための Packager の資格情報を含む PKCS12 ファイル。 </p> <p class="- topic/p ">The <span class="codeph"> encrypt.sign.certfile</span> を参照する必要がある <span class="filepath"> .pfx</span> 証明書と秘密鍵を含むファイル。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.sign.certpass</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">指定したファイルを保護するために適用できるパスワード。 <span class="codeph"> encrypt.sign.certfile</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.minServerVersion</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">パッケージ化するコンテンツのライセンスを発行する際に必要な最小サーバーバージョンを設定します。 </p> <p class="- topic/p ">x （Primetime DRM x.0 の場合）を指定します。x はメジャーリリース番号を表します。 Adobe Primetimeバージョン 3.0 より前のバージョンのサーバーでは、この設定はサポートされていません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">encrypt.keys.policyFile.n .domain.transportcert </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">DRM ポリシーの場合 <span class="+ topic/ph pr-d/codeph codeph"> encrypt.keys.policyFile.n</span> では、で指定した以外のトランスポート証明書をサポートするサーバーとのドメイン登録が必要です。 <span class="+ topic/ph pr-d/codeph codeph"> encrypt.license.servercert</span>の場合は、ドメイントランスポート証明書のニーズを指定する必要があります。 </p> <p class="- topic/p ">このプロパティは、証明書のみを含むファイルを指定します（PEM または DER 形式が使用可能）。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.licenseKey</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスキーを指定します。 </p> <p class="- topic/p ">キーを指定しない場合、キーはランダムに生成されます。 キーのローテーションを有効にしない場合は、このキーを使用してコンテンツを暗号化できます。 </p> <p class="- topic/p ">キーの回転を有効にすると、このキーを使用して回転キーを保護できます。 キーの長さは 16 バイトで、16 進数で指定する必要があります。 16 進数値の間の空白はオプションです。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.rotation.enable</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">キーの回転を有効にするかどうかを指定します。 </p> <p class="- topic/p ">false に設定した場合（デフォルト設定）、キーの回転は無効になり、マスター CEK を使用してコンテンツ内のすべてのサンプルが暗号化されます。 </p> <p class="- topic/p ">true に設定した場合、キーのローテーションが有効になり、別のキーを使用して任意のコンテンツのセグメントを暗号化できます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">encrypt.keys.rotation.key.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">キーのローテーションが有効な場合にコンテンツを暗号化するために指定できる、回転されたキーのシーケンス。 </p> <p class="- topic/p ">キーを指定しない場合、キーはランダムに生成されます。 キーの長さは 16 バイトで、16 進数値で指定する必要があります。 </p> <p class="- topic/p ">16 進数値の間の空白はオプションです。 <i class="+ topic/ph hi-d/i ">n</i> は、1 から始まる単調に増加する必要があります。 複数のキーを指定する場合、キーは指定した順序で順番に切り替えられます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.rotation.interval</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コンテンツサンプルを暗号化するためにローテーションキーを適用できる時間間隔を秒単位で指定します。 </p> <p class="- topic/p ">コンテンツが暗号化された時間間隔が経過した後、次の回転キーが適用されます。 キーの回転を有効にしているが、時間間隔を指定していない場合、キーは 15 分ごとに自動的に回転されます。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.serverless</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">このオプションを true に設定した場合、ライセンスを取得できるライセンスサーバは使用できません。 </p> <p class="- topic/p ">ライセンスを埋め込むか、帯域外で取得する必要があります。 別の値を指定しない限り、デフォルト値は false に設定されます。 このオプションは、Primetime DRM Professional でのみサポートされます。 </p> </td> 
  </tr> 
 </tbody> 
</table>
