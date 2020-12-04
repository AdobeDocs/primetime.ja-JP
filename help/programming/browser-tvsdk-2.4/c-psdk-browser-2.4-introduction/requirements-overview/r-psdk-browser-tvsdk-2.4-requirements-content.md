---
description: ストリームおよび再生リスト（マニフェスト）の制限と要件を確認します。
seo-description: ストリームおよび再生リスト（マニフェスト）の制限と要件を確認します。
seo-title: コンテンツとマニフェストの要件
title: コンテンツとマニフェストの要件
uuid: 22ee7d02-b06d-4162-a8a4-a2391658fdb3
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---


# コンテンツとマニフェストの要件{#content-and-manifest-requirements}

ストリームおよび再生リスト（マニフェスト）の制限と要件を確認します。

<table id="table_D7C38CD3B4D24C3D9A3B55D8CEFE7366"> 
 <tbody> 
  <tr> 
   <td colname="col1"> コンテンツセグメントの長さ </td> 
   <td colname="col2"> セグメントの長さは、マニフェストファイルで指定されているターゲットの長さを超えてはなりません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> コンテンツ要件 </td> 
   <td colname="col2"> すべてのTSセグメントは、キーフレームと開始する必要があります。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> HLSコンテンツ </td> 
   <td colname="col2"> <p>次の点に注意してください。 
     <ul id="ul_B226605345EA46F69DA1380E16826117"> 
      <li id="li_6564DC0E879544BB8513DD2D1CFBA8DE">AAC-SSRオーディオはサポートされていません。 </li> 
      <li id="li_B73CAEBE4347406EA4DB25551B444BDA">オーディオコーデックAC3および拡張AC3はサポートされていません。 </li> 
      <li id="li_5986DD33C0FE485D99D4C00E2E6012CA">不連続を持つHLSストリームですが、不連続マーカはサポートされません。 </li> 
      <li id="li_FED8686372DF4A39BAABC531BA4EB137">HLS Liveはタイムスタンプのロールオーバーをサポートしていません。 </li> 
      <li id="li_565CFBEAD9874BA48F6E25B0893BF131">HLSライブストリームのDVR時間枠内の広告は解決されません。 </li> 
      <li id="li_7D22EA32C94240D79EDDA96D9E72FE8F">バイト範囲は、AES-128暗号化されたコンテンツではサポートされません。 </li> 
     </ul></p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> DASHコンテンツ </td> 
   <td colname="col2"> <p>次の点に注意してください。 
     <ul id="ul_9D33C2418F9F49DEAE0E642301726F89"> 
      <li id="li_74C69A21A7BD4831B92F0D57900E1CB1">ライブストリームの場合 — 動的タイプのライブプロファイルがサポートされます。 </li> 
      <li id="li_0C8743DB152047819D23C9F180998AD7">VODストリームの場合 — 静的タイプのライブプロファイルがサポートされます。 </li> 
      <li id="li_FBC6828663FB413798A4BDAF0B9831AA">VODストリームの場合 — オンデマンドプロファイルは、広告ワークフローに対して認証されていません。 </li> 
      <li id="li_4393B9B1F6144BDEAE484C879750ED23">複数のピリオドを含むDASHストリームの再生はサポートされていません。 </li> 
      <li id="li_6A2CEC4E974C4D44A45F5503A1A9D8D0">アクセシビリティタグを介して署名される埋め込みキャプション(608/708)がサポートされます。 </li> 
      <li id="li_EDE93DF4F3A64A53BA80877F701A8F0D">フラグメント化/セグメント化されたVTTファイルはサポートされていません。 </li> 
      <li id="li_8897F73611194030A490A4FF1178364C">インバンドカスタムタグを持つストリームは認証されません。 </li> 
     </ul></p> </td> 
  </tr> 
 </tbody> 
</table>

