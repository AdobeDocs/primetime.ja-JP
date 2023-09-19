---
title: コマンドラインの使用
description: コマンドラインの使用
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 0%

---

# コマンドラインの使用 {#command-line-usage}

Policy Manager を使用する前に、「要件」に示す要件を満たしていることを確認してください。

Policy Manager が [!DNL \Reference Implementation\Command Line Tools] DVD 上のディレクトリ。 ツールを実行するには、次の構文を使用します。

```
java -jar AdobePolicyManager.jar  
<i class="+ topic ph hi-d="" i "="">
  command filename [options] 
</i class="+ topic>
```

次の表に、上記の構文に示すコマンドラインアクションの説明を示します。

| コマンドラインの操作 | 説明 |
|---|---|
| `new` | 新しいポリシーを作成します。 |
| `detail` | 既存のポリシーを表します。 |
| `update` | 既存のポリシーを更新します。 |

次の表に、上記の構文と共に指定できるコマンドラインオプションを示します。

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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">設定ファイルの場所を指定します。 このオプションを使用しない場合、Policy Manager は <span class="filepath"> flashaccesstools.properties </span> を作業ディレクトリに追加します。 コマンドラインで指定したオプションは、設定ファイルに存在するオプションよりも優先されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">宛先ファイルが既に存在する場合は、確認を求めずに上書きします。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -noprompt </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">宛先ファイルを上書きするかどうかを確認しないでください。 宛先ファイルが既に存在し、 <span class="codeph"> -o </span> が設定されていない場合は、エラーが返されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -root </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ポリシーにルートライセンスがあることを示します。 更新を許可されていません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -e 日 </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスが有効になる日付。 次のように指定します。 <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd </span> または <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:秒 </span>. 例：2008-12-1や2008-12-1-00:00:2008 年 12 月 1 日午前 0 時。 値は、 <span class="codeph"> -s </span>（存在する場合） このオプションは、 <span class="codeph"> -r </span>. ポリシーの更新時に終了日を削除するには、 <span class="codeph"> -e </span> 日付を指定しないで </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -r 分 </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">このポリシーで保護されたコンテンツが有効である期間（分）です。この期間は、パッケージャーでコンテンツが保護された時点から始まります。 値は、負以外の値にする必要があります。 このオプションは、 <span class="codeph"> -e </span>. ポリシーの更新時に期間を削除するには、 <span class="codeph"> -r </span> 分数を指定しないでください。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -s 日付 </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスが有効になる日付。 次のように指定します。 <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd </span> または <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:秒 </span>. 例：2008-12-1や2008-12-1-00:00:2008 年 12 月 1 日午前 0 時。 値は、 <span class="codeph"> -e </span>（存在する場合） このオプションは、 <span class="codeph"> -r </span>. ポリシーの更新時に開始日を削除するには、 <span class="codeph"> -s </span> 日付を指定しないで </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -w 分 </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">再生ウィンドウ ( 最初の再生からコンテンツが視聴されるまでの時間（分）)。 このオプションが指定されていない場合、または <span class="codeph"> -w </span> 分数を指定せずにを使用する場合は、再生ウィンドウに制限はありません。 値は、負以外の値にする必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -l 分 </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスのキャッシュ期間（分）。これは、サーバーがライセンスを発行した後に、クライアントのライセンスストアにライセンスをキャッシュできる時間です。 値は、負以外の値にする必要があります。 指定 <span class="codeph"> -l 0 </span> をクリックして、ライセンスのキャッシュが許可されていないことを示します。 用途 <span class="codeph"> -l </span> 何分も指定せずに、無制限のライセンスキャッシュを実行できます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -ldate 日 </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスキャッシュの終了日（サーバーがライセンスを発行した後、クライアントのライセンスストアにライセンスをキャッシュできない日付）。 次のように指定します。 <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd </span><i class="+ topic/ph hi-d/i "> </i>または<i class="+ topic/ph hi-d/i "> </i> <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:秒 </span>. 例：2008-12-1や2008-12-1-00:00:2008 年 12 月 1 日午前 0 時。 用途 <span class="codeph"> -l </span> 何分も指定せずに、無制限のライセンスキャッシュを実行できます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -authNS </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">認証名前空間。 指定した場合、クライアントは、指定した権限が発行したユーザー名とパスワードを使用して認証する必要があります。 このオプションは、 <span class="codeph"> -x </span>. 更新を許可されていません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -x </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">匿名アクセスを許可します。 このオプションは、 <span class="codeph"> -authNS </span>. 更新を許可されていません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -air pubId </span>[: <span class="+ topic/ph pr-d/codeph codeph"> appId </span>[:[ <span class="+ topic/ph pr-d/codeph codeph"> 分 </span>]:[ <span class="+ topic/ph pr-d/codeph codeph"> 最大 </span>]] </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">AIRアプリケーションの許可リストで、保護されたコンテンツの再生が許可されています。 このポリシーで保護されたコンテンツにアクセスできる発行者、アプリケーションおよびバージョンを制限するには、このオプションを使用します。 </p> <p class="- topic/p ">次の場合 <i class="+ topic/ph hi-d/i ">appId</i> が指定されていません。パブリッシャのすべてのアプリケーションが指定されています。 <i class="+ topic/ph hi-d/i ">pubId</i> は許可されています。 </p> <p class="- topic/p "><i class="+ topic/ph hi-d/i ">分</i> および <i class="+ topic/ph hi-d/i ">最大</i> バージョン番号はオプションです。 </p> <p class="- topic/p ">複数 <span class="codeph"> -air </span> 複数のアプリケーションを許可する場合は、オプションを指定できます。 AIRまたはSWFアプリケーションが指定されていない場合、すべてのアプリケーションがこのコンテンツにアクセスできます。 更新中に、-air を残りの引数なしで使用して、リストからすべてのエントリを削除します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -drmBlacklist 名 </span> <i class="+ topic/ph hi-d/i ">/</i> <span class="+ topic/ph pr-d/codeph codeph"> 値 </span> <i class="+ topic/ph hi-d/i "> </i> <span class="+ topic/ph pr-d/codeph codeph"> ペア </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">DRM クライアントは保護されたコンテンツへのアクセスを制限しています。 値は、次の形式のコンマ区切りの名前と値のペアで構成されます。 </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> os | release= stringValue </span> </p> <p class="- topic/p ">例： <span class="codeph"> os=Win,release=2.0.1 </span>. 更新時に、 <span class="codeph"> -drmBlacklist </span> 残りの引数を指定せずに、リストからすべてのエントリを削除します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -drmLevel int </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツにアクセスするには、DRM クライアントが指定された最小セキュリティレベルを持っている必要があることを示します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -opAnalog NO_PROTECTION | USE_IF_AVAILABLE |必須 | NO_PLAYBACK | ACP_REQUIRED | CGMS-A_REQUIRED | USE_ACP_IF_AVAILABLE | USE_CGMS-A_IF_AVAILABLE </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">アナログ出力保護の制約。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -opDigital NO_PROTECTION | USE_IF_AVAILABLE |必須 | NO_PLAYBACK </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">デジタル出力保護の制約。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -runtimeBlacklist 名 </span> <i class="+ topic/ph hi-d/i ">/</i> <span class="+ topic/ph pr-d/codeph codeph"> 値 </span> <i class="+ topic/ph hi-d/i "> </i> <span class="+ topic/ph pr-d/codeph codeph"> ペア </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">アプリケーションのランタイムは、保護されたコンテンツへのアクセスを制限しています。 値は、次の形式のコンマ区切りの名前と値のペアで構成されます。 </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> os | application | release= stringValue </span> </p> <p class="- topic/p ">例： <span class="codeph"> os=Win,release=2.0.1,application=AIR </span>. 更新時に、 <span class="codeph"> -runtimeBlacklist </span> 残りの引数を指定せずに、リストからすべてのエントリを削除します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -runtimeLevel int </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツにアクセスするには、アプリケーションのランタイムに指定された最小セキュリティレベルが必要であることを示します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -swf url </span> </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -swf file= swf_file </span>, <span class="+ topic/ph pr-d/codeph codeph"> time= max_time_to_verify </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツを再生できるSWFアプリケーションの許可リストです。 複数の —swf オプションを指定して、複数のアプリケーションを許可することができます。 AIRまたはSWFアプリケーションが指定されていない場合、すべてのアプリケーションがこのコンテンツにアクセスできます。 更新時に、-swf を残りの引数なしで使用して、リストからすべてのエントリを削除します。 SWFをハッシュ値で識別するには、ハッシュを計算するSWFファイルと、SWF検証が完了するまでの最大時間（秒）を指定します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -k name= value </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ポリシーに追加するカスタムキー/値を指定します。 複数 <span class="codeph"> -k </span> オプションを指定できます。 更新時に、 <span class="codeph"> -k </span> 残りの引数を指定せずに、すべてのプロパティを削除します。 このデータの解釈や処理は、Adobe・アクセス・ライセンス・サーバの実装によって完全に異なります。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -p name=値 </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">カスタムプロパティを追加します。このプロパティは、各クライアントに対して生成されたライセンスに表示されます。 複数 <span class="codeph"> -p </span> 複数のプロパティを追加する場合は、オプションを指定できます。 更新時に、 <span class="codeph"> -p </span> 残りの引数を指定せずに、すべてのプロパティを削除します。 このデータの解釈や処理は、クライアントアプリケーションの実装次第です。 </p> </td> 
  </tr> 
 </tbody> 
</table>
