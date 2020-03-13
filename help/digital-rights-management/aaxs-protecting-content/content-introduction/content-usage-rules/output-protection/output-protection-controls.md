---
seo-title: 出力保護の制御
title: 出力保護の制御
uuid: 1f4cc617-7f14-4952-8e61-6acbdf01d10e
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c

---


# 出力保護の制御 {#output-protection-controls}

**外部レンダリングデバイスへの出力を保護するかどうかを制御します。 アナログ出力とデジタル出力を個別に指定します。**

外部レンダリングデバイスへの出力を制限するかどうかを制御します。 外部デバイスは、コンピューターに埋め込まれていないビデオまたはオーディオデバイスと定義されます。 外部デバイスのリストには、ノートブックコンピューターなどの統合ディスプレイが含まれていません。 アナログ出力とデジタル出力の制限は、独立して指定できます。

以下のオプション/実施レベルを使用できます。

<table frame="all" colsep="0" rowsep="1" id="adobetable_fvw_5fx_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">オプション </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">アナログデバイスでのサポート </p> </th> 
   <th colname="3" class="- topic/entry entry"> <p class="- topic/p ">デジタルデバイスでのサポート </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">必須</b> — 外部デバイスでコンテンツを再生するには、ACP（アナログコピー保護）またはCGMS（コピー生成管理システム） — アナログ(CGMS-A)の出力保護を有効にする必要があります。 Adobe Accessクライアントは、ACPまたはCGMS-Aを使用して出力保護を有効にする必要があります。両方をサポートするデバイスでは、Adobe Access 3.0クライアントは両方を有効にしようとします。 ただし、コンテンツの再生を有効にする必要があるのは1つだけです。 </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">ACPが必要</b> — ACP出力保護が必要です。 CGMS-Aでの再生は許可されません。Adobe Access 2.0クライアントは、このオプションをサポートしていません。 設定した場合、Adobe Access 2.0クライアントは、「再生なし」オプションが指定された場合と同じ動作をします。 </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">CGMS-Aが必要</b> — CGMS-A出力保護が必要です。 ACPでの再生は許可されません。 Adobe Access 2.0クライアントは、このオプションをサポートしていません。 設定した場合、Adobe Access 2.0クライアントは、「再生なし」オプションが指定された場合と同じ動作をします。 </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">使用可能な場合に使用</b> — ACPおよびCGMS-Aの出力保護を有効にし、使用できない場合は再生を許可します。 Adobe Access 3.0クライアントは、可能であれば、ACPとCGMS-Aの両方を有効にしようとします。 Adobe Access 2.0クライアントは、ACPまたはCGMS-Aのいずれかを有効にしようとします。例えば、Adobe AccessクライアントはACPまたはCGMS-Aを有効にしようとします。試行が成功した場合、もう1つのオプションは有効になりません。 試行が失敗した場合は、もう一方のオプションを有効にするための再試行が行われます。 両方の試行が失敗した場合でも、コンテンツは再生されます。 </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">ACPを使用(利用可能な場合</b> )— ACP出力保護を有効にしようとしますが、有効になっていない場合は再生を許可します。 保護はCGMS-Aでは利用できません。Adobe Access 2.0クライアントは、このオプションをサポートしていません。 設定した場合、Adobe Access 2.0クライアントは、「保護なし」オプションが指定された場合と同じ動作をします。 </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">CGMS-Aを使用（可能な場合） </b>— CGMS-Aの出力保護を有効にしようとします（可能な場合）が、使用できない場合は再生を許可します。 保護はACPでは使用できません。 Adobe Access 2.0クライアントは、このオプションをサポートしていません。 設定した場合、Adobe Access 2.0クライアントは、「保護なし」オプションが指定された場合と同じ動作をします。 </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">保護なし</b> — アナログ出力およびデジタル出力に対しては、出力保護の有効化は実施されません。 </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">再生なし</b> — アナログおよびデジタル出力用に外部デバイスでの再生を許可しません。 </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>これらのルールはすべてのプラットフォームで一貫して適用されますが、現在のところ、Windowsプラットフォームで出力保護を安全に有効にすることしかできません。 その他のプラットフォーム（MacintoshやLinuxなど）では、サードパーティのアプリケーションで使用できるサポートするオペレーティングシステム機能はありません。

使用例：一部のコンテンツでは、出力保護の制御が強制され、保護のレベルをコンテンツ配布者が設定できます。 「必須」を指定し、Macintoshでの再生を試みた場合、クライアントは外部デバイスでコンテンツを再生しません。 ただし、コンテンツは内部モニターで再生されます。

「必須」を指定し、Linuxで再生を試みると、クライアントは内部デバイスと外部デバイスを区別できないので、どのデバイスでもコンテンツを再生しません。

「使用可能な場合に使用」を指定すると、可能な場合は出力保護が有効になります。 例えば、Certified Output Protection Protocol(COPP)をサポートするWindowsマシンでは、コンテンツは出力保護と共に外部ディスプレイに渡されます。 この例は、「選択可能な出力制御」と呼ばれることもあります。
