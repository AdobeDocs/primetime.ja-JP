---
description: TVSDK は現在、TVSDK 広告、ダイレクト広告の時間、カスタム広告マーカーに対して、広告プロバイダーのメタデータの組み込みサポートを提供しています。
title: 広告挿入のタイプ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---

# 広告挿入のタイプ {#ad-insertion-types}

TVSDK は現在、TVSDK 広告、ダイレクト広告の時間、カスタム広告マーカーに対して、広告プロバイダーのメタデータの組み込みサポートを提供しています。

VOD およびライブ/リニアコンテンツでは、次のタイプの広告挿入ワークフローをサポートしています。

<table id="table_1C3A659BDDB7453CA953A103045FCA01"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 挿入タイプ </th> 
   <th colname="col2" class="entry"> サポート対象… </th> 
   <th colname="col3" class="entry"> 説明 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> Adobe Primetime ad decisioning ads </td> 
   <td colname="col2">VOD <p>ライブ </p> <p>線形 </p> </td> 
   <td colname="col3">リファレンス実装では、次の情報が提供されます。 <span class="codeph"> AuditudeMetadata</span> Primetime ads 部分で提供される情報に基づいて、Primetime ad decisioning( 旧称：Auditude) 用にサーバーに接続するための情報</a> JSON 設定ファイルの</a>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> ダイレクト広告ブレーク </td> 
   <td colname="col2"> VOD </td> 
   <td colname="col3">入力 JSON ファイルに広告の URL を指定する必要があります。 TVSDK は、広告を解決しようとすると、ダイレクト広告ブレークリゾルバーを呼び出し、JSON 設定ファイルで指定されたダイレクト広告ブレーク情報に基づいて広告を解決します</a>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> カスタム広告マーカー </td> 
   <td colname="col2"> VOD </td> 
   <td colname="col3">カスタム広告マーカーは、ビデオストリームにメインコンテンツと広告の両方が含まれているが、広告の位置とタイミングに関する情報が含まれていない場合に役立ちます。 例えば、外部の CMS を介して広告の位置情報を取得する別の方法で取得する場合は、カスタム広告マーカーを定義して、プレーヤータイムラインに渡すことができます。 <p>広告挿入用のプレーヤーを設定するには、JSON 設定ファイルのカスタム広告メタデータセクションに広告メタデータを渡す必要があります</a>：参照実装にサポートする広告プロバイダー実装を持ちます。 </p> </td>
  </tr>
 </tbody>
</table>
