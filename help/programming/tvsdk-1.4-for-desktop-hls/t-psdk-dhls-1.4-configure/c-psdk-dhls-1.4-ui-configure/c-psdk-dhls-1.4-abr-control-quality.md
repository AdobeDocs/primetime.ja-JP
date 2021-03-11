---
description: HLSストリームとDASHストリームは、同じビデオの短いバーストを目的として異なるビットレートエンコーディング(プロファイル)を提供します。 TVSDKは、使用可能な帯域幅に基づいて、各バーストの品質レベルを選択できます。
title: ビデオ画質に関する可変ビットレート(ABR)
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '973'
ht-degree: 0%

---


# ビデオ画質の可変ビットレート(ABR){#adaptive-bit-rates-abr-for-video-quality}

HLSストリームとDASHストリームは、同じビデオの短いバーストを目的として異なるビットレートエンコーディング(プロファイル)を提供します。 TVSDKは、使用可能な帯域幅に基づいて、各バーストの品質レベルを選択できます。

TVSDKは、常にビットレートを監視し、現在のネットワーク接続に最適なビットレートでコンテンツが再生されるようにします。

可変ビットレート(ABR)切り替えポリシーと、マルチビットレート(MBR)ストリームの初期、最小、最大ビットレートを設定できます。 TVSDKは、指定された設定で最高の再生エクスペリエンスを提供するビットレートに自動的に切り替えます。

<table id="table_AF838E082235406AA359BF1C1A77F85F"> 
 <tbody> 
  <tr> 
   <td colname="col01"> 初期ビットレート </td> 
   <td colname="col2"> <p>最初のセグメントに対する目的の再生ビットレート（ビット/秒）。 再生開始の場合、最初のセグメントには、初期ビットレートと等しいかそれ以上の最も近いプロファイルが使用されます。 </p> <p> 最小ビットレートが定義され、初期ビットレートが最小ビットレートより低い場合、最小ビットレートを超える最小ビットレートを持つプロファイルがTVSDKによって選択されます。 初期レートが最大レートを超える場合、TVSDKは最大レートを下回る最も高いレートを選択します。 </p> <p>初期ビットレートが0または未定義の場合、初期ビットレートはABRポリシーによって決定されます。 </p> <p> <span class="apiname"> ABRInitialBitRateは、1秒あたりのバイトプロファイルを表す整数値を </span> 返します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> 最小ビットレート </td> 
   <td colname="col2"> <p>ABRで切り替え可能な最小許容ビットレートです。 ABR切り替えでは、このビットレートより低いビットレートのプロファイルは無視されます。 </p> <p> <span class="apiname"> ABRMinBitRateは、1秒あたりのビット数プロファイルを表す整数値を </span> 返します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> 最大ビットレート </td> 
   <td colname="col2"> <p>ABRで切り替え可能な最大許容ビットレートです。 ABR切り替えでは、このビットレートよりも大きいビットレートのプロファイルは無視されます。 </p> <p> <span class="apiname"> ABRMaxBitRateは、1秒あたりのビット数プロファイルを表す整数値を </span> 返します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> ABR切り替えポリシー </td> 
   <td colname="col2"> 可能な場合は、再生時のビットレートが徐々に最も高いプロファイルに切り替わります。 ABR切り替えポリシーを設定できます。これにより、TVSDKがプロファイルを切り替える速度が決まります。 デフォルトは<span class="codeph"> MODERATE_POLICY </span>です。 <p>TVSDKがより高いビットレートに切り替えると判断した場合、プレイヤーは、現在のABRポリシーに基づいて、最適なビットレートプロファイルを選択して切り替えます。 
     <ul id="ul_058D0FFC944C476A83BB9E756B95DEBD"> 
      <li id="li_C690A12DC34C4754B01C2D0616FB6A0A"> <span class="codeph"> CONSERVATIVE_POLICY  </span>:帯域幅が現在のビットレートより50 %以上大きい場合は、次に大きいビットレートを持つプロファイルに切り替えます。 </li> 
      <li id="li_FF5BDB099B554940AC296938C7A12B81"> <span class="codeph"> MODERATE_POLICY  </span>:帯域幅が現在のビットレートより20%高い場合に、次に高いビットレートプロファイルに切り替えます。 </li> 
      <li id="li_E602508429864C279BF78360E95718A6"> <span class="codeph"> AGGRESSIVE_POLICY  </span>:帯域幅が現在のビットレートよりも大きい場合は、高いビットレートプロファイルに即座に切り替えます。 </li> 
     </ul> </p> <p>初期ビットレートが0であるか、指定されていないがポリシーが指定されている場合、保守的なビットレートプロファイルが最も低い再生開始、モデレートの使用可能なプロファイルの中央値ビットレートに最も近いプロファイル、積極的なビットレートプロファイルが最も高い再生。 </p> <p>このポリシーは、最小および最大ビットレートが指定されている場合は、その制約に従って機能します。 </p> <p> <span class="codeph"> ABRPolicy </span> は、ABRControlParameters  <span class="codeph">  </span> enumから現在の設定を返します。CONSERVATIVE_POLICY、MODERATE_POLICYまたはAGGRESSIVE_POLICYです。 </p> </td> 
  </tr> 
 </tbody> 
</table>

次の情報に注意してください。

* TVSDKは、制御パラメーターに厳密に従うよりも継続的な再生エクスペリエンスのほうが優先されるので、TVSDKのフェイルオーバーメカニズムによって設定が上書きされる場合があります。
* ビットレートが変更されると、TVSDKは`ProfileEvent.PROFILE_CHANGED`をディスパッチします。
* ABR設定はいつでも変更でき、プレイヤーは最新の設定に最も近いプロファイルを使用するように切り替わります。

例えば、ストリームに次のプロファイルがあるとします。

* 1:300000
* 2:700000
* 3:1500000
* 4:2400000
* 5:4000000

300000 ～ 200000の範囲を指定した場合、TVSDKはプロファイル1、2、3のみを考慮します。 これにより、アプリケーションをwi-fiから3Gへの切り替えや、スマートフォン、タブレット、デスクトップコンピューターなどの様々なデバイスへの切り替えなど、様々なネットワーク条件に合わせて調整できます。

ABR制御パラメーターを設定するには、次のいずれかを実行します。

* `ABRControlParameterBuilder`ヘルパークラスを使用して、パラメーターのサブセットを設定します（背後で`ABRControlParameter`を操作します）

* `ABRControlParameter`クラスにパラメーターを設定します。

## ABRControlParametersBuilder {#section_3DDE397A7CE445E1832EBAA46CE5C069}を使用して可変ビットレートを設定

`ABRControlParametersBuilder`ヘルパークラスの使用は、ABRパラメーターを設定する最も簡単で効率的な方法です。

* `ABRControlParametersBuilder`コンストラクターは、すべてのABRパラメーターを基になる`ABRControlParameters`オブジェクトのデフォルト値に設定します。

* 同じ`ABRControlParametersBuilder`インスタンスへの参照を維持している限り、個々のABRパラメーターを実行時にリセットできます。

このクラスには、`toABRControlParameters()`ヘルパーメソッドも含まれます。 `ABRControlParameters`のインスタンスを取得し、`mediaPlayer.ABRControlParameters`プロパティに設定するには、このメソッドを使用します。 これにより、設定がプレイヤーで有効になります。

1. `ABRControlParametersBuilder`ヘルパークラスをインスタンス化し、パラメーターをMedia Playerに設定します。

   >[!NOTE]
   >
   >例えば、以下の例では、すべてのパラメーターをデフォルト値に初期化し、ポリシーのみをconservativeに設定し、最大ビットレートを100000に制限しています。
   >
   >
   ```
   >var abrBuilder:ABRControlParametersBuilder =  
   >   new ABRControlParametersBuilder(); 
   >abrBuilder.policy = ABRControlParameters.CONSERVATIVE_POLICY; 
   >abrBuilder.maxBitRate = 1000000; 
   >mediaPlayer.abrControlParameters =  
   >   abrBuilder.toABRControlParameters();
   >```

1. 個々のABRパラメーターを実行時に変更します。

   残りのパラメーターをそのままにして、個々のパラメーターを変更するには：

   ```
   // If later you want to reset the max bit rate to 2000000 
   abrBuilder.maxBitRate = 2000000; 
   mediaPlayer.abrControlParameters =  
     abrBuilder.toABRControlParameters();
   ```

   以前の設定を維持するには、手順1で作成したのと同じ`ABRControlParametersBuilder`インスタンスへの参照を維持する必要があります。

## ABRControlParameters {#section_02161FD0A73F40ED9CAE17F9AF850483}を使用して可変ビットレートを設定

ABR制御値は`ABRControlParameters`でのみ設定できますが、新しい値をいつでも作成できます。

このABRパラメーターの設定機能は、`ABRControlParametersBuilder`クラスが存在する前にサポートされていましたが、この機能は、構築時にABRパラメーターを設定する場合にも有効です。 ただし、構築後に個々のパラメーターを変更するには、`ABRControlParametersBuilder`クラスを使用する必要があります。

`ABRControlParameters`には次の条件が適用されます。

* 構築時に、すべてのパラメーターに値を指定する必要があります。
* 構築後に個々の値を変更することはできません。
* 指定したパラメーターが許容範囲外の場合は、`ArgumentError`がスローされます。

1. 初期、最小および最大ビットレートを決定します。
1. ABRポリシーの決定：

   * `CONSERVATIVE_POLICY`
   * `MODERATE_POLICY`
   * `AGGRESSIVE_POLICY`

1. ABRパラメーターの値を`ABRControlParameters`コンストラクターに設定し、それらをメディアプレイヤーに割り当てます。

   ```
   mediaPlayer.abrControlParameters = new ABRControlParameters( 
       ABRControlParameters.CONSERVATIVE_POLICY, 
       0, // Initial bit rate 
       0, // Minimum bit rate 
       1000000 // Maximum bit rate 
   );
   ```

