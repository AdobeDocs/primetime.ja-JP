---
title: 出力保護の制御
description: 出力保護の制御
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 0%

---


# 出力保護コントロール{#output-protection-controls}

**外部レンダリングデバイスへの出力を保護するかどうかを制御します。アナログ出力とデジタル出力を個別に指定します。**

外部レンダリングデバイスへの出力を制限するかどうかを制御します。 外部デバイスは、コンピューターに埋め込まれていないビデオまたはオーディオデバイスと定義されます。 外部デバイスのリストは、ノートパソコンなどの内蔵ディスプレイを除きます。 アナログ出力とデジタル出力の制限は、独立して指定できます。

以下のオプション/実施レベルを使用できます。

<table frame="all" colsep="0" rowsep="1" id="adobetable_fvw_5fx_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">オプション </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">アナログデバイスでサポート </p> </th> 
   <th colname="3" class="- topic/entry entry"> <p class="- topic/p ">デジタルデバイスでサポート </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">必須</b>  — 外部デバイスにコンテンツを再生するには、ACP（アナログコピー保護）またはCGMS（コピー生成管理システム）のアナログ(CGMS-A)出力保護を有効にする必要があります。Adobe・アクセス・クライアントは、ACPまたはCGMS-Aを使用して出力保護を有効にする必要があります。両方をサポートするデバイスでは、AdobeAccess 3.0クライアントは両方を有効にしようとします。 ただし、コンテンツの再生を有効にする必要があるのは1つだけです。 </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">ACP必須</b> - ACP出力保護が必要です。CGMS-Aでは再生が許可されません。Adobeアクセス2.0クライアントは、このオプションをサポートしていません。 設定した場合、AdobeAccess 2.0クライアントは、「再生なし」オプションが指定された場合と同じ動作になります。 </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">CGMS-A Required</b>  — CGMS-A出力保護が必要です。ACPでは再生できません。 Adobeアクセス2.0クライアントは、このオプションをサポートしていません。 設定した場合、AdobeAccess 2.0クライアントは、「再生なし」オプションが指定された場合と同じ動作になります。 </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">使用可能な場合</b> - ACPおよびCGMS-Aの出力保護が可能な場合は有効にし、利用できない場合は再生を許可します。Adobe・アクセス3.0クライアントは、可能であれば、ACPとCGMS-Aの両方を有効にしようとします。 Adobeアクセス2.0クライアントは、ACPまたはCGMS-Aのいずれかを有効にしようとします。例えば、Adobe・アクセス・クライアントは、ACPまたはCGMS-Aを有効にする試みを行います。試行が成功すると、他のオプションは有効になりません。 試行が失敗した場合は、もう1つのオプションを有効にするための再試行が行われます。 両方の試行が失敗した場合でも、コンテンツは再生されます。 </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">ACPを使用する（使用可能な場合）</b> - ACP出力保護を有効にしようとするが、使用できない場合は再生を許可する。保護は、CGMS-Aでは使用できません。Adobeアクセス2.0クライアントは、このオプションをサポートしていません。 設定した場合、AdobeAccess 2.0クライアントは、「保護なし」オプションが指定された場合と同じ動作になります。 </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">「Use CGMS-A if available」  </b>— CGMS-Aの出力保護を有効にしようとします（使用可能な場合）。使用できない場合は再生を許可します。保護はACPでは使用できません。 Adobeアクセス2.0クライアントは、このオプションをサポートしていません。 設定した場合、AdobeAccess 2.0クライアントは、「保護なし」オプションが指定された場合と同じ動作になります。 </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">保護なし</b>  — アナログ出力とデジタル出力に対しては、出力保護の有効化は実施されません。 </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">再生なし</b>  — アナログ出力とデジタル出力のために外部デバイスでの再生を許可しません。 </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>これらのルールはすべてのプラットフォームに一貫して適用されますが、現在のところ、Windowsプラットフォームで出力保護を安全に有効にできるのは、唯一の方法です。 他のプラットフォーム（MacintoshやLinuxなど）では、サードパーティのアプリケーションで使用できるサポートするオペレーティングシステム機能はありません。

使用例：一部のコンテンツでは、出力保護コントロールが適用される場合があり、コンテンツ配信者が保護レベルを設定できます。 「必須」を指定し、Macintoshで再生を試行した場合、クライアントは外部デバイスでコンテンツを再生しません。 ただし、コンテンツは内部モニターで再生されます。

「必須」を指定し、Linuxで再生を試行した場合、クライアントは内部デバイスと外部デバイスを区別できないので、どのデバイスでもコンテンツを再生しません。

「使用可能な場合に使用」を指定した場合は、可能な場合は出力保護が有効になります。 例えば、Certified Output Protection Protocol(COPP)をサポートするWindowsコンピューターでは、コンテンツは出力保護と共に外部ディスプレイに渡されます。 この例は、「選択可能な出力制御」と呼ばれる場合もあります。
