---
description: HLSストリームとDASHストリームは、同じビデオの短いバーストを目的として異なるビットレートエンコーディング(プロファイル)を提供します。 TVSDKは、使用可能な帯域幅に基づいて、各バーストの品質レベルを選択できます。
title: ビデオ画質に関する可変ビットレート(ABR)
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 0%

---


# 概要{#adaptive-bit-rates-abr-for-video-quality-overview}

HLSストリームとDASHストリームは、同じビデオの短いバーストを目的として異なるビットレートエンコーディング(プロファイル)を提供します。 TVSDKは、使用可能な帯域幅に基づいて、各バーストの品質レベルを選択できます。

TVSDKは、常にビットレートを監視し、現在のネットワーク接続に最適なビットレートでコンテンツが再生されるようにします。

可変ビットレート(ABR)切り替えポリシーと、マルチビットレート(MBR)ストリームの初期、最小、最大ビットレートを設定できます。 TVSDKは、指定された設定で最高の再生エクスペリエンスを提供するビットレートに自動的に切り替えます。

<table id="table_AF838E082235406AA359BF1C1A77F85F"> 
 <tbody> 
  <tr> 
   <td colname="col01"> 初期ビットレート </td> 
   <td colname="col2"> <p>最初のセグメントに対する目的の再生ビットレート（ビット/秒）。 再生開始の場合、最初のセグメントには、初期ビットレートと等しいかそれ以上の最も近いプロファイルが使用されます。 </p> <p> 最小ビットレートが定義され、初期ビットレートが最小ビットレートより低い場合、最小ビットレートを超える最小ビットレートを持つプロファイルがTVSDKによって選択されます。 初期レートが最大レートを超える場合、TVSDKは最大レートを下回る最も高いレートを選択します。 </p> <p>初期ビットレートが0または未定義の場合、初期ビットレートはABRポリシーによって決定されます。 </p> <p><span class="codeph"> getABRInitialBitRateは、1秒あたりのバイトプロファイルを表す整数値を</span> 返します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> 最小ビットレート </td> 
   <td colname="col2"> <p>ABRで切り替え可能な最小許容ビットレートです。 ABR切り替えでは、このビットレートより低いビットレートのプロファイルは無視されます。 </p> <p><span class="codeph"> getABRMinBitRateは、1秒あたりのビット数プロファイルを表す整数値を</span> 返します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> 最大ビットレート </td> 
   <td colname="col2"> <p>ABRで切り替え可能な最大許容ビットレートです。 ABR切り替えでは、このビットレートよりも大きいビットレートのプロファイルは無視されます。 </p> <p><span class="codeph"> getABRMaxBitRateは、1秒あたりのビット数プロファイルを表す整数値を返し</span> ます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> ABR切り替えポリシー </td> 
   <td colname="col2"> 可能な場合は、再生時のビットレートが徐々に最も高いプロファイルに切り替わります。 ABR切り替えポリシーを設定できます。これにより、TVSDKがプロファイルを切り替える速度が決まります。 デフォルトは<span class="codeph"> ABR_MODERATE</span>です。 <p>TVSDKがより高いビットレートに切り替えると判断した場合、プレイヤーは、現在のABRポリシーに基づいて、最適なビットレートプロファイルを選択して切り替えます。 
     <ul id="ul_AC9C99D84A3B4A8DBD1A05CC05DEE771"> 
      <li id="li_B79C0AA2CBFB42FF98A257CEC9C400BA"><span class="codeph"> ABR_CONSERVATIVE</span>:帯域幅が現在のビットレートより50 %以上大きい場合は、次に大きいビットレートを持つプロファイルに切り替えます。 </li> 
      <li id="li_38CC3A95D8634F359D0F7C273D0108C0"><span class="codeph"> ABR_MODERATE</span>:帯域幅が現在のビットレートより20%高い場合に、次に高いビットレートプロファイルに切り替えます。 </li> 
      <li id="li_E845C035420D4B3FB2B179F448F8CA85"><span class="codeph"> ABR_AGGRESSIVE</span>:帯域幅が現在のビットレートよりも大きい場合は、高いビットレートプロファイルに即座に切り替えます。 </li> 
     </ul> </p> <p>初期ビットレートが0であるか、指定されていないがポリシーが指定されている場合、保守的なビットレートプロファイルが最も低い再生開始、モデレートの使用可能なプロファイルの中央値ビットレートに最も近いプロファイル、積極的なビットレートプロファイルが最も高い再生。 </p> <p>このポリシーは、最小および最大ビットレートが指定されている場合は、その制約に従って機能します。 </p> <p><span class="codeph"> getABRPolicyは、ABRControlParametersenumから現在の設定を</span> 返し <span class="codeph"> </span> ます。 
     <ul id="ul_bd4_5kb_cz"> 
      <li id="li_E7C118AF48994454B7B3C016913DE545"><span class="codeph"> ABR_CONSERVATIVE</span> </li> 
      <li id="li_0A90BB42786449629CE7DD3364B385EE"><span class="codeph"> ABR_MODERATE</span> </li> 
      <li id="li_AFEB9B2862F24A369CA90596184A2883"><span class="codeph"> ABR_AGGRESSIVE</span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

次の情報に注意してください。

* TVSDKは、制御パラメーターに厳密に従うよりも継続的な再生エクスペリエンスのほうが優先されるので、TVSDKのフェイルオーバーメカニズムによって設定が上書きされる場合があります。
* ビットレートが変更されると、TVSDKは`onProfileChanged`イベントを`PlaybackEventListener`にディスパッチします。

* ABR設定はいつでも変更でき、プレイヤーは最新の設定に最も近いプロファイルを使用するように切り替わります。

例えば、ストリームに次のプロファイルがあるとします。

* 1:300000
* 2:700000
* 3:1500000
* 4:2400000
* 5:4000000

300000 ～ 200000の範囲を指定した場合、TVSDKはプロファイル1、2、3のみを考慮します。 これにより、アプリケーションをwi-fiから3Gへの切り替えや、スマートフォン、タブレット、デスクトップコンピューターなどの様々なデバイスへの切り替えなど、様々なネットワーク条件に合わせて調整できます。

ABR制御パラメーターを設定するには、`ABRControlParameter`クラスにパラメーターを設定します。
