---
description: HLS ストリームと DASH ストリームでは、同じビデオの短いバーストに対して異なるビットレートエンコーディング（プロファイル）を提供します。 TVSDK は、使用可能な帯域幅に基づいて、各バーストの品質レベルを選択できます。
title: ビデオ画質の可変ビットレート (ABR)
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 0%

---

# ビデオ画質の可変ビットレート (ABR) {#adaptive-bit-rates-abr-for-video-quality}

HLS ストリームと DASH ストリームでは、同じビデオの短いバーストに対して異なるビットレートエンコーディング（プロファイル）を提供します。 TVSDK は、使用可能な帯域幅に基づいて、各バーストの品質レベルを選択できます。

TVSDK は、常にビットレートを監視し、現在のネットワーク接続に最適なビットレートでコンテンツが再生されるようにします。

可変ビットレート (ABR) 切り替えポリシーと、マルチビットレート (MBR) ストリームの初期ビットレート、最小ビットレート、最大ビットレートを設定できます。 TVSDK は、指定した設定で最適な再生エクスペリエンスを提供するビットレートに自動的に切り替えます。

<table id="table_AF838E082235406AA359BF1C1A77F85F"> 
 <tbody> 
  <tr> 
   <td colname="col01"> 初期ビットレート </td> 
   <td colname="col2"> <p>最初のセグメントの目的の再生ビットレート (bps)。 再生が開始すると、最初のセグメントには、初期ビットレート以上の最も近いプロファイルが使用されます。 </p> <p> 最小ビットレートが定義され、初期ビットレートが最小ビットレートより低い場合、 TVSDK は最小ビットレートよりも低いビットレートを持つプロファイルを選択します。 初期レートが最大レートを超える場合、 TVSDK は最大レートを下回る最も高いレートを選択します。 </p> <p>初期ビットレートがゼロまたは未定義の場合、初期ビットレートは ABR ポリシーによって決定されます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> 最小ビットレート </td> 
   <td colname="col2"> <p>ABR が切り替え可能な最も低いビットレートです。 ABR 切り替えでは、このビットレートより低いビットレートを持つプロファイルは無視されます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> 最大ビットレート </td> 
   <td colname="col2"> <p>ABR が切り替え可能な最大許容ビットレートです。 ABR 切り替えでは、このビットレートよりも高いビットレートを持つプロファイルは無視されます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

次の情報に留意してください。

* TVSDK は、ビットレートの切り替えからイベントをディスパッチしません。
* ABR 設定はいつでも変更でき、プレーヤーは最新の設定に最も近いプロファイルを使用するように切り替えます。

例えば、ストリームに次のプロファイルが含まれている場合、

* 1: 300000
* 2: 700000
* 3: 1500000
* 4: 2400000
* 5: 4000000

300000 ～ 2000000の範囲を指定した場合、 TVSDK は 1、2、3 のプロファイルのみを考慮します。 これにより、WiFi から 3G への切り替えや、電話、タブレット、デスクトップコンピューターなどの様々なデバイスへの切り替えなど、アプリケーションが様々なネットワーク条件に合わせて調整できます。

## アダプティブビットレートの設定 {#section_572FCE4CC28D4DF8BD9C461F00B3CA17}

TVSDK のアダプティブビットレートパラメーターを設定するには：

1. のインスタンスの設定 `PTABRControlParameters` 初期、最小、最大のビットレート設定を設定する。

   デフォルト値は、次のコードスニペットに表示されますが、アプリケーションは、これらの各パラメーターに任意の整数値を設定できます。

   >[!IMPORTANT]
   >
   >ビットレート設定を bps(bps) 単位で指定します。

   ```
   // ARC (add autorelease for non-ARC) 
   PTABRControlParameters *abrMetaData =  
       [[PTABRControlParameters alloc] init];  
   
   abrMetaData.initialBitRate = -1; 
   abrMetaData.minBitRate = 0; 
   abrMetaData.maxBitRate = INT_MAX;
   ```

1. を更新します。 `PTMediaPlayer` 設定済みのインスタンス `PTABRControlParameters` インスタンス。

   ```
   // assuming self.player is the PTMediaPlayer instance 
   self.player.abrControlParameters = abrMetaData;
   ```

次の点に注意してください。

* アプリケーションでは、 `abrControlParameters` プロパティ： `PTMediaPlayer` を設定する前に `PTMediaPlayerItem` 初期および最小ビットレート設定を有効にするインスタンス。

  コンテンツの再生が開始した後に新しいインスタンスを設定すると、最大ビットレート設定のみに影響します。

* 再生中に最大ビットレート設定を更新するには、新しい `PTABRControlParameters` インスタンスを作成し、プレーヤーインスタンスに設定します。
* 最大ビットレート設定は、iOS 8.0 以降での再生時にのみ更新できます。 以前のバージョンの場合、 `maxBitrate` コンテンツの再生が開始される前に設定された値を使用します。
