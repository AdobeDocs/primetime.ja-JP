---
description: HLS ストリームと DASH ストリームでは、同じビデオの短いバーストに対して異なるビットレートエンコーディング（プロファイル）を提供します。 TVSDK は、現在のバッファリングレベルと使用可能な帯域幅に基づいて、各バーストの品質レベルを選択できます。
title: ビデオ画質の可変ビットレート (ABR)
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 0%

---

# 概要 {#adaptive-bit-rates-abr-for-video-quality-overview}

HLS ストリームと DASH ストリームでは、同じビデオの短いバーストに対して異なるビットレートエンコーディング（プロファイル）を提供します。 TVSDK は、現在のバッファリングレベルと使用可能な帯域幅に基づいて、各バーストの品質レベルを選択できます。

TVSDK は、常にビットレートを監視し、現在のネットワーク接続に最適なビットレートでコンテンツが再生されるようにします。 可変ビットレート (ABR) 切り替えポリシーと、マルチビットレート (MBR) ストリームの初期ビットレート、最小ビットレート、最大ビットレートを設定できます。 TVSDK は、指定した設定で最適な再生エクスペリエンスを提供するビットレートに自動的に切り替えます。

<table id="table_AF838E082235406AA359BF1C1A77F85F"> 
 <tbody> 
  <tr> 
   <td colname="col01"> 初期ビットレート </td> 
   <td colname="col2"> <p>最初のセグメントの目的の再生ビットレート (bps)。 </p> <p>再生が開始すると、最初のセグメントには、初期ビットレート以上の最も近いプロファイルが使用されます。 最小ビットレートが定義され、初期ビットレートが最小ビットレートより低い場合、 TVSDK は最小ビットレートよりも低いビットレートを持つプロファイルを選択します。 初期レートが最大レートを超える場合、 TVSDK は最大レートを下回る最も高いレートを選択します。 初期ビットレートがゼロまたは未定義の場合、初期ビットレートは ABR ポリシーによって決定されます。 </p> <p><span class="codeph"> getABRInitialBitRate</span> 1 秒あたりのバイト数を表す integer 値を返します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> 最小ビットレート </td> 
   <td colname="col2"> <p>ABR が切り替え可能な最も低いビットレートです。 </p> <p>ABR 切り替えでは、このビットレートより低いビットレートを持つプロファイルは無視されます。 <span class="codeph"> getABRMinBitRate</span> bps プロファイルを表す integer 値を返します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> 最大ビットレート </td> 
   <td colname="col2"> <p>ABR が切り替え可能な最大許容ビットレートです。 </p> <p>ABR 切り替えでは、このビットレートよりも高いビットレートを持つプロファイルは無視されます。 <span class="codeph"> getABRMaxBitRate</span> bps プロファイルを表す integer 値を返します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> ABR 切り替えポリシー </td> 
   <td colname="col2"> <p>可能な場合は、再生が徐々に最も高いビットレートのプロファイルに切り替わります。 ABR 切り替えのポリシーを設定できます。このポリシーは、TVSDK がプロファイルを切り替える速度を決定します。 デフォルトはです。 <span class="codeph"> ABR_MODERATE</span>. </p> <p>TVSDK がより高いビットレートに切り替えると決定した場合、プレーヤーは現在の ABR ポリシーに基づいて、切り替える理想的なビットレートプロファイルを選択します。 
     <ul id="ul_AC9C99D84A3B4A8DBD1A05CC05DEE771"> 
      <li id="li_B79C0AA2CBFB42FF98A257CEC9C400BA"><span class="codeph"> ABR_CONSERVATIVE</span>：帯域幅が現在のビットレートより 50%高い場合、次に高いビットレートを持つプロファイルに切り替えます。 </li> 
      <li id="li_38CC3A95D8634F359D0F7C273D0108C0"><span class="codeph"> ABR_MODERATE</span>：帯域幅が現在のビットレートより 20%高い場合、次に高いビットレートプロファイルに切り替えます。 </li> 
      <li id="li_E845C035420D4B3FB2B179F448F8CA85"><span class="codeph"> ABR_AGGRESSIVE</span>：帯域幅が現在のビットレートよりも高い場合、最も高いビットレートのプロファイルに即座に切り替えます。 </li> 
     </ul> </p> <p>初期ビットレートが 0 の場合、または指定されていないがポリシーが指定された場合、保守的なポリシーの最も低いビットレートプロファイル、中程度のポリシーの利用可能なプロファイルの中央値に最も近いプロファイル、攻撃的なポリシーの最も高いビットレートプロファイルで再生が開始されます。 </p> <p>このポリシーは、最小ビットレートと最大ビットレートの制約で機能します（これらのレートが指定されている場合）。 </p> <p> <span class="codeph"> getABRPolicy</span> 現在の設定を <span class="codeph"> ABRControlParameters</span> enum: <span class="codeph"> ABR_CONSERVATIVE</span>, <span class="codeph"> ABR_MODERATE</span>または <span class="codeph"> ABR_AGGRESSIVE</span>. </p> <p>詳しくは、 ABR 制御パラメータ API ドキュメントを参照してください。 </p> </td> 
  </tr> 
 </tbody> 
</table>

次の情報に留意してください。

* TVSDK は、制御パラメーターに厳密に準拠しているよりも連続再生を優先するので、 TVSDK のフェイルオーバーメカニズムが設定を上書きする場合があります。
* ビットレートが変更されると、 TVSDK は `onProfileChanged` イベント `PlaybackEventListener`.

* ABR 設定はいつでも変更でき、プレーヤーは最新の設定に最も近いプロファイルを使用するように切り替えます。

例えば、ストリームに次のプロファイルが含まれている場合、

* 1: 300000
* 2: 700000
* 3: 1500000
* 4: 2400000
* 5: 4000000

300000 ～ 2000000の範囲を指定した場合、 TVSDK は 1、2、3 のプロファイルのみを考慮します。 これにより、アプリケーションは、Wi-Fi から 3G への切り替えや、電話、タブレット、デスクトップコンピューターなどの様々なデバイスへの切り替えなど、様々なネットワーク条件に合わせて調整できます。

ABR 制御パラメーターを設定するには、 `ABRControlParameter` クラス。
