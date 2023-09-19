---
description: HLS ストリームと DASH ストリームでは、同じビデオの短いバーストに対して異なるビットレートエンコーディング（プロファイル）を提供します。 TVSDK は、使用可能な帯域幅に基づいて、各バーストの品質レベルを選択できます。
title: ビデオ画質の可変ビットレート (ABR)
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '973'
ht-degree: 0%

---

# ビデオ画質の可変ビットレート (ABR){#adaptive-bit-rates-abr-for-video-quality}

HLS ストリームと DASH ストリームでは、同じビデオの短いバーストに対して異なるビットレートエンコーディング（プロファイル）を提供します。 TVSDK は、使用可能な帯域幅に基づいて、各バーストの品質レベルを選択できます。

TVSDK は、常にビットレートを監視し、現在のネットワーク接続に最適なビットレートでコンテンツが再生されるようにします。

可変ビットレート (ABR) 切り替えポリシーと、マルチビットレート (MBR) ストリームの初期ビットレート、最小ビットレート、最大ビットレートを設定できます。 TVSDK は、指定した設定で最適な再生エクスペリエンスを提供するビットレートに自動的に切り替えます。

<table id="table_AF838E082235406AA359BF1C1A77F85F"> 
 <tbody> 
  <tr> 
   <td colname="col01"> 初期ビットレート </td> 
   <td colname="col2"> <p>最初のセグメントの目的の再生ビットレート (bps)。 再生が開始すると、最初のセグメントには、初期ビットレート以上の最も近いプロファイルが使用されます。 </p> <p> 最小ビットレートが定義され、初期ビットレートが最小ビットレートより低い場合、 TVSDK は最小ビットレートよりも低いビットレートを持つプロファイルを選択します。 初期レートが最大レートを超える場合、 TVSDK は最大レートを下回る最も高いレートを選択します。 </p> <p>初期ビットレートがゼロまたは未定義の場合、初期ビットレートは ABR ポリシーによって決定されます。 </p> <p> <span class="apiname"> ABRInitialBitRate </span> 1 秒あたりのバイト数を表す integer 値を返します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> 最小ビットレート </td> 
   <td colname="col2"> <p>ABR が切り替え可能な最も低いビットレートです。 ABR 切り替えでは、このビットレートより低いビットレートを持つプロファイルは無視されます。 </p> <p> <span class="apiname"> ABRMinBitRate </span> bps プロファイルを表す integer 値を返します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> 最大ビットレート </td> 
   <td colname="col2"> <p>ABR が切り替え可能な最大許容ビットレートです。 ABR 切り替えでは、このビットレートよりも高いビットレートを持つプロファイルは無視されます。 </p> <p> <span class="apiname"> ABRMaxBitRate </span> bps プロファイルを表す integer 値を返します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> ABR 切り替えポリシー </td> 
   <td colname="col2"> 可能な場合は、再生が徐々に最も高いビットレートのプロファイルに切り替わります。 ABR 切り替えのポリシーを設定できます。このポリシーは、TVSDK がプロファイルを切り替える速度を決定します。 デフォルトはです。 <span class="codeph"> MODERATE_POLICY </span>. <p>TVSDK がより高いビットレートに切り替えると決定した場合、プレーヤーは現在の ABR ポリシーに基づいて、切り替える理想的なビットレートプロファイルを選択します。 
     <ul id="ul_058D0FFC944C476A83BB9E756B95DEBD"> 
      <li id="li_C690A12DC34C4754B01C2D0616FB6A0A"> <span class="codeph"> CONSERVATIVE_POLICY </span>：帯域幅が現在のビットレートより 50%高い場合、次に高いビットレートを持つプロファイルに切り替えます。 </li> 
      <li id="li_FF5BDB099B554940AC296938C7A12B81"> <span class="codeph"> MODERATE_POLICY </span>：帯域幅が現在のビットレートより 20%高い場合、次に高いビットレートプロファイルに切り替えます。 </li> 
      <li id="li_E602508429864C279BF78360E95718A6"> <span class="codeph"> AGGRESSIVE_POLICY </span>：帯域幅が現在のビットレートよりも高い場合、最も高いビットレートのプロファイルに即座に切り替えます。 </li> 
     </ul> </p> <p>初期ビットレートが 0 または指定されていない場合、ポリシーが指定されている場合、保守的な場合は最も低いビットレートプロファイル、中程度の場合は中央値ビットレートに最も近いプロファイル、攻撃的な場合は最も高いビットレートプロファイルで再生が開始されます。 </p> <p>このポリシーは、最小ビットレートと最大ビットレートの制約で機能します（これらのレートが指定されている場合）。 </p> <p> <span class="codeph"> ABRPolicy </span> 現在の設定を <span class="codeph"> ABRControlParameters </span> enum: CONSERVATIVE_POLICY、MODERATE_POLICY、AGGRESSIVE_POLICY のいずれかです。 </p> </td> 
  </tr> 
 </tbody> 
</table>

次の情報に留意してください。

* TVSDK は、制御パラメーターに厳密に準拠しているよりも連続再生を優先するので、 TVSDK のフェイルオーバーメカニズムが設定を上書きする場合があります。
* ビットレートが変更されると、 TVSDK は `ProfileEvent.PROFILE_CHANGED`.
* ABR 設定はいつでも変更でき、プレーヤーは最新の設定に最も近いプロファイルを使用するように切り替えます。

例えば、ストリームに次のプロファイルが含まれている場合、

* 1: 300000
* 2: 700000
* 3: 1500000
* 4: 2400000
* 5: 4000000

300000 ～ 2000000の範囲を指定した場合、 TVSDK は 1、2、3 のプロファイルのみを考慮します。 これにより、アプリケーションは、Wi-Fi から 3G への切り替えや、電話、タブレット、デスクトップコンピューターなどの様々なデバイスへの切り替えなど、様々なネットワーク条件に合わせて調整できます。

ABR 制御パラメーターを設定するには、次のいずれかの操作を行います。

* 以下を使用します。 `ABRControlParameterBuilder` パラメーターのサブセットを設定するヘルパークラス ( `ABRControlParameter` 舞台裏

* 次に示すように、 `ABRControlParameter` クラス。

## ABRControlParametersBuilder を使用したアダプティブビットレートの設定 {#section_3DDE397A7CE445E1832EBAA46CE5C069}

の使用 `ABRControlParametersBuilder` helper クラスは、ABR パラメーターを設定する最も簡単で効率的な方法です。

* The `ABRControlParametersBuilder` コンストラクタは、すべての ABR パラメータを基になる `ABRControlParameters` オブジェクト。

* 同じ `ABRControlParametersBuilder` インスタンス。

このクラスには、 `toABRControlParameters()` ヘルパーメソッド。 このメソッドを使用して、のインスタンスを取得します。 `ABRControlParameters` そして、それを `mediaPlayer.ABRControlParameters` プロパティ。 これにより、設定がプレーヤーで有効になります。

1. をインスタンス化します。 `ABRControlParametersBuilder` ヘルパークラスを作成し、Media Player でパラメーターを設定します。

   >[!NOTE]
   >
   >例えば、次の例では、すべてのパラメーターをデフォルト値に初期化し、ポリシーを conservative に設定し、最大ビットレートを1000000に制限します。
   >
   >```
   >var abrBuilder:ABRControlParametersBuilder =  
   >   new ABRControlParametersBuilder(); 
   >abrBuilder.policy = ABRControlParameters.CONSERVATIVE_POLICY; 
   >abrBuilder.maxBitRate = 1000000; 
   >mediaPlayer.abrControlParameters =  
   >   abrBuilder.toABRControlParameters();
   >```
   >

1. 個々の ABR パラメーターを実行時に変更します。

   残りのパラメータをそのままにして、個々のパラメータを変更するには、次の手順に従います。

   ```
   // If later you want to reset the max bit rate to 2000000 
   abrBuilder.maxBitRate = 2000000; 
   mediaPlayer.abrControlParameters =  
     abrBuilder.toABRControlParameters();
   ```

   以前の設定を保持するには、同じ `ABRControlParametersBuilder` 手順 1 で作成したインスタンス。

## ABRControlParameters を使用したアダプティブビットレートの設定 {#section_02161FD0A73F40ED9CAE17F9AF850483}

ABR 制御値を設定できるのは、 `ABRControlParameters`新しいをいつでも作成できます。

ABR パラメーターを設定するこの機能は、 `ABRControlParametersBuilder` クラスではありますが、この機能は、構築時に ABR パラメータを設定する際に引き続き有効です。 ただし、構築後に個々のパラメータを変更するには、 `ABRControlParametersBuilder` クラス。

次の条件が適用されます。 `ABRControlParameters`:

* 構築時にすべてのパラメータの値を指定する必要があります。
* 構築後に個々の値を変更することはできません。
* 指定したパラメーターが許容範囲外の場合、 `ArgumentError` がスローされます。

1. 初期、最小、最大のビットレートを決定します。
1. ABR ポリシーを決定します。

   * `CONSERVATIVE_POLICY`
   * `MODERATE_POLICY`
   * `AGGRESSIVE_POLICY`

1. ABR パラメーター値を `ABRControlParameters` コンストラクターに割り当てて、Media Player に割り当てます。

   ```
   mediaPlayer.abrControlParameters = new ABRControlParameters( 
       ABRControlParameters.CONSERVATIVE_POLICY, 
       0, // Initial bit rate 
       0, // Minimum bit rate 
       1000000 // Maximum bit rate 
   );
   ```
