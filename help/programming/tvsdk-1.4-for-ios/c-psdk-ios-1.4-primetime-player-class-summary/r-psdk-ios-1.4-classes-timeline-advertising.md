---
description: タイムライン内で発生する広告に関する情報を提供するクラスです。
title: Timeline advertising クラス
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# Timeline advertising クラス{#timeline-advertising-classes}

タイムライン内で発生する広告に関する情報を提供するクラスです。

<table frame="all" colsep="1" rowsep="1" id="table_1A59E777BA99466793D586286F19E933"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> 名前 </th> 
   <th colname="2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAd.html" format="html" scope="external"> PTAd</a> </td> 
   <td colname="2">広告の抽象化を定義し、すべての広告情報を保持するクラス。 一意の ID、期間および MediaResourcede によって定義されます。 MediaResource には、実際の広告コンテンツが存在する URL が含まれます。 
    <pre>
      コンテンツにスプライスされるプライマリリニアアセットを表します。 オプションで、リニアアセットと共に表示する必要があるコンパニオンアセットの配列を含めることができます。
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAdAsset.html" format="html" scope="external"> PTAdAsset</a> </td> 
   <td colname="2">表示するアセットを表すクラス。 
    <pre>
      表示されるアセットを表します。
    </pre> 
    <pre>
      広告アセットを表すクラス。
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAdBannerView.html" format="html" scope="external"> PTAdBannerView</a> </td> 
   <td colname="2">
    <pre>
      バナーアセットを表示します。 アプリケーションは、このユーティリティクラスの新しいインスタンスを作成し、バナーアセットを設定して、ビューに追加する必要があります。 バナーのインプレッションとクリックの追跡は、このクラスによって内部的に管理されます。
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAdBreak.html" format="html" scope="external"> PTAdBreak</a> </td> 
   <td colname="2">再生中にある時点で再生される、複数の広告に対して統合ビューを提供するクラス。 
    <pre>
      コンテンツにスプライスされる広告の連続したシーケンスを表します。
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAdClick.html" format="html" scope="external"> PTAdClick</a> </td> 
   <td colname="2">アセットに関連付けられたクリックインスタンスを表すクラス。 このインスタンスには、クリックスルー URL に関する情報と、ユーザーに追加情報を提供するために使用できるタイトルが含まれています。 
    <pre>
      アセットに関連付けられたクリックインスタンスを表します。 このインスタンスには、クリックスルー URL に関する情報と、ユーザーに追加情報を提供するために使用できるタイトルが含まれています。
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTAdPolicyInfo.html" format="html" scope="external"> PTAdPolicyInfo</a> </td> 
   <td colname="2"> AdPolicySelector API 呼び出しのプロパティを定義するプロトコル。 これらのプロパティは、各広告の動作を強制するコンテキストを提供します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">PTAdPolicySelector</td> 
   <td colname="2"> 広告の動作を適用する広告ポリシーセレクタープロトコル。 アプリケーションは、必要なすべてのメソッドを実装するか、既存のデフォルトのポリシーセレクタークラスを拡張して特定の動作をカスタマイズすることで、このプロトコルに準拠できます。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> PTAdTimeline</td> 
   <td colname="2"> コンテンツ内の改ページのタイムラインを表すクラス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> 
    <pre>
     <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTContentResolver.html" format="html" scope="external"> PTContentResolver</a> クラス 
     <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Protocols/PTContentResolver.html" format="html" scope="external"> PTContentResolver</a> protocol
    </pre> </td> 
   <td colname="2"> Adobe Primetime Ad Decisioning プロセスの広告解決部分を処理するクラス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Protocols/PTContentResolverDelegate.html" format="html" scope="external"> PTContentResolverDelegate</a> </td> 
   <td colname="2"> カスタムコンテンツリゾルバー ( <span class="codeph"> PTContentResolver</span> ) は、を使用して、コンテンツ解決のステータスをデリゲートするように伝える必要があります。 </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Constants/PTPlacementType.html" format="html" scope="external"> PTPlacementType</a> </td> 
   <td colname="2">配置情報リクエストを抽象化するクラス。 解決された各広告には、1 つの配置情報が添付されている必要があります。 配置情報は、広告がタイムライン上のどこに配置されるかを示します。 次のような情報が含まれます。 
    <ul id="ul_A9105A78F0C24488BCD5E3F2EE62A3EE"> 
     <li id="li_01E968A4330D4B40BA1EB6F4A6000FFD">配置の位置（ミリ秒） </li> 
     <li id="li_A3DC9498BEE14FBA9E7A5D26874F3984">配置のタイプ（プリロール、ミッドロールまたはポストロール） </li> 
     <li id="li_4B9094DD318B4792854A377CC6064232">置き換えられるメインコンテンツチャンクの期間 </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
