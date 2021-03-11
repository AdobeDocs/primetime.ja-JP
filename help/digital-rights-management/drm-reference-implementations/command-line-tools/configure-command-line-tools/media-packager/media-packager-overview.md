---
title: 概要
description: 概要
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '1315'
ht-degree: 0%

---


# DRM Media Packager {#media-packager}

Media Packager([!DNL AdobePackager.jar])を使用して、コンテンツに適用するDRMポリシーを指定し、コンテンツの暗号化する部分を指定します。 例えば、パッケージャーでビデオデータを暗号化するが、オーディオデータは暗号化しないように指定できます。

[!DNL AdobePackager.jar]を実行する前に、設定ファイルの「Media Packagerのプロパティ」セクションでプロパティを設定する必要があります。

>[!NOTE]
>
>コマンドラインからMedia Packagerのすべてのプロパティを指定することもできます。

## Media Packagerのコマンドラインでの使用{#media-packager-command-line-usage}

**パッケージ1ファイル：**

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

   ディレクトリを指定すると、暗号化されたファイルは、ソースファイルと同じファイル名で指定したディレクトリに自動的に保存されます。 ただし、ソースファイルを含む宛先ディレクトリを指定することはできません。

**複数のファイルを同じキーでパッケージ化** （マルチビットレートをサポートする場合）:

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

* `sourcefiles`  — 暗号化するファイルのソースエントリを、空白で区切って並べたもの。
* `dest-directory`  — 暗号化されたコンテンツを書き込む宛先ディレクトリ。暗号化されたファイルは、ソースファイルと同じファイル名を使用して、自動的にこのディレクトリに保存されます。 ただし、宛先ディレクトリにソースファイルを含めることはできません。

**暗号化されたファイルに関する表示情報：**

```
java -jar AdobePackager.jar -d  
<i class="+ topic ph hi-d="" i "="">
  encryptedfile [-e] [-m] 
</i class="+ topic>
```

**メタデータファイルに関する表示情報：**

```
java -jar AdobePackager.jar -dm <metadatafile> [-e]
```

* `metadatafile` は、DRMメタデータを含む [!DNL .metadata] ファイルです。

>[!NOTE]
>
>パッケージ化中に、Media Packagerでデフォルトで[!DNL .header]ファイルを生成できなくなりました。 [!DNL .header]ファイルを生成するには、パッケージ化の際に`-h`オプションを使用します。

**表3:オプション**

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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">設定ファイルの名前と場所を指定します。 </p> <p class="- topic/p ">名前または場所を指定しない場合、DRM Media Packagerは、現在の作業ディレクトリ内の<span class="filepath"> flashaccesstools.properties </span>を検索します。 </p> <p>注意： コマンドラインで指定するオプションは、設定ファイルで指定するオプションよりも優先されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-d <span class="+ topic/ph pr-d/codeph codeph"> encryptedfile </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">既にパッケージ化されているファイルに関する表示情報を指定できます。 </p> <p class="- topic/p ">ソースファイルと保存先ファイルは不要です。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-dm <span class="+ topic/ph pr-d/codeph codeph"> metadatafile </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">既存のメタデータに関する表示情報を有効にします。 </p> <p class="- topic/p ">ソースファイルと保存先ファイルは不要です。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-e </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p "><span class="codeph"> -d </span>オプションと組み合わせてこのオプションを適用すると、パッケージファイルからDRMポリシーを抽出します。 </p> <p class="- topic/p ">ファイルは、暗号化されたファイルが存在するディレクトリと同じディレクトリに、ファイル名とDRMポリシー識別子を使用して自動的に作成されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-h </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p "><span class="codeph"> -d </span>オプションと組み合わせてこのオプションを適用すると、パッケージファイルからDRMヘッダーを抽出します。 </p> <p class="- topic/p ">ファイルは、暗号化されたファイルと同じディレクトリに自動的に作成され、ファイル名と拡張子<span class="filepath"> .header </span>が付けられます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-i <span class="+ topic/ph pr-d/codeph codeph"> contentID </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">このコンテンツセグメントの固有の識別子を指定します。 </p> <p class="- topic/p ">識別子を指定しない場合は、デストファイル名が自動的に適用されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-k <span class="+ topic/ph pr-d/codeph codeph">キー</span>= <span class="+ topic/ph pr-d/codeph codeph">値</span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コンテンツメタデータに追加するカスタムキー/値を指定します。 </p> <p class="- topic/p ">複数の<span class="codeph"> -k </span>オプションを指定できます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-m </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">このオプションを<span class="codeph"> -d </span>オプションと組み合わせて適用する場合は、パッケージ化されたファイルからメタデータを抽出します。 </p> <p class="- topic/p ">ファイルは、暗号化されたファイルと同じディレクトリに、ファイル名と<span class="codeph"> .metadata </span>拡張子を持つファイルとして自動的に作成されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-noprompt </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コピー先のファイルを上書きするかどうかを確認しない。 </p> <p class="- topic/p ">宛先ファイルが既に存在し、<span class="codeph"> -o </span>が設定されていない場合は、エラーが発生します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-o </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保存先のファイルが既に存在しない場合は、プロンプトを表示せずに上書きします。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-p <span class="+ topic/ph pr-d/codeph codeph"> filename [domain-transport-cert] </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">DRMポリシーを含むファイルの名前を指定します。 </p> <p class="- topic/p ">DRMポリシーで、プロパティファイルで指定したもの以外のトランスポート証明書を使用するサーバーとのドメイン登録が必要な場合は、ドメイントランスポート証明書を指定する必要があります。 </p> <p class="- topic/p ">複数の<span class="codeph"> -p </span>オプションを指定できます。 クライアントはデフォルトで常に最初のオプションを適用します。 コマンドラインで指定した値は、設定ファイルで指定した値よりも優先されます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 構成プロパティ{#configuration-properties}

<!--<a id="section_3081C60BE54D47569FD1E3793513A2D9"></a>-->

>[!NOTE]
>
>* n*を含むプロパティ名の場合、*n*&#x200B;は、1を含む整数を表し、プロパティの各インスタンスで増加します。

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
   <td colname="2" class="- topic/entry "> <p>mp4sでスクリプトデータを暗号化するかどうかを示します。 </p> <p><i class="+ topic/ph hi-d/i ">こ</i> のオプションを有効にし <i class="+ topic/ph hi-d/i "></i> た場合でも、onMetaDataおよびonXMPscriptのデータタグは暗号化されません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.video.level</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ビデオ暗号化レベルを示します。 </p> <p class="- topic/p ">すべてのビデオコンテンツを暗号化するには<span class="codeph"> high</span>の値を使用し、H.264コンテンツを含むmp4ファイルのビデオコンテンツの一部を暗号化するには<span class="codeph">medium</span>と<span class="codeph">low</span>を使用します。 </p> <p class="- topic/p ">値= <span class="codeph">高 | medium | low</span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.secondsUnencrypted</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">値が0より大きい場合、ファイルの先頭のコンテンツの指定秒数は暗号化されません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.asymmetric.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">キーの暗号化に使用するライセンスサーバー証明書ファイルです。 </p> <p class="- topic/p "><span class="codeph"> encrypt.keys.asymmetric.certfile</span>プロパティは、証明書のみを含むファイルを指定します（PEM形式またはDER形式を使用できます）。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">encrypt.keys.policyFile.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">このプロパティは、コンテンツに適用するDRMポリシーのリストを作成する際に繰り返し使用されます。 <span class="codeph"> 1</span> 以上の値を持つ整数を表します。クライアントはデフォルトで最初のインスタンスを使用します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.serverurl</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスサーバーのURL </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.servercert</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスサーバーのトランスポート証明書です。 </p> <p class="- topic/p ">このプロパティは、証明書のみを含む<span class="filepath"> .cer</span>ファイルを指定します（PEM形式またはDER形式を使用できます）。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.sign.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コンテンツに署名するためのパッケージャーの資格情報を含むPKCS12ファイルです。 </p> <p class="- topic/p "><span class="codeph"> encrypt.sign.certfile</span>は、証明書と秘密鍵を含む<span class="filepath"> .pfx</span>ファイルを参照する必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.sign.certpass</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p "><span class="codeph"> encrypt.sign.certfile</span>で指定されたファイルの保護に適用できるパスワードです。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.minServerVersion</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">パッケージ化するコンテンツのライセンスを発行するために必要な最小限のサーバーバージョンを設定します。 </p> <p class="- topic/p ">x（Primetime DRM x.0の場合）を指定します。xはメジャーリリース番号を表します。 Adobe Primetimeバージョン3.0より前のバージョンのサーバーでは、この設定はサポートされていません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">encrypt.keys.policyFile.n .domain.transportcert  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">DRMポリシー<span class="+ topic/ph pr-d/codeph codeph"> encrypt.keys.policyFile.n</span>で、<span class="+ topic/ph pr-d/codeph codeph"> encrypt.license.servercert</span>で指定した以外のトランスポート証明書をサポートするサーバーとのドメイン登録が必要な場合は、ドメイントランスポート証明書の必要性を指定する必要があります。 </p> <p class="- topic/p ">このプロパティは、証明書のみを含むファイルを指定します（PEM形式またはDER形式を使用できます）。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.licenseKey</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスキーを指定します。 </p> <p class="- topic/p ">キーを指定しない場合、キーはランダムに生成されます。 キーの循環を有効にしない場合は、このキーを使用してコンテンツを暗号化できます。 </p> <p class="- topic/p ">キーの回転を有効にすると、このキーを使用して回転キーを保護できます。 キーは16バイトの長さで、16進数値で指定する必要があります。 16進数値の間に空白文字を入力することは省略可能です。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.rotation.enable</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">キーの回転を有効にするかどうかを指定します。 </p> <p class="- topic/p ">デフォルト設定であるfalseに設定した場合、キーの回転は無効になり、マスターCEKを使用してコンテンツ内のすべてのサンプルが暗号化されます。 </p> <p class="- topic/p ">trueに設定すると、キーの回転が有効になり、異なるキーを使用して任意のコンテンツのセグメントを暗号化できます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">encrypt.keys.rotation.key.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">キーの回転が有効な場合に、コンテンツの暗号化に指定できる回転したキーのシーケンス。 </p> <p class="- topic/p ">キーを指定しない場合、キーはランダムに生成されます。 キーは16バイトの長さで、16進数値で指定する必要があります。 </p> <p class="- topic/p ">16進数値の間に空白文字を入力することは省略可能です。 <i class="+ topic/ph hi-d/i ">1</i> から始まる単調に増加する必要があります。複数のキーを指定する場合、指定した順にキーが循環します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.rotation.interval</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コンテンツサンプルを暗号化するために回転キーを適用できる時間間隔を秒単位で指定します。 </p> <p class="- topic/p ">コンテンツが暗号化された時間の間隔が経過した後、次のローテーションキーが適用されます。 キーの回転を有効にしたが、時間の間隔を指定しなかった場合、キーは15分ごとに自動的に回転します。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.serverless</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">このオプションをtrueに設定すると、ライセンスを取得できるライセンスサーバは使用できなくなります。 </p> <p class="- topic/p ">ライセンスは、埋め込むか、帯域外で取得する必要があります。 別の値を指定しない限り、デフォルト値はfalseに設定されます。 このオプションは、Primetime DRM Professionalでのみサポートされます。 </p> </td> 
  </tr> 
 </tbody> 
</table>