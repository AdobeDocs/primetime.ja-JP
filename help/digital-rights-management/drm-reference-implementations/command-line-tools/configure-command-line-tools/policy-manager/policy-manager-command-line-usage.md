---
title: Policy Manager のコマンドラインの使用
description: Policy Manager のコマンドラインの使用
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1223'
ht-degree: 0%

---

# Policy Manager のコマンドラインの使用 {#policy-manager-command-line-usage}

```
java -jar AdobePolicyManager.jar  
<i class="+ topic ph hi-d="" i "="">
  command filename [options] 
</i class="+ topic>
```

**表 1：コマンド**

| コマンド | 説明 |
|---|---|
| `new` | 新しい DRM ポリシーを作成します |
| `detail` | 既存の DRM ポリシーを記述します |
| `update` | 既存の DRM ポリシーを更新します |

**表 2：オプション**

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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">設定ファイルの名前と場所を指定します。 </p> <p class="- topic/p ">名前や場所を指定しない場合、DRM ポリシーマネージャーは <span class="filepath"> flashaccesstools.properties </span> 現在の作業ディレクトリ内。 </p> <p>注：コマンドラインで指定するオプションは、設定ファイルで指定するオプションよりも優先されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">宛先ファイルが存在する場合は、プロンプトを表示せずにファイルを上書きできます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -noprompt </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">宛先ファイルを上書きするかどうかを確認しないでください。 宛先ファイルが存在し、 <span class="codeph"> -o </span> が設定されていない場合、エラーが発生します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -root </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">DRM ポリシーにルートライセンスがあることを示します。 </p> <p class="- topic/p ">このオプションは、更新では使用できません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -e 日 </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスの有効期限が切れます。 </p> <p>日付は、 <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd </span> または <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:秒 </span> 形式を使用します。 例：2008-12-1や2008-12-1-00:00:2008 年 12 月 1 日午前 0 時。 </p> <p> 
     <ul id="ul_D5DB5044756D4BD6A734813971598425"> 
      <li id="li_B6BD62A524384060A9DDA14FF50936FA">値は、 <span class="codeph"> -s </span> 存在する場合は。 </li> 
      <li id="li_C3C5AD0231A240EC9AC57685B9206E8D">このオプションは、 <span class="codeph"> -r </span>. </li> 
      <li id="li_3790E2F829A149979BF44E0914CFF431">DRM ポリシーを更新する際に終了日を削除するには、 <span class="codeph"> -e </span> 日付を指定しないで </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -r 分 </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツが有効である期間（分単位）です。 </p> <p class="- topic/p ">コンテンツがパッケージャーで保護されると、DRM ポリシーが有効になります。 </p> <p> 
     <ul id="ul_4690A0E4677A4DF6A006B7FCBD46F1BE"> 
      <li id="li_D1F098D44B494EE7A8647C0B62D5ACFA">値は、負以外の値にする必要があります。 </li> 
      <li id="li_ADFDCB01EEE04B37AFA42886AAEF47EB">このオプションは、 <span class="codeph"> -e </span>. </li> 
      <li id="li_E80563E68BEB43FC9E29A694594CAE01">DRM ポリシーを更新する際に期間を削除するには、 <span class="codeph"> -r </span> 分を指定せずに </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -s 日付 </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスが有効になった日付。 </p> <p>日付は <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd </span> または <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:秒 </span> 形式を使用します。 例： <span class="codeph"> 2008-12-1 </span> または <span class="codeph"> 2008-12-1-00:00:00 </span> 2008 年 12 月 1 日深夜。 </p> <p> 
     <ul id="ul_D52B337F547F4E7AB87FE025236CA930"> 
      <li id="li_DBAE380972434DB1A4EF20D399038AB8">値は、 <span class="codeph"> -e </span>（存在する場合） </li> 
      <li id="li_2899EC5559CF44319A4AC4ECD90A5B9A">このオプションは、 <span class="codeph"> -r </span>. </li> 
      <li id="li_19861B1A64E44B95B649948EAB3E4085">DRM ポリシーを更新する際に開始日を削除するには、 <span class="codeph"> -s </span> 日付を指定しないで </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -w [&lt;minutes&gt;[,enableHS|disableHS]] </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">再生ウィンドウ：最初の再生からコンテンツを視聴できる時間（分）です。 </p> <p>指定しない場合、または <span class="codeph"> -w </span> が分数を指定せずに使用される場合、再生ウィンドウの制限はありません。 値は、負以外の値にする必要があります。 </p> <p>オプションの <span class="codeph"> enableHS </span> または <span class="codeph"> disableHS </span> フラグは、ハードストップを有効または無効にするかどうかを示します。 このフラグは、復号コンテキストが再生ウィンドウの終わりに破棄されるか（有効）、破棄されないか（無効）を示します。 </p> <p>例えば、コンテンツが 60 分間のみ表示され、ハードストップが必要となるように指定するには、次のように指定します。 
     <codeblock>
       -w&amp;nbsp;60,enableHS 
     </codeblock> </p> <p>注意：  <i>ハードストップ</i> は、現在、Flash Player、Android、iOSではサポートされていません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -l 分 </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスのキャッシュ期間とは、サーバーがライセンスを発行した後に、クライアントのライセンスストアにライセンスをキャッシュできる時間（分）を指します。 値は、負以外の値にする必要があります。 </p> <p>次を指定できます。 <span class="codeph"> -l 0 </span> をクリックして、ライセンスのキャッシュが許可されていないことを示します。 無制限のライセンスキャッシュの場合は、次を指定します。 <span class="codeph"> -l </span> 何分も経たずに </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -ldate 日 </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスキャッシュの終了日です。 </p> <p class="- topic/p ">これは、Primetime DRM サーバーがライセンスを発行した後に、クライアントがクライアントのライセンスストアでライセンスをキャッシュできる最終日を示します。 </p> <p>日付は、次の形式で指定できます。 
     <ul id="ul_112DE7248A9C48B19520A3AA9E5D1F03"> 
      <li id="li_01C5400E78B84A3B8955972FBA875AAC"> <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd </span> </li> 
      <li id="li_AA13B1EFA07A4542A3DB41FA3320B143"> <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:秒 </span> </li> 
     </ul>例： <span class="codeph"> 2008-12-1 </span> または <span class="codeph"> 2008-12-1-00:00:00 </span> 2008 年 12 月 1 日深夜。 を適用する必要があります <span class="codeph"> -l </span> 無制限のライセンスキャッシュに関して何分も指定しないでください。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -authNS </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">認証名前空間。 </p> <p class="- topic/p ">このオプションを適用する場合、クライアントは、指定された権限によって発行されたユーザー名とパスワードを入力する必要があります。 </p> <p>このオプションは、 <span class="codeph"> -x </span>. </p> <p>このオプションは更新では使用できません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -x </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">匿名アクセスを許可します。 </p> <p class="- topic/p ">このオプションは、 <span class="codeph"> -authNS </span>. </p> <p class="- topic/p ">このオプションは更新では使用できません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -air pubId </span>[: <span class="+ topic/ph pr-d/codeph codeph"> appId </span>[:[ <span class="+ topic/ph pr-d/codeph codeph"> 分 </span>]:[ <span class="+ topic/ph pr-d/codeph codeph"> 最大 </span>]] </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツを再生できるAIRアプリケーションの許可リスト。 </p> <p class="- topic/p ">このオプションを適用して、この DRM ポリシーで保護されたコンテンツにアクセスできる公開者、アプリケーションおよびバージョンを制限できます。 </p> <p class="- topic/p ">指定しない場合、 <i class="+ topic/ph hi-d/i ">appId</i>（パブリッシャー用のすべてのアプリケーション） <i class="+ topic/ph hi-d/i ">pubId</i> は許可されています。 </p> <p>注意：  <i class="+ topic/ph hi-d/i ">分</i> および <i class="+ topic/ph hi-d/i ">最大</i> バージョン番号はオプションです。 </p> <p class="- topic/p ">複数の <span class="codeph"> -air </span> 複数のアプリケーションを許可するオプション。 AIRまたはSWFアプリケーションを指定しない場合、すべてのアプリケーションがこのコンテンツにアクセスできます。 更新中に、リストからすべてのエントリを削除または削除するには、を適用します。 <span class="codeph"> -air </span> 残りの引数なし </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -drmBlacklist 名 </span> <i class="+ topic/ph hi-d/i ">/</i> <span class="+ topic/ph pr-d/codeph codeph"> 値 </span> <i class="+ topic/ph hi-d/i "> </i> <span class="+ topic/ph pr-d/codeph codeph"> ペア </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツへのアクセスを制限されている DRM クライアント。 </p> <p class="- topic/p ">この値では、次の形式で名前と値のペアをコンマ区切りでサポートします。 </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> os | release= stringValue </span> </p> <p class="- topic/p ">例： <span class="codeph"> os=Win,release=2.0.1 </span>. 更新中に、リストからすべてのエントリを削除するには、を適用します。 <span class="codeph"> -drmBlacklist </span> 残りの引数なしで </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -drmLevel int </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツにアクセスするには、DRM クライアントに最小セキュリティレベルを割り当てる必要があることを示します。 </p> </td> 
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
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -runtimeBlacklist 名 </span> <i class="+ topic/ph hi-d/i ">/</i> <span class="+ topic/ph pr-d/codeph codeph"> 値 </span> <i class="+ topic/ph hi-d/i "> </i> <span class="+ topic/ph pr-d/codeph codeph"> ペア </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツへのアクセスが制限されているアプリケーションランタイム。 </p> <p class="- topic/p ">値は、次の形式でコンマ区切りの名前と値のペアをサポートします。 </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> os | application | release= stringValue </span> </p> <p class="- topic/p ">例： <span class="codeph"> os=Win,release=2.0.1,application=AIR </span>. 更新中に、リストからすべてのエントリを削除するには、を適用します。 <span class="codeph"> -runtimeBlacklist </span> 残りの引数なし </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -runtimeLevel int </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツにアクセスするには、アプリケーションのランタイムに指定された最小セキュリティレベルが必要であることを示します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -swf url </span> </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -swf file= swf_file </span>, <span class="+ topic/ph pr-d/codeph codeph"> time= max_time_to_verify </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツの再生が許可されるSWFアプリケーションの許可リスト。 </p> <p class="- topic/p ">複数の <span class="codeph"> -swf </span> 複数のアプリケーションを許可するオプション。 AIRまたはSWFアプリを指定しない場合、すべてのアプリケーションがこのコンテンツにアクセスできます。 </p> <p>更新中に、リストからすべてのエントリを削除するには、を適用します。 <span class="codeph"> -swf </span> 残りの引数なし ハッシュ値でSWFを識別する場合は、ハッシュを計算するSWFファイルと、SWF検証が完了するまでの最大時間（秒）を指定する必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -k name= value </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">DRM ポリシーに追加するカスタムキー/値を指定します。 </p> <p class="- topic/p ">複数の <span class="codeph"> -k </span> オプション。 更新中に、 <span class="codeph"> -k </span> すべてのプロパティを削除する場合は、残りの引数を指定しません。 データの解釈や処理は、Primetime DRM ライセンスサーバーによって管理されます。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -p name=値 </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">各クライアントに対して生成されたライセンスに表示されるカスタムプロパティを追加します。 </p> <p class="- topic/p ">複数の <span class="codeph"> -p </span> 複数のプロパティを追加するオプション。 更新中に、 <span class="codeph"> -p </span> すべてのプロパティを削除する場合は、残りの引数を指定しません。 このデータの解釈や処理は、クライアントアプリケーションの実装によって管理されます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> <span class="codeph"> -opOTA ホワイトリスト=&lt;connection types=""&gt; </span> </span> </td> 
   <td colname="2" class="- topic/entry "> 空気 (OTA) 上での出力保護制約。 The <span class="codeph"> whitelist </span> フィールドには、接続の種類と許可リストの形式を指定します &lt;connection types=""&gt; 次に該当 <span class="codeph"> [type(,type)*] </span>で指定できるタイプは、MIRACAST、AIRPLAY、WIDI、DLNA のいずれかです。 </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -opResolution &lt;filename&gt; </span> </td> 
   <td colname="2" class="- topic/entry "> <p>指定したファイルで定義されている、解像度ベースの出力保護制約。 </p> <p>このファイルのエンコードは JSON です。 書式設定の文法については、 <i>解像度ベースの出力保護について</i>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**例**

独自の設定プロパティファイルを使用して、コンテンツへの匿名アクセスを許可するポリシーを作成するには、次の手順を実行します。

```
java -jar libs\AdobePolicyManager.jar new policy_test.pol -x -c my_configuration.properties
```
