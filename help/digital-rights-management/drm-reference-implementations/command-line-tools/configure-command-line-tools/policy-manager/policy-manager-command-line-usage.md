---
description: 'null'
seo-description: 'null'
seo-title: Policy Managerのコマンドラインでの使用
title: Policy Managerのコマンドラインでの使用
uuid: 9b17bc9a-0b1b-405f-a62b-0310c43c9255
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc

---


# Policy Managerのコマンドラインでの使用 {#policy-manager-command-line-usage}

```
java -jar AdobePolicyManager.jar  
<i class="+ topic ph hi-d="" i "="">
  command filename [options] 
</i class="+ topic>
```

**表1:コマンド**

| コマンド | 説明 |
|---|---|
| `new` | 新しいDRMポリシーを作成します |
| `detail` | 既存のDRMポリシーについて説明します |
| `update` | 既存のDRMポリシーを更新します |

**表2:オプション**

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_q5h_cpy_n4">  
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">コマンドラインオプション </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">説明 </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -c configfile </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">設定ファイルの名前と場所を指定します。 </p> <p class="- topic/p ">名前または場所を指定しない場合、DRM Policy Managerは現在の作業ディレクトリ内で <span class="filepath"> flashaccesstools.properties </span> を検索します。 </p> <p>注意： コマンドラインで指定したオプションは、設定ファイルで指定したオプションよりも優先されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コピー先のファイルが存在する場合は、プロンプトを表示せずにファイルを上書きできます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -noprompt </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コピー先のファイルを上書きするかどうかを確認しない。 コピー先のファイルが存在し、 <span class="codeph"> -oが設定さ </span> れていない場合は、エラーが発生します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -root </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">DRMポリシーにルートライセンスがあることを示します。 </p> <p class="- topic/p ">このオプションは、アップデートには使用できません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -e日 </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスが有効になる前の日付。 </p> <p>日付は、 <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-ddまたは </span> yyyy-mm-dd-h24:min:secの形式で指定でき <span class="+ topic/ph pr-d/codeph codeph"></span> ます。 例えば、2008年12月1日の午前0時は2008-12-1または2008-12-1-00:00:00のように指定します。 </p> <p> 
     <ul id="ul_D5DB5044756D4BD6A734813971598425"> 
      <li id="li_B6BD62A524384060A9DDA14FF50936FA">-sの値（存在する場合）より大きい値を <span class="codeph"> 指定する必 </span> 要があります。 </li> 
      <li id="li_C3C5AD0231A240EC9AC57685B9206E8D">このオプションは —rと共に適用 <span class="codeph"> できませ </span>ん。 </li> 
      <li id="li_3790E2F829A149979BF44E0914CFF431">DRMポリシーを更新する際に終了日を削除するには、日付を指定せずに —e <span class="codeph"> を適 </span> 用してください。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -r分 </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツが有効な時間（分単位）です。 </p> <p class="- topic/p ">DRMポリシーは、コンテンツがパッケージャーで保護されると有効になります。 </p> <p> 
     <ul id="ul_4690A0E4677A4DF6A006B7FCBD46F1BE"> 
      <li id="li_D1F098D44B494EE7A8647C0B62D5ACFA">値は負以外にする必要があります。 </li> 
      <li id="li_ADFDCB01EEE04B37AFA42886AAEF47EB">このオプションは、-eと共に適用するこ <span class="codeph"> とはできませ </span>ん。 </li> 
      <li id="li_E80563E68BEB43FC9E29A694594CAE01">DRMポリシーの更新時に期間を削除するには、分を指定せずに <span class="codeph"> -rを </span> 適用します。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -s日付 </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスが有効になった日付。 </p> <p>日付は、 <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-ddまたは </span> yyyy-mm-dd-h24:min:secの形式で指定でき <span class="+ topic/ph pr-d/codeph codeph"></span> ます。 例えば、 <span class="codeph"> 2008年12月1日の午前0 </span> 時は、2008-12-1または2008-12-1-00:00 <span class="codeph"></span> と入力します。 </p> <p> 
     <ul id="ul_D52B337F547F4E7AB87FE025236CA930"> 
      <li id="li_DBAE380972434DB1A4EF20D399038AB8">値が —eより小さい場合は、 <span class="codeph"> -eより小さい </span>値を指定します。 </li> 
      <li id="li_2899EC5559CF44319A4AC4ECD90A5B9A">このオプションは、 <span class="codeph"> -rと共に適用できませ </span>ん。 </li> 
      <li id="li_19861B1A64E44B95B649948EAB3E4085">DRMポリシーを更新する際に開始日を削除するには、日付を指定せずに —s <span class="codeph"> を使 </span> 用してください。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -w [&lt;分&gt;[,enableHS|disableHS]] </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">再生ウィンドウ。最初の再生からコンテンツを表示できる時間（分）です。 </p> <p>指定しない場合、または <span class="codeph"> -wを </span> 分単位で指定せずに使用する場合、再生ウィンドウに制限はありません。 値は負以外にする必要があります。 </p> <p>オプションのenableHS <span class="codeph"> または </span> disableHSフ <span class="codeph"> ラグは、ハ </span> ードストップを有効または無効にするかどうかを示します。 このフラグは、復号化コンテキストが再生ウィンドウの最後に破棄される（有効になる）か、破棄されない（無効になる）かを示します。 </p> <p>例えば、コンテンツを60分間のみ表示でき、ハードストップが必要になるように指定するには、次のように記述します。 
     <codeblock>
       -w&amp;nbsp;60,enableHS 
     </codeblock> </p> <p>注意： ハー <i>ドストップは</i> 、現在、Flash Player、AndroidおよびiOSではサポートされていません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -l分 </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスのキャッシュ期間は、ライセンスがサーバーから発行された後に、クライアントのライセンスストアにライセンスをキャッシュできる時間（分単位）です。 値は負以外にする必要があります。 </p> <p>-l 0を指定す <span class="codeph"> ると、ライセ </span> ンスのキャッシュが許可されません。 無制限のライセンスキャッシュを使用する場合は、 <span class="codeph"> -lを指 </span> 定します（分を指定しない）。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -ldate </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスキャッシュの終了日です。 </p> <p class="- topic/p ">これは、Primetime DRMサーバーがライセンスを発行した後に、クライアントがクライアントのライセンスストアにライセンスをキャッシュできる最終日を示します。 </p> <p>日付は次の形式で指定できます。 
     <ul id="ul_112DE7248A9C48B19520A3AA9E5D1F03"> 
      <li id="li_01C5400E78B84A3B8955972FBA875AAC"> <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd </span> </li> 
      <li id="li_AA13B1EFA07A4542A3DB41FA3320B143"> <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:sec </span> </li> 
     </ul>例えば、 <span class="codeph"> 2008年12月1日の午前0 </span> 時は、2008-12-1または2008-12-1-00:00 <span class="codeph"></span> と入力します。 無制限のライセンスキャッシ <span class="codeph"> ュを使用す </span> る場合は、分を指定せずに —lを適用する必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -authNS </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">認証名前空間。 </p> <p class="- topic/p ">このオプションを適用する場合、クライアントは、指定した権限によって発行されたユーザー名とパスワードを入力する必要があります。 </p> <p>このオプションを —xと共に適用するこ <span class="codeph"> とはできませ </span>ん。 </p> <p>このオプションは、更新に対しては使用できません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -x </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">匿名アクセスを許可します。 </p> <p class="- topic/p ">このオプションは、-authNSと共に適用するこ <span class="codeph"> とはできませ </span>ん。 </p> <p class="- topic/p ">このオプションは、更新に対しては使用できません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -air pubId </span>[: <span class="+ topic/ph pr-d/codeph codeph"> appId </span>[:[最小]:[ <span class="+ topic/ph pr-d/codeph codeph"> 最大 </span><span class="+ topic/ph pr-d/codeph codeph"></span>]] </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツを再生できるAIRアプリケーションのホワイトリストです。 </p> <p class="- topic/p ">このオプションを適用すると、このDRMポリシーで保護されたコンテンツにアクセスできる発行者、アプリケーションおよびバージョンを制限できます。 </p> <p class="- topic/p ">appIdを指定しない場合は <i class="+ topic/ph hi-d/i ">、発行者のpubIdのすべてのアプリケーションが</i>許可されます <i class="+ topic/ph hi-d/i "></i> 。 </p> <p>注意： 最小バ <i class="+ topic/ph hi-d/i ">ージョ</i> ン番号と最大バージョン番号は <i class="+ topic/ph hi-d/i "></i> 省略可能です。 </p> <p class="- topic/p ">複数の —airオプションを指 <span class="codeph"> 定して、複 </span> 数のアプリケーションを許可できます。 AIRまたはSWFアプリケーションを指定しない場合、すべてのアプリケーションがこのコンテンツにアクセスできます。 更新時に、リストからすべてのエントリを削除するには、残りの引数を指定せずに <span class="codeph"> -air </span> を適用します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -drmブラックリスト名 </span> / <i class="+ topic/ph hi-d/i ">ブラックリ</i><span class="+ topic/ph pr-d/codeph codeph"> スト </span><i class="+ topic/ph hi-d/i "></i><span class="+ topic/ph pr-d/codeph codeph"> 名/ペア </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツへのアクセスが制限されているDRMクライアント。 </p> <p class="- topic/p ">この値は、次の形式の名前と値のペアをコンマで区切って指定できます。 </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> または| release= stringValue </span> </p> <p class="- topic/p ">例えば、 <span class="codeph"> os=Win,release=2.0.1のように指定します </span>。 更新中に、リストからすべてのエントリを削除するには、残りの引数を <span class="codeph"> 指定せずに —drmBlacklist </span> を適用します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -drmLevel int </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツにアクセスするには、DRMクライアントに最小セキュリティレベルを割り当てる必要があることを示します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -opAnalog NO_PROTECTION| USE_IF_AVAILABLE|必須| NO_PLAYBACK| REQUIRED_ACP| REQUIRED_CGMSA| USE_IF_AVAILABLE_ACP| USE_IF_AVAILABLE_CGMSA </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">アナログ出力保護の制約 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -opDigital NO_PROTECTION| USE_IF_AVAILABLE|必須| NO_PLAYBACK </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">デジタル出力保護の制約 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -runtimeBlacklist name </span> value <i class="+ topic/ph hi-d/i ">/</i> pairs <span class="+ topic/ph pr-d/codeph codeph"></span><i class="+ topic/ph hi-d/i "></i><span class="+ topic/ph pr-d/codeph codeph"> value </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツへのアクセスが制限されているアプリケーションランタイムです。 </p> <p class="- topic/p ">値は、次の形式のコンマ区切りの名前：値のペアをサポートします。 </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> または|アプリケーション| release= stringValue </span> </p> <p class="- topic/p ">例えば、 <span class="codeph"> os=Win,release=2.0.1,application=AIRのように指定します </span>。 更新時に、リストからすべてのエントリを削除するには、残りの引数を <span class="codeph"> 指定せずに —runtimeBlacklist </span> を適用します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -runtimeLevel int </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツにアクセスするには、アプリケーションのランタイムに指定された最小セキュリティレベルが必要であることを示します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -swf url </span> </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -swf file=swf_file </span>、 <span class="+ topic/ph pr-d/codeph codeph"> time= max_time_to_verify </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツの再生が許可されるSWFアプリケーションのホワイトリストです。 </p> <p class="- topic/p ">複数の —swfオプションを指 <span class="codeph"> 定して、複数の </span> アプリケーションを許可することができます。 AIRまたはSWFアプリケーションを指定しない場合は、すべてのアプリケーションがこのコンテンツにアクセスできます。 </p> <p>更新時に、リストからすべてのエントリを削除するには、残りの引数を <span class="codeph"> 指定せずに —swf </span> を適用します。 SWFをハッシュ値で識別する場合は、ハッシュを計算するSWFファイルと、SWF検証の完了を許可する最大時間（秒）を指定する必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -k name=value </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">DRMポリシーに追加するカスタムキー/値を指定します。 </p> <p class="- topic/p ">複数の —kオプション <span class="codeph"> を指定で </span> きます。 更新時に、残りの引数を <span class="codeph"> 指定せずに —k </span> を適用すると、すべてのプロパティを削除できます。 データの解釈または処理は、Primetime DRMライセンスサーバーで管理されます。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -p name=value </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">各クライアント用に生成されたライセンスに表示されるカスタムプロパティを追加します。 </p> <p class="- topic/p ">複数の —pオプションを指 <span class="codeph"> 定して、複数 </span> のプロパティを追加できます。 すべてのプロパティを削除する場合は、更新中に残りの引数を <span class="codeph"> -p </span> しないで適用する必要があります。 このデータの解釈または処理は、クライアントアプリケーションの実装によって管理されます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> <span class="codeph"> -opOTAホワイトリスト=&lt;接続タイプ&gt; </span></span> </td> 
   <td colname="2" class="- topic/entry "> 大気(OTA)の出力保護の制約を越えて ホワイ <span class="codeph"> トリ </span> ストフィールドでは、ホワイトリストに含める接続タイプを指定し、&lt;connection types&gt;の形式は <span class="codeph"> [type(,type)*] </span>です。typeは次のいずれかです。ミラカスト、エアプレイ、ウィディ、デルナ </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -opResolution &lt;ファイル名&gt; </span> </td> 
   <td colname="2" class="- topic/entry "> <p>指定したファイルで定義される、解像度ベースの出力保護の制約。 </p> <p>このファイルのエンコードはJSONです。 形式設定の文法は、「解像度ベースの出力保護に <i>ついて」を参照してください</i>。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**例**

独自の設定プロパティファイルを使用して、コンテンツへの匿名アクセスを許可するポリシーを作成するには：

```
java -jar libs\AdobePolicyManager.jar new policy_test.pol -x -c my_configuration.properties
```
