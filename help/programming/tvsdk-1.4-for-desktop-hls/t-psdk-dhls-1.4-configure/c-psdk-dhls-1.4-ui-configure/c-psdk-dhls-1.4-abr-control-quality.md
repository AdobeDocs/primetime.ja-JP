---
description: HLSストリームとDASHストリームは、ビデオの同じ短いバーストに対して異なるビットレートエンコーディング（プロファイル）を提供します。 TVSDKは、使用可能な帯域幅に基づいて、各バーストの品質レベルを選択できます。
seo-description: HLSストリームとDASHストリームは、ビデオの同じ短いバーストに対して異なるビットレートエンコーディング（プロファイル）を提供します。 TVSDKは、使用可能な帯域幅に基づいて、各バーストの品質レベルを選択できます。
seo-title: ビデオ画質の可変ビットレート(ABR)
title: ビデオ画質の可変ビットレート(ABR)
uuid: e3d5ef90-067d-48e0-a025-081de931d842
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# ビデオ画質の可変ビットレート(ABR){#adaptive-bit-rates-abr-for-video-quality}

HLSストリームとDASHストリームは、ビデオの同じ短いバーストに対して異なるビットレートエンコーディング（プロファイル）を提供します。 TVSDKは、使用可能な帯域幅に基づいて、各バーストの品質レベルを選択できます。

TVSDKは、常にビットレートを監視し、現在のネットワーク接続に最適なビットレートでコンテンツが再生されることを確認します。

可変ビットレート(ABR)切り替えポリシーと、マルチビットレート(MBR)ストリームの初期ビットレート、最小ビットレートおよび最大ビットレートを設定できます。 TVSDKは、指定した設定で最高の再生エクスペリエンスを提供するビットレートに自動的に切り替えます。

<table id="table_AF838E082235406AA359BF1C1A77F85F"> 
 <tbody> 
  <tr> 
   <td colname="col01"> 初期ビットレート </td> 
   <td colname="col2"> <p>最初のセグメントの目的の再生ビットレート（ビット/秒）。 再生が開始すると、最初のセグメントに対して、初期ビットレート以上の最も近いプロファイルが使用されます。 </p> <p> 最小ビットレートが定義され、初期ビットレートが最小ビットレートより低い場合、TVSDKは最小ビットレートよりも低いビットレートのプロファイルを選択します。 初期レートが最大レートを超える場合、TVSDKは最大レートを下回る最も高いレートを選択します。 </p> <p>初期ビットレートが0または未定義の場合、初期ビットレートはABRポリシーによって決定されます。 </p> <p> <span class="apiname"> ABRInitialBitRateは、1 </span> 秒あたりのバイト数を表す整数値を返します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> 最小ビットレート </td> 
   <td colname="col2"> <p>ABRが切り替え可能な最小許容ビットレートです。 ABR切り替えでは、このビットレートより低いビットレートのプロファイルは無視されます。 </p> <p> <span class="apiname"> ABRMinBitRateは、 </span> ビット/秒プロファイルを表す整数値を返します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> 最大ビットレート </td> 
   <td colname="col2"> <p>ABRが切り替え可能な最大許容ビットレートです。 ABR切り替えでは、このビットレートより大きいビットレートのプロファイルは無視されます。 </p> <p> <span class="apiname"> ABRMaxBitRateは、 </span> ビット/秒プロファイルを表す整数値を返します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> ABR切り替えポリシー </td> 
   <td colname="col2"> 可能な場合、再生は徐々に最も高いビットレートのプロファイルに切り替わります。 ABR切り替えのポリシーを設定できます。このポリシーにより、TVSDKがプロファイルを切り替える速度が決まります。 デフォルトは <span class="codeph"> MODERATE_POLICYです </span>。 <p>TVSDKが高いビットレートに切り替えることを決定した場合、プレイヤーは現在のABRポリシーに基づいて、切り替える理想的なビットレートプロファイルを選択します。 
     <ul id="ul_058D0FFC944C476A83BB9E756B95DEBD"> 
      <li id="li_C690A12DC34C4754B01C2D0616FB6A0A"> <span class="codeph"> CONSERVATIVE_POLICY </span>:帯域幅が現在のビットレートより50%高い場合に、次に高いビットレートを持つプロファイルに切り替えます。 </li> 
      <li id="li_FF5BDB099B554940AC296938C7A12B81"> <span class="codeph"> MODERATE_POLICY </span>:帯域幅が現在のビットレートより20%高い場合に、次に高いビットレートプロファイルに切り替えます。 </li> 
      <li id="li_E602508429864C279BF78360E95718A6"> <span class="codeph"> AGGRESSIVE_POLICY </span>:帯域幅が現在のビットレートよりも大きい場合に、最も高いビットレートのプロファイルに即座に切り替えます。 </li> 
     </ul> </p> <p>初期ビットレートが0であるか、指定されていないがポリシーが指定されている場合、再生は保守的には最も低いビットレートプロファイル、モデレートでは使用可能なプロファイルの中央値のビットレートに最も近いプロファイル、積極的には最も高いビットレートプロファイルで開始されます。 </p> <p>このポリシーは、最小および最大ビットレートが指定されている場合は、その制約に従って機能します。 </p> <p> <span class="codeph"> ABRPolicyは、 </span> ABRControlParameters列挙から現在の設定 <span class="codeph"> を返 </span> します。CONSERVATIVE_POLICY、MODERATE_POLICYまたはAGGRESSIVE_POLICY。 </p> </td> 
  </tr> 
 </tbody> 
</table>

次の情報に注意してください。

* TVSDKは、制御パラメーターに厳密に準拠するよりも継続的な再生エクスペリエンスを優先するので、TVSDKのフェイルオーバーメカニズムが設定を上書きする可能性があります。
* ビットレートが変更されると、TVSDKはディスパッチしま `ProfileEvent.PROFILE_CHANGED`す。
* ABR設定はいつでも変更でき、プレイヤーは最新の設定に最も近いプロファイルを使用するように切り替わります。

例えば、ストリームに次のプロファイルがある場合、

* 1: 300000
* 2: 700000
* 3: 1500000
* 4: 2400000
* 5: 4000000

300000 ～ 200000の範囲を指定した場合、TVSDKはプロファイル1、2、3のみを考慮します。 これにより、アプリケーションは、Wi-Fiから3Gへの切り替えなど、様々なネットワーク条件や、スマートフォン、タブレット、デスクトップコンピューターなどの様々なデバイスに調整できます。

ABR制御パラメーターを設定するには、次のいずれかの操作を行います。

* ヘルパーク `ABRControlParameterBuilder` ラスを使用して、パラメーターのサブセットを設定します(背後で `ABRControlParameter` 動作)。

* クラスのパラメーターを設定 `ABRControlParameter` します。

## ABRControlParametersBuilderを使用したアダプティブビットレートの設定 {#section_3DDE397A7CE445E1832EBAA46CE5C069}

ヘルパークラ `ABRControlParametersBuilder` スの使用は、ABRパラメーターを設定する最も簡単で効率的な方法です。

* コンスト `ABRControlParametersBuilder` ラクターは、すべてのABRパラメーターを基になるオブジェクトのデフォルト値に設定 `ABRControlParameters` します。

* 同じインスタンスへの参照を維持している限り、個々のABRパラメーターを実行時にリセットで `ABRControlParametersBuilder` きます。

このクラスには、ヘルパーメソッドも `toABRControlParameters()` 含まれます。 このメソッドを使用して、のインスタンスを取得し、 `ABRControlParameters` プロパティに設定し `mediaPlayer.ABRControlParameters` ます。 これにより、設定がプレイヤーで有効になります。

1. ヘルパークラ `ABRControlParametersBuilder` スをインスタンス化し、Media Playerでパラメーターを設定します。

   >[!NOTE]
   >
   >例えば、次の例では、すべてのパラメーターをデフォルト値に初期化し、ポリシーのみをconservativeに設定し、最大ビットレートを1000000に制限しています。   >
   >
   >
   ```>
   >var abrBuilder:ABRControlParametersBuilder =  
   >   new ABRControlParametersBuilder(); 
   >abrBuilder.policy = ABRControlParameters.CONSERVATIVE_POLICY; 
   >abrBuilder.maxBitRate = 1000000; 
   >mediaPlayer.abrControlParameters =  
   >   abrBuilder.toABRControlParameters();
   >```   >
   >



1. 個々のABRパラメーターを実行時に変更します。

   残りのパラメータをそのままにして、個々のパラメータを変更するには：

   ```
   // If later you want to reset the max bit rate to 2000000 
   abrBuilder.maxBitRate = 2000000; 
   mediaPlayer.abrControlParameters =  
     abrBuilder.toABRControlParameters();
   ```

   以前の設定を保持するには、手順1で作成したのと同じインスタンスへの参 `ABRControlParametersBuilder` 照を維持する必要があります。

## ABRControlParametersを使用した可変ビットレートの設定 {#section_02161FD0A73F40ED9CAE17F9AF850483}

ABR制御値はでのみ設定できますが、 `ABRControlParameters`いつでも新しい値を作成することができます。

このABRパラメーターの設定機能は、クラスが存在する前にサポートされていま `ABRControlParametersBuilder` したが、この機能は構築時にABRパラメーターを設定する場合にも有効です。 ただし、構築後に個々のパラメータを変更するには、クラスを使用する必要があ `ABRControlParametersBuilder` ります。

次の条件が適用されま `ABRControlParameters`す。

* 構築時に、すべてのパラメーターの値を指定する必要があります。
* 構築後に個々の値を変更することはできません。
* 指定したパラメーターが許容範囲外の場合は、がスロー `ArgumentError` されます。

1. 初期、最小、最大のビットレートを決定します。
1. ABRポリシーの決定：

   * `CONSERVATIVE_POLICY`
   * `MODERATE_POLICY`
   * `AGGRESSIVE_POLICY`

1. ABRパラメーターの値をコンストラク `ABRControlParameters` ターに設定し、Media Playerに割り当てます。

   ```
   mediaPlayer.abrControlParameters = new ABRControlParameters( 
       ABRControlParameters.CONSERVATIVE_POLICY, 
       0, // Initial bit rate 
       0, // Minimum bit rate 
       1000000 // Maximum bit rate 
   );
   ```

