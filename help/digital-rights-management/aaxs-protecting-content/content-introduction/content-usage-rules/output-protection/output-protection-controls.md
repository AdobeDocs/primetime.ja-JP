---
title: 出力保護制御
description: 出力保護制御
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 0%

---

# 出力保護制御 {#output-protection-controls}

**外部レンダリングデバイスへの出力を保護するかどうかを制御します。 アナログ出力とデジタル出力を個別に指定します。**

外部レンダリングデバイスへの出力を制限するかどうかを制御します。 外部デバイスは、コンピュータに埋め込まれていないビデオまたはオーディオデバイスと定義されます。 外部デバイスのリストは、ノートブックコンピューターなどの統合ディスプレイを除外します。 アナログ出力とデジタル出力の制限は、独立して指定できます。

適用の次のオプション/レベルを使用できます。

<table frame="all" colsep="0" rowsep="1" id="adobetable_fvw_5fx_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">オプション </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">アナログデバイスでサポート </p> </th> 
   <th colname="3" class="- topic/entry entry"> <p class="- topic/p ">デジタルデバイスでのサポート </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">必須</b>  — 外部デバイスにコンテンツを再生するには、Analog Copy Protection(ACP) または Copy Generation Management System - Analog(CGMS-A) の出力保護を有効にする必要があります。 Adobe・アクセス・クライアントは、ACP または CGMS-A を使用して出力保護を有効にする必要があります。両方をサポートするデバイスでは、AdobeAccess 3.0 クライアントは両方を有効にしようとします。 ただし、コンテンツの再生を有効にする必要があるのは 1 つだけです。 </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">ACP 必須</b> — ACP 出力保護が必要です。 CGMS-A では再生は許可されていません。AdobeAccess 2.0 クライアントは、このオプションをサポートしていません。 設定した場合、AdobeAccess 2.0 クライアントは、「再生なし」オプションが指定された場合と同じように動作します。 </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">CGMS-A が必要</b> — CGMS-A 出力保護が必要です。 ACP では再生が許可されていません。 AdobeAccess 2.0 クライアントは、このオプションをサポートしていません。 設定した場合、AdobeAccess 2.0 クライアントは、「再生なし」オプションが指定された場合と同じように動作します。 </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">使用可能な場合は、次を使用します。</b> — ACP および CGMS-A 出力保護を有効にしようとします（使用可能な場合）。使用できない場合は再生を許可します。 Adobeアクセス 3.0 クライアントは、可能な場合は、ACP と CGMS-A の両方を有効にしようとします。 Adobeアクセス 2.0 クライアントは、ACP または CGMS-A を有効にしようとします。例えば、Adobe・アクセス・クライアントが ACP または CGMS-A を有効にしようとします。試行が成功した場合、その他のオプションは有効になりません。 試行が失敗した場合は、もう一方のオプションを有効にするために、もう一度試みます。 両方の試行が失敗しても、コンテンツは再生されます。 </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">ACP を使用（可能な場合）</b> — ACP 出力保護を有効にしようとします（使用できる場合）。ただし、使用できない場合は再生を許可します。 保護は CGMS-A では利用できません。AdobeAccess 2.0 クライアントは、このオプションをサポートしていません。 設定した場合、AdobeAccess 2.0 クライアントは、「No Protection」オプションが指定された場合と同じように動作します。 </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">CGMS-A を使用（可能な場合） </b>— CGMS-A 出力保護を有効にしようとします（使用可能な場合）が、使用できない場合は再生を許可します。 ACP では保護を利用できません。 AdobeAccess 2.0 クライアントは、このオプションをサポートしていません。 設定した場合、AdobeAccess 2.0 クライアントは、「No Protection」オプションが指定された場合と同じように動作します。 </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">- </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">保護なし</b>  — アナログ出力とデジタル出力に対しては、出力保護のイネーブルメントは適用されません。 </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">再生なし</b>  — アナログ出力やデジタル出力用の外部デバイスへの再生を許可しません。 </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">はい </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>これらのルールは、すべてのプラットフォームで一貫して適用されますが、現在、Windows プラットフォームで出力保護を安全に有効にすることしかできません。 その他のプラットフォーム（Macintosh や Linux など）では、サードパーティのアプリケーションで使用できるオペレーティングシステムの機能はサポートされていません。

使用例：一部のコンテンツは出力保護制御を実施し、保護レベルはコンテンツ配布者が設定できます。 「必須」を指定し、Macintosh での再生を試行した場合、クライアントは外部デバイスではコンテンツを再生しません。 ただし、内蔵モニターではコンテンツが再生されます。

「必須」を指定し、Linux で再生を試みる場合、クライアントは内部デバイスと外部デバイスを区別できないので、どのデバイスでもコンテンツを再生しません。

「使用可能な場合に使用」を指定した場合は、可能な限り出力保護がオンになります。 例えば、Certified Output Protection Protocol(COPP) をサポートする Windows マシンでは、コンテンツは出力保護付きで外部ディスプレイに渡されます。 この例は、「選択可能な出力制御」と呼ばれる場合があります。
