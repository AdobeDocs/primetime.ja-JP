---
description: TVSDKは、現在、TVSDK広告、ダイレクト広告の時間、カスタム広告マーカーに対する組み込み広告プロバイダーメタデータのサポートを提供しています。
seo-description: TVSDKは、現在、TVSDK広告、ダイレクト広告の時間、カスタム広告マーカーに対する組み込み広告プロバイダーメタデータのサポートを提供しています。
seo-title: 広告挿入タイプ
title: 広告挿入タイプ
uuid: 6b5c3555-1ddd-4215-8bb2-03d16bb818c5
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# 広告挿入タイプ {#ad-insertion-types}

TVSDKは、現在、TVSDK広告、ダイレクト広告の時間、カスタム広告マーカーに対する組み込み広告プロバイダーメタデータのサポートを提供しています。

VODおよびライブ/リニアコンテンツでは、次のタイプの広告挿入ワークフローをサポートしています。

<table id="table_1C3A659BDDB7453CA953A103045FCA01"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 挿入タイプ </th> 
   <th colname="col2" class="entry"> サポート対象 </th> 
   <th colname="col3" class="entry"> 説明 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> Adobe Primetime ad decisioning広告 </td> 
   <td colname="col2">VOD <p>ライブ </p> <p>線形 </p> </td> 
   <td colname="col3">参照実装は、JSON設定ファイルのPrimetime ads部分に指定された情報に基づいて <span class="codeph"> 、Primetime ad decisioning（旧称Auditude）のサーバーに接続するAuditudeMetadata</span> 情報を提供します</a></a>。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> ダイレクト広告の時間 </td> 
   <td colname="col2"> VOD </td> 
   <td colname="col3">広告のURLは、入力JSONファイルで指定する必要があります。 TVSDKは、広告を解決しようとすると、ダイレクト広告ブレークリゾルバーを呼び出し、JSON設定ファイルで提供されるダイレクト広告ブレーク情報に基づいて広告を解決します</a>。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> カスタム広告マーカー </td> 
   <td colname="col2"> VOD </td> 
   <td colname="col3">カスタム広告マーカーは、ビデオストリームにメインコンテンツと広告の両方が含まれ、広告の位置とタイミングに関する情報が含まれない場合に役立ちます。 例えば、外部CMSを介して広告の位置情報を取得する別の方法で、カスタム広告マーカーを定義して、プレーヤーのタイムラインに渡すことができます。 <p>広告挿入用のプレーヤーを設定するには、JSON設定ファイルのカスタム広告メタデータセクションに広告メタデータを渡す必要があります。このファイルには</a>、参照実装にサポートする広告プロバイダーの実装が含まれています。 </p> </td>
  </tr>
 </tbody>
</table>