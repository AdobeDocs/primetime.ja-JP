---
description: 'null'
seo-description: 'null'
seo-title: 概要
title: 概要
uuid: f4474837-9460-479d-89c2-dd697e0fb997
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc

---


# DRM Media Packager {#media-packager}

Media Packager( [!DNL AdobePackager.jar])を使用して、コンテンツに適用するDRMポリシーを指定し、コンテンツのどの部分を暗号化するかを指定します。 例えば、パッケージャーでビデオデータを暗号化するが、オーディオデータは暗号化しないように指定できます。

実行する前に、設 [!DNL AdobePackager.jar]定ファイルの「Media Packagerのプロパティ」セクションでプロパティを設定する必要があります。

>[!NOTE]
>
>また、コマンドラインからMedia Packagerのすべてのプロパティを指定することもできます。

## Media Packagerのコマンドラインでの使用 {#media-packager-command-line-usage}

**1つのファイルのパッケージ化：**

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
* `dest`  — 生成される暗号化されたファイルの名前。

   ディレクトリを指定すると、暗号化されたファイルは、ソースファイルと同じファイル名で指定したディレクトリに自動的に保存されます。 ただし、ソースファイルを含む宛先ディレクトリを指定することはできません。

**複数のファイルを同じキーでパッケージ化する** （マルチビットレートをサポートする場合）:

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

* `sourcefiles`  — 暗号化するファイルの空白で区切られた一連のソースエントリ。
* `dest-directory`  — 暗号化されたコンテンツを書き込む宛先ディレクトリ。 暗号化されたファイルは、ソースファイルと同じファイル名を使用して、このディレクトリに自動的に保存されます。 ただし、宛先ディレクトリにソースファイルを含めることはできません。

**暗号化されたファイルに関する情報の表示：**

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

* `metadatafile` は、DRMメタデ [!DNL .metadata] ータを含むファイルです。

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>パッケージ化中に、Media Packagerでデフォルトでファイルを生成できな [!DNL .header] くなりました。 ファイルを生成する [!DNL .header] には、パッケージ化時にこ `-h` のオプションを使用します。

**表4:オプション**

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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">設定ファイルの名前と場所を指定します。 </p> <p class="- topic/p ">名前または場所を指定しない場合、DRM Media Packagerは現在の作業ディレクトリ内で <span class="filepath"> flashaccesstools.properties </span> を検索します。 </p> <p>注意： コマンドラインで指定したオプションは、設定ファイルで指定したオプションよりも優先されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-d encryptedfile- <span class="+ topic/ph pr-d/codeph codeph"> d encryptedfile </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">既にパッケージ化されているファイルに関する情報を表示できます。 </p> <p class="- topic/p ">ソースファイルと宛先ファイルは不要です。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-dmメタデータフ <span class="+ topic/ph pr-d/codeph codeph"> ァイル </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">既存のメタデータに関する情報を表示できます。 </p> <p class="- topic/p ">ソースファイルと宛先ファイルは不要です。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-e </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">このオプションを —dオプションと組み合わせて適用すると、パッケージ化されたファイルからDRMポリシー <span class="codeph"> が抽出さ </span> れます。 </p> <p class="- topic/p ">ファイルは、暗号化されたファイルが存在するディレクトリと同じディレクトリに、ファイル名とDRMポリシー識別子を使用して自動的に作成されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-h </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">このオプションを —dオプションと組み合わせて適用すると、パッケージ化されたファイルからDRMヘッダ <span class="codeph"> ーが抽出さ </span> れます。 </p> <p class="- topic/p ">ファイルは、暗号化されたファイルと同じディレクトリに自動的に作成され、ファイル名と拡張子 <span class="filepath"> .headerが付きま </span>す。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-i <span class="+ topic/ph pr-d/codeph codeph"> contentID </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">このコンテンツのセグメントの一意の識別子を指定します。 </p> <p class="- topic/p ">識別子を指定しない場合は、デストファイル名が自動的に適用されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-kキ <span class="+ topic/ph pr-d/codeph codeph"> ー </span>= <span class="+ topic/ph pr-d/codeph codeph"> 値 </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コンテンツメタデータに追加するカスタムキー/値を指定します。 </p> <p class="- topic/p ">複数の —kオプション <span class="codeph"> を指定で </span> きます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-m </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">このオプションを —dオプションと組み合わせて適用する場合は、パッケージ化されたファイルからメタデ <span class="codeph"> ータを抽出 </span> します。 </p> <p class="- topic/p ">ファイルは、暗号化されたファイルと同じディレクトリに、ファイル名と <span class="codeph"> .metadata拡張子を持つファイルとして自動的に作成さ </span> れます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-noprompt </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コピー先のファイルを上書きするかどうかを確認しない。 </p> <p class="- topic/p ">コピー先のファイルが既に存在し、 <span class="codeph"> -oが設定さ </span> れていない場合は、エラーが発生します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-o </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保存先のファイルが既に存在しない場合は、プロンプトを表示せずに上書きします。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-p <span class="+ topic/ph pr-d/codeph codeph"> filename [domain-transport-cert] </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">DRMポリシーを含むファイルの名前を指定します。 </p> <p class="- topic/p ">DRMポリシーで、プロパティファイルで指定した以外のトランスポート証明書を使用するサーバーとのドメイン登録が必要な場合は、ドメイントランスポート証明書を指定する必要があります。 </p> <p class="- topic/p ">複数の —pオプション <span class="codeph"> を指定で </span> きます。 クライアントは、デフォルトで常に最初のオプションを適用します。 コマンドラインで指定した値は、設定ファイルで指定した値よりも優先されます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 設定プロパティ {#configuration-properties}

<!--<a id="section_3081C60BE54D47569FD1E3793513A2D9"></a>-->

>[!NOTE]
>
>* n*を含むプロパティ名の場合、 *n* は1で始まり、プロパティの各インスタンスで増加する整数を表します。

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
   <td colname="2" class="- topic/entry "> <p>mp4sでスクリプトデータを暗号化するかどうかを示します。 </p> <p><i class="+ topic/ph hi-d/i ">onMetaDataと</i> onXMP <i class="+ topic/ph hi-d/i ">Scriptのデータタグは</i> 、このオプションを有効にした場合でも暗号化されません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.video.level</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ビデオの暗号化レベルを示します。 </p> <p class="- topic/p ">値がhighの場合、すべてのビデ <span class="codeph"> オコンテンツが暗号化され、</span> medium <span class="codeph"></span><span class="codeph"></span> とlowの場合、H.264コンテンツを含むmp4ファイルのビデオコンテンツの一部が暗号化されます。 </p> <p class="- topic/p ">value = <span class="codeph"> high| medium|低</span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.contents.secondsUnencrypted</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">値が0より大きい場合、ファイルの先頭の指定された秒数の内容は暗号化されません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.asymmetric.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">キーの暗号化に使用するライセンスサーバー証明書ファイル。 </p> <p class="- topic/p ">encrypt.keys. <span class="codeph"> asymmetric.certfileプロパティは、証明書のみを含むファイルを指定します</span> （PEMまたはDER形式を使用できます）。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">encrypt.keys.policyFile.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">このプロパティは、コンテンツに適用するDRMポリシーのリストを作成するために繰り返し使用されます。 <span class="codeph"> nは</span> 、値が1以上の整数を表します。 クライアントはデフォルトで最初のインスタンスを使用します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.serverurl</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスサーバーのURL </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.servercert</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスサーバーのトランスポート証明書。 </p> <p class="- topic/p ">このプロパティは、証明 <span class="filepath"> 書のみを含む</span> .cerファイルを指定します（PEMまたはDER形式を使用できます）。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.sign.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コンテンツに署名するためのパッケージャーの資格情報を含むPKCS12ファイルです。 </p> <p class="- topic/p ">encrypt.sign.certfile <span class="codeph"> は、証明書と秘密鍵を含む</span> .pfx <span class="filepath"> (.pfx</span> )ファイルを参照する必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.sign.certpass</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">encrypt.sign.certfileで指定したファイルの保護に適用できるパ <span class="codeph"> スワードです</span>。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.minServerVersion</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">パッケージ化するコンテンツのライセンスを発行するために必要な最小のサーバーバージョンを設定します。 </p> <p class="- topic/p ">x（Primetime DRM x.0の場合）を指定します。xはメジャーリリース番号を表します。 Adobe Primetimeバージョン3.0より前のバージョンのサーバーでは、この設定はサポートされません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">encrypt.keys.policyFile.n .domain.transportcert </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">DRMポリシー <span class="+ topic/ph pr-d/codeph codeph"> encrypt.keys.policyFile.nで、</span><span class="+ topic/ph pr-d/codeph codeph"></span>encrypt.license.servercertで指定した以外のトランスポート証明書をサポートするサーバーとのドメイン登録が必要な場合は、ドメイントランスポート証明書の必要な要件を指定する必要があります。 </p> <p class="- topic/p ">このプロパティは、証明書のみを含むファイルを指定します（PEMまたはDER形式を使用できます）。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.licenseKey</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスキーを指定します。 </p> <p class="- topic/p ">キーを指定しない場合、キーはランダムに生成されます。 キーの回転を有効にしない場合は、このキーを使用してコンテンツを暗号化できます。 </p> <p class="- topic/p ">キーの回転を有効にすると、このキーを使用して回転キーを保護できます。 キーは16バイトの長さで、16進数値で指定する必要があります。 16進数値の間の空白はオプションです。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.rotation.enable</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">キーの回転を有効にするかどうかを指定します。 </p> <p class="- topic/p ">デフォルト設定であるfalseに設定した場合、キーの回転は無効になり、マスターCEKを使用してコンテンツ内のすべてのサンプルが暗号化されます。 </p> <p class="- topic/p ">trueに設定すると、キーの回転が有効になり、異なるキーを使用して任意のコンテンツのセグメントを暗号化できます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">encrypt.keys.rotation.key.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">回転キーのシーケンス。キーの回転が有効な場合に、コンテンツの暗号化に指定できます。 </p> <p class="- topic/p ">キーを指定しない場合、キーはランダムに生成されます。 キーの長さは16バイトで、16進数値で指定します。 </p> <p class="- topic/p ">16進数値の間の空白はオプションです。 <i class="+ topic/ph hi-d/i ">nは</i> 、1から始まる単調に増加する必要があります。 複数のキーを指定すると、指定した順序でキーが循環されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.keys.rotation.interval</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コンテンツサンプルを暗号化するためにローテーションキーを適用できる時間間隔を秒単位で指定します。 </p> <p class="- topic/p ">コンテンツが暗号化された時間の経過後、次の回転キーが適用されます。 キーの回転を有効にしているが、時間の間隔を指定していない場合、キーは15分ごとに自動的に回転されます。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> encrypt.license.serverless</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">このオプションをtrueに設定すると、ライセンスを取得できるライセンスサーバは使用できなくなります。 </p> <p class="- topic/p ">ライセンスは、埋め込むか、帯域外で取得する必要があります。 別の値を指定しない限り、デフォルト値はfalseに設定されます。 このオプションは、Primetime DRM Professionalでのみサポートされます。 </p> </td> 
  </tr> 
 </tbody> 
</table>