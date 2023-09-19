---
description: ストリームと再生リスト（マニフェスト）の制限と要件を確認します。
title: コンテンツとマニフェストの要件
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---

# コンテンツとマニフェストの要件{#content-and-manifest-requirements}

ストリームと再生リスト（マニフェスト）の制限と要件を確認します。

<table id="table_D7C38CD3B4D24C3D9A3B55D8CEFE7366"> 
 <tbody> 
  <tr> 
   <td colname="col1"> コンテンツセグメントの期間 </td> 
   <td colname="col2"> セグメントの期間は、マニフェストファイルで指定されているターゲット期間を超えてはなりません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> コンテンツ要件 </td> 
   <td colname="col2"> すべての TS セグメントは、キーフレームで始まる必要があります。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> HLS コンテンツ </td> 
   <td colname="col2"> <p>次の点に注意してください。 
     <ul id="ul_B226605345EA46F69DA1380E16826117"> 
      <li id="li_6564DC0E879544BB8513DD2D1CFBA8DE">AAC-SSR オーディオはサポートされていません。 </li> 
      <li id="li_B73CAEBE4347406EA4DB25551B444BDA">オーディオコーデック AC3 および拡張 AC3 はサポートされていません。 </li> 
      <li id="li_5986DD33C0FE485D99D4C00E2E6012CA">HLS は不連続を伴うストリームですが、不連続マーカーはサポートされていません。 </li> 
      <li id="li_FED8686372DF4A39BAABC531BA4EB137">HLS Live はタイムスタンプのロールオーバーをサポートしていません。 </li> 
      <li id="li_565CFBEAD9874BA48F6E25B0893BF131">HLS ライブストリームの DVR ウィンドウ内の広告は解決されません。 </li> 
      <li id="li_7D22EA32C94240D79EDDA96D9E72FE8F">バイト範囲は、AES-128 で暗号化されたコンテンツではサポートされていません。 </li> 
     </ul></p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> DASH コンテンツ </td> 
   <td colname="col2"> <p>次の点に注意してください。 
     <ul id="ul_9D33C2418F9F49DEAE0E642301726F89"> 
      <li id="li_74C69A21A7BD4831B92F0D57900E1CB1">ライブストリームの場合 — 動的タイプのライブプロファイルがサポートされます。 </li> 
      <li id="li_0C8743DB152047819D23C9F180998AD7">VOD ストリームの場合 — 静的タイプのライブプロファイルがサポートされます。 </li> 
      <li id="li_FBC6828663FB413798A4BDAF0B9831AA">VOD ストリームの場合 — オンデマンドプロファイルは、広告ワークフローに対しては認定されていません。 </li> 
      <li id="li_4393B9B1F6144BDEAE484C879750ED23">複数のピリオドを含む DASH ストリームの再生はサポートされていません。 </li> 
      <li id="li_6A2CEC4E974C4D44A45F5503A1A9D8D0">埋め込みキャプション(608/708)は、アクセシビリティタグを介して通知され、サポートされています。 </li> 
      <li id="li_EDE93DF4F3A64A53BA80877F701A8F0D">断片化/セグメント化された VTT ファイルはサポートされていません。 </li> 
      <li id="li_8897F73611194030A490A4FF1178364C">インバンドカスタムタグを含むストリームは認定されていません。 </li> 
     </ul></p> </td> 
  </tr> 
 </tbody> 
</table>
