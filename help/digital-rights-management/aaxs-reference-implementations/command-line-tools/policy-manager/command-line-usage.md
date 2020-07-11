---
seo-title: コマンドラインの使用
title: コマンドラインの使用
uuid: e549a98e-b027-4472-8860-6aa1d56d4a8b
translation-type: tm+mt
source-git-commit: 58bb3bedc5b0ac63afd96eb6101d9ad779e6deed
workflow-type: tm+mt
source-wordcount: '1026'
ht-degree: 0%

---


# コマンドラインの使用 {#command-line-usage}

Policy Managerを使用する前に、「要件」に示されている要件を満たしていることを確認してください。

Policy Managerは、DVD上の [!DNL \Reference Implementation\Command Line Tools] ディレクトリにあります。 ツールを実行するには、次の構文を使用します。

```
java -jar AdobePolicyManager.jar  
<i class="+ topic ph hi-d="" i "="">
  command filename [options] 
</i class="+ topic>
```

次の表に、上の構文に示したコマンドラインアクションの説明を示します。

| コマンドラインアクション | 説明 |
|---|---|
| `new` | 新しいポリシーを作成します。 |
| `detail` | 既存のポリシーについて説明します。 |
| `update` | 既存のポリシーを更新します。 |

次の表に、上の構文と共に指定できるコマンドラインオプションを示します。

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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">設定ファイルの場所を指定します。 このオプションを使用しない場合、Policy Managerは、作業ディレクトリ内で <span class="filepath"> flashaccesstools.properties </span> を検索します。 コマンドラインで指定したオプションは、設定ファイルに存在するオプションよりも優先されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コピー先のファイルが既に存在する場合は、確認せずに上書きします。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -noprompt </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コピー先のファイルを上書きするかどうかを確認しない。 コピー先のファイルが既に存在し、 <span class="codeph"> -oが設定さ </span> れていない場合は、エラーが返されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -root </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ポリシーにルートライセンスがあることを示します。 アップデートは許可されていません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -e日 </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスが有効になる日付です。 yyyy-mm-dd <span class="+ topic/ph pr-d/codeph codeph"> または </span> yyyy-mm-dd-h24:min:secと指定し <span class="+ topic/ph pr-d/codeph codeph"></span>ます。 例えば、2008年12月1日の午前0時は、2008-12-1または2008-12-1-00:00:00と指定します。 値は —s（存在する場合）より大きい <span class="codeph"> 必要があ </span>ります。 このオプションは —rと組み合わせて使用することはでき <span class="codeph"> ません </span>。 ポリシーの更新時に終了日を削除するには、日付を指定せずに <span class="codeph"> -e </span> を使用します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -r分 </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">このポリシーで保護されたコンテンツが有効である期間（分）です。この期間は、パッケージャーでコンテンツが保護された時点から開始されます。 値は負以外にする必要があります。 このオプションは —eと共に使用することはでき <span class="codeph"> ません </span>。 ポリシーの更新時に期間を削除するには、-rを使用します。分数は指定しま <span class="codeph"></span> せん。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -s日付 </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスが有効になる日付です。 yyyy-mm-dd <span class="+ topic/ph pr-d/codeph codeph"> または </span> yyyy-mm-dd-h24:min:secと指定し <span class="+ topic/ph pr-d/codeph codeph"></span>ます。 例えば、2008年12月1日の午前0時は、2008-12-1または2008-12-1-00:00:00と指定します。 値が存在する場合は、 <span class="codeph"> -eより小さい値を指定する必要があ </span>ります。 このオプションは —rと組み合わせて使用することはでき <span class="codeph"> ません </span>。 ポリシーの更新時に開始日を削除するには、日付を指定せずに <span class="codeph"> -s </span> を使用します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -w分 </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">再生ウィンドウ(最初の再生から始まる、コンテンツが表示される時間（分）)。 このオプションを指定しない場合、または <span class="codeph"> -wを分数を指定せずに使用する場合 </span> は、再生時間に関する制限はありません。 値は負以外にする必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -l分 </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスのキャッシュ期間（分単位）です。この時間は、ライセンスがサーバーによって発行された後に、クライアントのライセンスストアでライセンスがキャッシュされる時間です。 値は負以外にする必要があります。 ライセンスのキャッシュ <span class="codeph"></span> が許可されていないことを示す場合は、-l 0を指定します。 無制限のライセンスキャッシュを行う場合は、 <span class="codeph"> -l </span> を使用し、分数を指定しません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -ldate日 </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスキャッシュの終了日（サーバーがライセンスを発行した後、クライアントのLicense Storeにライセンスをキャッシュできない場合がある日付）。 yyyy-mm-dd <span class="+ topic/ph pr-d/codeph codeph"> または </span><i class="+ topic/ph hi-d/i "></i><i class="+ topic/ph hi-d/i "> yyyy-mm-dd-h24:min:secと指定し </i><span class="+ topic/ph pr-d/codeph codeph"></span>ます。 例えば、2008年12月1日の午前0時は、2008-12-1または2008-12-1-00:00:00と指定します。 無制限のライセンスキャッシュを行う場合は、 <span class="codeph"> -l </span> を使用し、分数を指定しません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -authNS </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">認証名前空間。 指定する場合、クライアントは、指定した機関が発行したユーザー名とパスワードを使用して認証を受ける必要があります。 このオプションは —xと共に使用するこ <span class="codeph"> とはできません </span>。 アップデートは許可されていません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -x </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">匿名アクセスを許可します。 このオプションは、-authNSでは使用できま <span class="codeph"> せん </span>。 アップデートは許可されていません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -air pubId </span>[: <span class="+ topic/ph pr-d/codeph codeph"> appId </span>[:[ <span class="+ topic/ph pr-d/codeph codeph"> min </span>]:[ <span class="+ topic/ph pr-d/codeph codeph"> max </span>]] </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツの再生が許可されるAIRアプリケーションの許可リスト。 このポリシーで保護されたコンテンツにアクセスできる発行者、アプリケーションおよびバージョンを制限する場合に使用します。 </p> <p class="- topic/p ">appId <i class="+ topic/ph hi-d/i ">を指定しない場合</i> 、publisher <i class="+ topic/ph hi-d/i ">pubId</i> のすべてのアプリケーションが許可されます。 </p> <p class="- topic/p "><i class="+ topic/ph hi-d/i ">最小</i> と <i class="+ topic/ph hi-d/i "></i> 最大のバージョン番号は省略可能です。 </p> <p class="- topic/p ">複数の <span class="codeph"> -air </span> オプションを指定して、複数のアプリケーションを使用できます。 AIRまたはSWFアプリケーションを指定しない場合、すべてのアプリケーションがこのコンテンツにアクセスする可能性があります。 更新時に、-airを残りの引数なしで使用し、リストからすべてのエントリを削除します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -drmブラックリスト名 </span> /値 <i class="+ topic/ph hi-d/i ">のペア</i><span class="+ topic/ph pr-d/codeph codeph"> / </span><i class="+ topic/ph hi-d/i "></i><span class="+ topic/ph pr-d/codeph codeph"> 値 </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">DRMクライアントは、保護されたコンテンツへのアクセスを制限しています。 値は、次の形式で名前と値のペアをカンマで区切って構成します。 </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> os | release= stringValue </span> </p> <p class="- topic/p ">例えば、os=Win, <span class="codeph"> release=2.0.1のように指定し </span>ます。 更新中に、-drmBlacklistを使用し、残りの引数を指定しないで、リスト <span class="codeph"></span> からすべてのエントリを削除します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -drmLevel int </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツにアクセスするためにDRMクライアントのセキュリティレベルが指定の最小値になっている必要があることを示します。 </p> </td> 
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
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -runtimeBlacklist name </span> / <i class="+ topic/ph hi-d/i ">value</i><span class="+ topic/ph pr-d/codeph codeph"></span><i class="+ topic/ph hi-d/i "></i><span class="+ topic/ph pr-d/codeph codeph"> pairs </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">アプリケーションの実行時に、保護されたコンテンツへのアクセスが制限されています。 値は、次の形式で名前と値のペアをカンマで区切って構成します。 </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> os | application | release= stringValue </span> </p> <p class="- topic/p ">例えば、 <span class="codeph"> os=Win,release=2.0.1,application=AIR </span>です。 更新時に、-runtimeBlacklistを使用し、残りの引数 <span class="codeph"></span> を指定しないで、リストからすべてのエントリを削除します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -runtimeLevel int </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツにアクセスするために、アプリケーションの実行時に指定した最小セキュリティレベルが必要であることを示します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -swf url </span> </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -swf file=swf_file </span>、 <span class="+ topic/ph pr-d/codeph codeph"> time= max_time_to_verify </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツの再生が許可されるSWFアプリケーションの許可リストです。 複数の —swfオプションを指定して、複数のアプリケーションを使用できるようにすることができます。 AIRまたはSWFアプリケーションを指定しない場合、すべてのアプリケーションがこのコンテンツにアクセスする可能性があります。 更新時に、-swfを残りの引数なしで使用すると、リストからすべてのエントリが削除されます。 SWFをハッシュ値で識別するには、ハッシュを計算する対象のSWFファイルと、SWF検証の完了に必要な最大時間（秒）を指定します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -k name=value </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ポリシーに追加するカスタムキー/値を指定します。 複数の <span class="codeph"> -k </span> オプションを指定できます。 更新時に、残りの引数を指定しないで <span class="codeph"> -k </span> を使用し、すべてのプロパティを削除します。 このデータの解釈や処理は、Adobe Accessライセンスサーバーの実装に完全に依存します。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -p name=value </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">カスタムプロパティを追加します。このプロパティは、各クライアント用に生成されたライセンスに表示されます。 複数の <span class="codeph"> -p </span> オプションを指定して、複数のプロパティを追加できます。 更新時に、残りの引数を指定しないで <span class="codeph"> -p </span> を使用し、すべてのプロパティを削除します。 このデータの解釈や処理は、クライアントアプリケーションの実装に完全に依存します。 </p> </td> 
  </tr> 
 </tbody> 
</table>

