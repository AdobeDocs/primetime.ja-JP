---
title: コマンドラインの使用
description: コマンドラインの使用
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '1026'
ht-degree: 0%

---


# コマンドラインの使用{#command-line-usage}

Policy Managerを使用する前に、「要件」に示されている要件を満たしていることを確認してください。

Policy Managerは、DVDの[!DNL \Reference Implementation\Command Line Tools]ディレクトリにあります。 ツールを実行するには、次の構文を使用します。

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
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -c configfile  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">設定ファイルの場所を指定します。 このオプションを使用しない場合、Policy Managerは、作業ディレクトリ内の<span class="filepath"> flashaccesstools.properties </span>を探します。 コマンドラインで指定したオプションは、設定ファイルに存在するオプションよりも優先されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コピー先のファイルが既に存在する場合は、確認せずに上書きします。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -noprompt  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コピー先のファイルを上書きするかどうかを確認しない。 宛先ファイルが既に存在し、<span class="codeph"> -o </span>が設定されていない場合は、エラーが返されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -root  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ポリシーにルートライセンスがあることを示します。 アップデートは許可されていません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -e日  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスが有効になる日付です。 <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd </span>または<span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:sec </span>の形式で指定します。 例えば、2008年12月1日の午前0時は、2008-12-1または2008-12-1-00:00:00と指定します。 値は、<span class="codeph"> -s </span>の値（存在する場合）より大きくなければなりません。 このオプションは<span class="codeph"> -r </span>と共に使用することはできません。 ポリシーの更新時に終了日を削除するには、日付を指定せずに<span class="codeph"> -e </span>を使用します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -r分  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">このポリシーで保護されたコンテンツが有効である期間（分）です。この期間は、パッケージャーでコンテンツが保護された時点から開始されます。 値は負以外にする必要があります。 このオプションは<span class="codeph"> -e </span>と共に使用することはできません。 ポリシーの更新時に期間を削除するには、<span class="codeph"> -r </span>を使用し、分数を指定しません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -s日付  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスが有効になる日付です。 <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd </span>または<span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:sec </span>の形式で指定します。 例えば、2008年12月1日の午前0時は、2008-12-1または2008-12-1-00:00:00と指定します。 値は、<span class="codeph"> -e </span>の値（存在する場合）より小さい必要があります。 このオプションは<span class="codeph"> -r </span>と共に使用することはできません。 ポリシーの更新時に開始日を削除するには、日付を指定せずに<span class="codeph"> -s </span>を使用します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -w分  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">再生ウィンドウ(最初の再生から始まる、コンテンツが表示される時間（分）)。 このオプションを指定しない場合、または<span class="codeph"> -w </span>が分数を指定せずに使用される場合、再生ウィンドウに制限はありません。 値は負以外にする必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -l分  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスのキャッシュ期間（分単位）です。この時間は、ライセンスがサーバーによって発行された後に、クライアントのライセンスストアでライセンスがキャッシュされる時間です。 値は負以外にする必要があります。 <span class="codeph"> -l 0 </span>を指定して、ライセンスのキャッシュが許可されないことを示します。 無制限のライセンスキャッシュを行う場合は、分単位で<span class="codeph"> -l </span>を使用します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -ldate日  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスキャッシュの終了日（サーバーがライセンスを発行した後、クライアントのLicense Storeにライセンスをキャッシュできない場合がある日付）。 <span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd </span><i class="+ topic/ph hi-d/i "> </i>または<i class="+ topic/ph hi-d/i "> </i> <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:sec </span>の形式で指定します。 例えば、2008年12月1日の午前0時は、2008-12-1または2008-12-1-00:00:00と指定します。 無制限のライセンスキャッシュを行う場合は、分単位で<span class="codeph"> -l </span>を使用します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -authNS  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">認証名前空間。 指定する場合、クライアントは、指定した機関が発行したユーザー名とパスワードを使用して認証を受ける必要があります。 このオプションは<span class="codeph"> -x </span>と共に使用することはできません。 アップデートは許可されていません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -x  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">匿名アクセスを許可します。 このオプションは、<span class="codeph"> -authNS </span>では使用できません。 アップデートは許可されていません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -air pubId  </span>[: <span class="+ topic/ph pr-d/codeph codeph"> appId  </span>[:[  <span class="+ topic/ph pr-d/codeph codeph"> min  </span>]:[  <span class="+ topic/ph pr-d/codeph codeph"> max  </span>]] </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツの再生が許可されるAIRアプリケーションの許可リスト。 このポリシーで保護されたコンテンツにアクセスできる発行者、アプリケーションおよびバージョンを制限する場合に使用します。 </p> <p class="- topic/p "><i class="+ topic/ph hi-d/i ">appId</i>を指定しない場合、パブリッシャー<i class="+ topic/ph hi-d/i ">pubId</i>のすべてのアプリケーションが許可されます。 </p> <p class="- topic/p "><i class="+ topic/ph hi-d/i "></i> minと <i class="+ topic/ph hi-d/i "></i> maxversionの数字はオプションです。 </p> <p class="- topic/p ">複数の<span class="codeph"> -air </span>オプションを指定して、複数のアプリケーションを使用できるようにすることができます。 AIRまたはSWFアプリケーションを指定しない場合、すべてのアプリケーションがこのコンテンツにアクセスする可能性があります。 更新時に、-airを残りの引数なしで使用し、リストからすべてのエントリを削除します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -drmBlacklist名 </span> <i class="+ topic/ph hi-d/i ">と</i> <span class="+ topic/ph pr-d/codeph codeph"> 値の </span> <i class="+ topic/ph hi-d/i "> </i> <span class="+ topic/ph pr-d/codeph codeph"> ペア  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">DRMクライアントは保護されたコンテンツへのアクセスを制限しています。 値は、次の形式で名前と値のペアをカンマで区切って構成します。 </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> os | release= stringValue  </span> </p> <p class="- topic/p ">例えば、<span class="codeph"> os=Win,release=2.0.1 </span>のように指定します。 更新中に、残りの引数を指定せずに<span class="codeph"> -drmBlacklist </span>を使用し、リストからすべてのエントリを削除します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -drmLevel int  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツにアクセスするためにDRMクライアントのセキュリティレベルが指定の最小値になっている必要があることを示します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -opAnalog NO_PROTECTION | USE_IF_AVAILABLE |必須 | NO_PLAYBACK | ACP_REQUIRED | CGMS-A_REQUIRED | USE_ACP_IF_AVAILABLE | USE_CGMS-A_IF_AVAILABLE  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">アナログ出力保護の制約。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -opDigital NO_PROTECTION | USE_IF_AVAILABLE |必須 | NO_PLAYBACK  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">デジタル出力保護の制約。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -runtimeBlacklist名 </span> <i class="+ topic/ph hi-d/i ">と</i> <span class="+ topic/ph pr-d/codeph codeph"> 値の </span> <i class="+ topic/ph hi-d/i "> </i> <span class="+ topic/ph pr-d/codeph codeph"> ペア  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">アプリケーションの実行時に、保護されたコンテンツへのアクセスが制限されています。 値は、次の形式で名前と値のペアをカンマで区切って構成します。 </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> os | application | release= stringValue  </span> </p> <p class="- topic/p ">例えば、<span class="codeph"> os=Win,release=2.0.1,application=AIR </span>のように指定します。 更新中に、残りの引数を指定せずに<span class="codeph"> -runtimeBlacklist </span>を使用し、リストからすべてのエントリを削除します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -runtimeLevel int  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツにアクセスするために、アプリケーションの実行時に指定した最小セキュリティレベルが必要であることを示します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -swf url  </span> </p> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -swf file= swf_file  </span>、 <span class="+ topic/ph pr-d/codeph codeph"> time= max_time_to_verify  </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツの再生が許可されるSWFアプリケーションの許可リストです。 複数の —swfオプションを指定して、複数のアプリケーションを使用できるようにすることができます。 AIRまたはSWFアプリケーションを指定しない場合、すべてのアプリケーションがこのコンテンツにアクセスする可能性があります。 更新時に、-swfを残りの引数なしで使用すると、リストからすべてのエントリが削除されます。 SWFをハッシュ値で識別するには、ハッシュを計算する対象のSWFファイルと、SWF検証の完了に必要な最大時間（秒）を指定します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -k name=value  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ポリシーに追加するカスタムキー/値を指定します。 複数の<span class="codeph"> -k </span>オプションを指定できます。 更新中に、残りの引数を指定せずに<span class="codeph"> -k </span>を使用し、すべてのプロパティを削除します。 このデータの解釈または処理は、Adobeアクセスライセンスサーバの実装に完全に依存します。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -p name=value  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">カスタムプロパティを追加します。このプロパティは、各クライアント用に生成されたライセンスに表示されます。 複数の<span class="codeph"> -p </span>オプションを指定して、複数のプロパティを追加できます。 更新中に、残りの引数を指定せずに<span class="codeph"> -p </span>を使用し、すべてのプロパティを削除します。 このデータの解釈や処理は、クライアントアプリケーションの実装に完全に依存します。 </p> </td> 
  </tr> 
 </tbody> 
</table>

