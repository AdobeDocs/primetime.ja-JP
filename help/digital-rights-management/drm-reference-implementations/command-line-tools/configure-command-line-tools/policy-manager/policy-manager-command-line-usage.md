---
description: 'null'
seo-description: 'null'
seo-title: Policy Managerコマンドラインの使用
title: Policy Managerコマンドラインの使用
uuid: 9b17bc9a-0b1b-405f-a62b-0310c43c9255
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '1228'
ht-degree: 0%

---


# Policy Managerコマンドラインの使用 {#policy-manager-command-line-usage}

```
java -jar AdobePolicyManager.jar  
<i class="+ topic ph hi-d="" i "="">
  command filename [options] 
</i class="+ topic>
```

**表1: コマンド**

| コマンド | 説明 |
|---|---|
| `new` | 新しいDRMポリシーを作成します |
| `detail` | 既存のDRMポリシーを説明します |
| `update` | 既存のDRMポリシーを更新します |

**表2: オプション**

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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">設定ファイルの名前と場所を指定します。 </p> <p class="- topic/p ">名前または場所を指定しない場合、DRM Policy Managerは、現在の作業ディレクトリ内で <span class="filepath"> flashaccesstools.properties </span> を検索します。 </p> <p>注意：  コマンドラインで指定するオプションは、設定ファイルで指定するオプションよりも優先されます。 </p> </td> 
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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">DRMポリシーにルートライセンスがあることを示します。 </p> <p class="- topic/p ">このオプションはアップデートには使用できません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -e日 </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスが有効になる前の日付。 </p> <p>日付は、 <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd </span> または <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:secの形式で指定でき </span> ます。 例えば、2008年12月1日の午前0時は、2008-12-1または2008-12-1-00:00:00と指定します。 </p> <p> 
     <ul id="ul_D5DB5044756D4BD6A734813971598425"> 
      <li id="li_B6BD62A524384060A9DDA14FF50936FA">値は —s（存在する場合）より大きい <span class="codeph"> 必要があ </span> ります。 </li> 
      <li id="li_C3C5AD0231A240EC9AC57685B9206E8D">このオプションを —rと共に適用するこ <span class="codeph"> とはできません </span>。 </li> 
      <li id="li_3790E2F829A149979BF44E0914CFF431">DRMポリシーを更新する際に終了日を削除するには、日付を指定せずに <span class="codeph"> -e </span> を適用します。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -r分 </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツが有効である時間（分）。 </p> <p class="- topic/p ">DRMポリシーは、コンテンツがパッケージャーで保護されると有効になります。 </p> <p> 
     <ul id="ul_4690A0E4677A4DF6A006B7FCBD46F1BE"> 
      <li id="li_D1F098D44B494EE7A8647C0B62D5ACFA">値は負以外にする必要があります。 </li> 
      <li id="li_ADFDCB01EEE04B37AFA42886AAEF47EB">このオプションを —eと共に適用することはでき <span class="codeph"> ません </span>。 </li> 
      <li id="li_E80563E68BEB43FC9E29A694594CAE01">DRMポリシーを更新する際に期間を削除するには、分を指定せずに <span class="codeph"> -r </span> を適用します。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -s日付 </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスが有効になった日付。 </p> <p>日付は、 <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd </span> または <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:secの形式で指定でき </span> ます。 例えば、2008年12月1日の午前0 <span class="codeph"> 時は、2008-12-1 </span> または2008年12月1日の午前0時 <span class="codeph"></span> は、2008年12月12日または2008年12月12日の1-00:00:00とします。 </p> <p> 
     <ul id="ul_D52B337F547F4E7AB87FE025236CA930"> 
      <li id="li_DBAE380972434DB1A4EF20D399038AB8">値が存在する場合は、 <span class="codeph"> -eより小さい値を指定する必要があ </span>ります。 </li> 
      <li id="li_2899EC5559CF44319A4AC4ECD90A5B9A">このオプションは、 <span class="codeph"> -rと共に適用することはできません </span>。 </li> 
      <li id="li_19861B1A64E44B95B649948EAB3E4085">DRMポリシーを更新する際に開始日を削除するには、日付を指定せずに <span class="codeph"> -s </span> を使用します。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -w [&lt;分&gt;[,enableHS|disableHS]] </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">再生ウィンドウ。最初の再生からコンテンツを表示できる分数です。 </p> <p>指定しない場合、または <span class="codeph"> -wを使用して分数を指定しない場合 </span> は、再生ウィンドウに制限はありません。 値は負以外にする必要があります。 </p> <p>オプションのenableHS <span class="codeph"> または </span> disableHS <span class="codeph"></span> フラグは、ハードストップを有効または無効にするかを示す。 このフラグは、復号化コンテキストが再生ウィンドウの最後に破棄される（有効になる）か、破棄されない（無効になる）かを示します。 </p> <p>例えば、コンテンツを60分間のみ表示でき、ハードストップが必要となるように指定するには、次の手順を実行します。 
     <codeblock>
       -w&amp;nbsp;60,enableHS 
     </codeblock> </p> <p>注意：  <i>ハードストップ</i> は、現在、Flash Player、AndroidおよびiOSではサポートされていません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -l分 </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスのキャッシュ期間は、ライセンスがサーバーから発行された後に、クライアントのライセンスストアにライセンスをキャッシュできる時間（分）です。 値は負以外にする必要があります。 </p> <p>-l 0を指定すると、ライセンスのキャッシュ <span class="codeph"></span> が許可されていないことを示すことができます。 無制限のライセンスキャッシュを使用する場合は、 <span class="codeph"> -lを指定します(分 </span> は不要)。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -ldate日 </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスキャッシュの終了日です。 </p> <p class="- topic/p ">これは、Primetime DRMサーバーがライセンスを発行した後に、クライアントがクライアントのLicense Storeのライセンスをキャッシュできる最終日を示します。 </p> <p>日付は、次の形式で指定できます。 
     <ul id="ul_112DE7248A9C48B19520A3AA9E5D1F03"> 
      <li id="li_01C5400E78B84A3B8955972FBA875AAC"> <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd </span> </li> 
      <li id="li_AA13B1EFA07A4542A3DB41FA3320B143"> <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:sec </span> </li> 
     </ul>例えば、2008年12月1日の午前0 <span class="codeph"> 時は、2008-12-1 </span> または2008年12月1日の午前0時 <span class="codeph"></span> は、2008年12月12日または2008年12月12日の1-00:00:00とします。 無制限のライセンスキャッシュには、分を指定しないで <span class="codeph"> -l </span> を適用する必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -authNS </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">認証名前空間。 </p> <p class="- topic/p ">このオプションを適用する場合、クライアントは指定した機関から発行されたユーザー名とパスワードを入力する必要があります。 </p> <p>このオプションを —xと共に適用するこ <span class="codeph"> とはできません </span>。 </p> <p>このオプションは、更新に対しては使用できません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -x </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">匿名アクセスを許可します。 </p> <p class="- topic/p ">-authNSと共にこのオプションを適用することはでき <span class="codeph"> ません </span>。 </p> <p class="- topic/p ">このオプションは、更新に対しては使用できません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -air pubId </span>[: <span class="+ topic/ph pr-d/codeph codeph"> appId </span>[:[ <span class="+ topic/ph pr-d/codeph codeph"> min </span>]:[ <span class="+ topic/ph pr-d/codeph codeph"> max </span>]] </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツを再生できるAIRアプリケーションの許可リストです。 </p> <p class="- topic/p ">このオプションを適用して、このDRMポリシーで保護されたコンテンツにアクセスできる発行者、アプリケーションおよびバージョンを制限できます。 </p> <p class="- topic/p ">appIdを指定しない場合は、 <i class="+ topic/ph hi-d/i ">pubId</i><i class="+ topic/ph hi-d/i "></i> （発行者）のすべてのアプリケーションが許可されます。 </p> <p>注意：  <i class="+ topic/ph hi-d/i ">最小</i> と <i class="+ topic/ph hi-d/i "></i> 最大のバージョン番号は省略可能です。 </p> <p class="- topic/p ">複数の <span class="codeph"> -air </span> オプションを指定して、複数のアプリケーションを許可できます。 AIRまたはSWFアプリケーションを指定しない場合は、すべてのアプリケーションがこのコンテンツにアクセスできます。 更新時に、リストからすべてのエントリを削除するには、残りの引数を指定せずに <span class="codeph"> -air </span> を適用します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -drmブラックリスト名 </span> /値 <i class="+ topic/ph hi-d/i ">のペア</i><span class="+ topic/ph pr-d/codeph codeph"> / </span><i class="+ topic/ph hi-d/i "></i><span class="+ topic/ph pr-d/codeph codeph"> 値 </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツへのアクセスが制限されているDRMクライアント。 </p> <p class="- topic/p ">値は、次の形式で名前と値のペアをコンマで区切って指定できます。 </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> os | release= stringValue </span> </p> <p class="- topic/p ">例えば、os=Win, <span class="codeph"> release=2.0.1のように指定し </span>ます。 更新中に、リストからすべてのエントリを削除するには、残りの引数を指定せずに <span class="codeph"> -drmBlacklist </span> を適用します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -drmLevel int </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツにアクセスするためにDRMクライアントに最小セキュリティレベルを割り当てる必要があることを示します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -opAnalog NO_PROTECTION | USE_IF_AVAILABLE |必須 | NO_PLAYBACK | REQUIRED_ACP | REQUIRED_CGMSA | USE_IF_AVAILABLE_ACP | USE_IF_AVAILABLE_CGMSA </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">アナログ出力保護の制約 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -opDigital NO_PROTECTION | USE_IF_AVAILABLE |必須 | NO_PLAYBACK </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">デジタル出力保護の制約 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -runtimeBlacklist name </span> / <i class="+ topic/ph hi-d/i ">value</i><span class="+ topic/ph pr-d/codeph codeph"></span><i class="+ topic/ph hi-d/i "></i><span class="+ topic/ph pr-d/codeph codeph"> pairs </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツへのアクセスが制限されているアプリケーションの実行時間です。 </p> <p class="- topic/p ">値は、次の形式で、名前と値のペアをカンマで区切ってサポートします。 </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> os | application | release= stringValue </span> </p> <p class="- topic/p ">例えば、 <span class="codeph"> os=Win,release=2.0.1,application=AIR </span>です。 更新時に、リストからすべてのエントリを削除するには、残りの引数を指定せずに —runtimeBlacklistを適用 <span class="codeph"> し </span> ます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -runtimeLevel int </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツにアクセスするために、アプリケーションの実行時に指定した最小セキュリティレベルが必要であることを示します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -swf url </span> </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -swf file=swf_file </span>、 <span class="+ topic/ph pr-d/codeph codeph"> time= max_time_to_verify </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツの再生が許可されるSWFアプリケーションの許可リストです。 </p> <p class="- topic/p ">複数の — <span class="codeph"> swf </span> オプションを指定して、複数のアプリケーションを許可できます。 AIRまたはSWFアプリケーションを指定しない場合は、すべてのアプリケーションがこのコンテンツにアクセスできます。 </p> <p>更新時に、リストからすべてのエントリを削除するには、残りの引数を指定せずに <span class="codeph"> -swf </span> を適用します。 SWFをハッシュ値で識別する場合は、ハッシュを計算する対象のSWFファイルと、SWF検証を完了するのに必要な最大時間（秒）を指定する必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -k name=value </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">DRMポリシーに追加するカスタムキーまたは値を指定します。 </p> <p class="- topic/p ">複数の <span class="codeph"> -k </span> オプションを指定できます。 更新時に、残りの引数を指定せずに —kを適用すると、すべてのプロパティを削除でき <span class="codeph"></span> ます。 データの解釈または処理は、Primetime DRMライセンスサーバーで管理されます。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -p name=value </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">各クライアント用に生成されたライセンスに表示されるカスタムプロパティを追加します。 </p> <p class="- topic/p ">複数の <span class="codeph"> -p </span> オプションを指定して、複数のプロパティを追加できます。 すべてのプロパティを削除する場合は、更新中に、残りの引数を指定せずに <span class="codeph"> -p </span> を適用する必要があります。 このデータの解釈または処理は、クライアントアプリケーションの実装によって管理されます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> <span class="codeph"> -opOTAホワイトリスト=&lt;接続タイプ&gt; </span> </span> </td> 
   <td colname="2" class="- topic/entry "> 大気(OTA)の出力保護の制約を超えています。 ホワ <span class="codeph"> イトリスト </span> フィールドでは、許可リストに対する接続の種類と&lt;connection types&gt;の形式を[type(,type)*] <span class="codeph"></span>に指定します。typeは次のいずれかです。 ミラカスト、エアプレイ、WIDI、DLNA </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -opResolution &lt;ファイル名&gt; </span> </td> 
   <td colname="2" class="- topic/entry "> <p>指定したファイルで定義される、解像度ベースの出力保護制約。 </p> <p>このファイルのエンコーディングはJSONです。 書式設定の文法は、「解像度ベースの出力保護に <i>ついて</i>」で確認できます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

**例**

独自の設定プロパティファイルを使用して、コンテンツへの匿名アクセスを許可するポリシーを作成するには：

```
java -jar libs\AdobePolicyManager.jar new policy_test.pol -x -c my_configuration.properties
```
