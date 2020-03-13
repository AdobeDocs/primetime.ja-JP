---
description: TVSDKは、様々なビットレートを持つ複数のプロファイルを持つビデオを再生し、それらを切り替えて、使用可能な帯域幅に基づいて複数の品質レベルを提供できます。
seo-description: TVSDKは、様々なビットレートを持つ複数のプロファイルを持つビデオを再生し、それらを切り替えて、使用可能な帯域幅に基づいて複数の品質レベルを提供できます。
seo-title: マルチビットレート
title: マルチビットレート
uuid: 46eac41e-0b2a-42e3-8a88-54ad9fe34212
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# マルチビットレート {#multiple-bit-rates}

TVSDKは、様々なビットレートを持つ複数のプロファイルを持つビデオを再生し、それらを切り替えて、使用可能な帯域幅に基づいて複数の品質レベルを提供できます。

初期、最小、最大のビットレートと、マルチビットレート(MBR)ストリームに対する可変ビットレート(ABR)切り替えポリシーを設定できます。 TVSDKは、指定した設定内で最高の再生エクスペリエンスを提供するビットレートに自動的に切り替えます。

参照の実装は、 [IPlaybackConfigで次のABRパラメーターを設定します](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html)。

| パラメータ | 説明 |
|--- |--- |
| 初期ビットレート： getABRInitialBitRate | 最初のセグメントの目的の再生ビットレート（ビット/秒）。 再生が開始すると、最初のセグメントに最も近い（初期ビットレート以上の）プロファイルが使用されます。  最小ビットレートが定義され、初期ビットレートが最小ビットレートより低い場合、TVSDKは最小ビットレートよりも低いビットレートのプロファイルを選択します。 同様に、初期レートが最大レートを超える場合、TVSDKは最大レートを下回る最も高いレートを選択します。 初期ビットレートが0または未定義の場合、初期ビットレートはABRポリシーによって決定されます。  バイト/秒プロファイルを表す整数値を返します。 |
| 最小ビットレート： getABRMinBitRate | ABRが切り替え可能な最小許容ビットレートです。 ABR切り替えでは、これより低いビットレートのプロファイルは無視されます。 ビット/秒プロファイルを表す整数値を返します。 |
| 最大ビットレート： getABRMaxBitRate | ABRが切り替え可能な最大許容ビットレートです。 ABR切り替えでは、これより大きいビットレートのプロファイルは無視されます。 ビット/秒プロファイルを表す整数値を返します。 |
| ABR切り替えポリシー： getABRPolicy | 可能な場合、再生は徐々に最も高いビットレートのプロファイルに切り替わります。 ABR切り替えのポリシーを設定できます。これにより、TVSDKがプロファイルを切り替える速度が決まります。 デフォルトは「モデレート」です。 <ul><li>*保守的*:帯域幅が現在のビットレートより50%高い場合に、次に高いビットレートを持つプロファイルに切り替えます。 </li><li>*モデレート*:帯域幅が現在のビットレートより20%高い場合に、次に高いビットレートプロファイルに切り替えます。</li><li>*積極的*:帯域幅が現在のビットレートよりも大きい場合に、最も高いビットレートプロファイルに即座に切り替えます。</li></ul><br/>初期ビットレートが0であるか、指定されていない場合、ポリシーが指定されていると、再生はConservativeの最も低いビットレートプロファイル、Moderateの使用可能なプロファイルの中央値のビットレートに最も近いプロファイル、Aggressiveの最も高いビットレートプロファイルで開始されます。<br/><br/>このポリシーは、最小および最大ビットレートが指定されている場合は、その制約の範囲内で機能します。  ABRControlParameters列挙から現在の設定を返します。 <ul><li>ABR_CONSERVATIVE</li><li>ABR_MODERATE </li><li>ABR_AGGRESSIVE</li></ul><br>ABRPolicyも参照して [ください](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/ABRControlParameters.ABRPolicy.html)。 |

>[!NOTE]
>
>* TVSDKは、制御パラメーターに厳密に従うよりも継続的な再生エクスペリエンスを優先するので、TVSDKのフェイルオーバーメカニズムがこれらの設定を上書きする可能性があります。
>* ビットレートが変更されると、TVSDKはでイベントをディス `onProfileChanged` パッチしま `PlaybackEventListener`す。


## 参照実装でのカスタムABRコントロールの有効化 {#section_72A6E7263E1441DD8D7E0690285515E6}

可変ビットレート(ABR)は、TVSDKでデフォルトで有効になっています。 カスタムABRコントロールを設定することで、Primetime Settingsユーザーインターフェイスを使用して、参照実装のデフォルトのTVSDK動作を上書きできます。

設定ユーザーインターフェイスを通じてカスタムABRを有効にするには：

* Primetime設定ダイアログを開きます。
* を選択しま **[!UICONTROL ABR controls]**&#x200B;す。

   ![](assets/abr-configuration.jpg)

* コントロールを [!UICONTROL Enable ON] タップして表示させま `OFF`す。

isABRControlEnabledが `PlaybackManager` true(ON)を返す場 [合にのみ、ABRパラメーターが設定されます](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html) 。 false(OFF)を返す場合、はデフォルトの `PlaybackManager` ABRコントロールを使用し、初期、最小および最大のビットレートがすべて0になり、ABRポリシーがになります `ABR_MODERATE`。

## 低ビットレートの設定 {#section_5451691CBBD24542AD54A474D222CD39}

一部の低ビットレート再生レートの場合、TVSDKは、デフォルトでオーディオ専用ストリームに切り替わり、再生がフリーズしたように表示されます。 プレーヤーがオーディオのみに切り替わる状況が発生しないように設定できます。

* IPlaybackConfigインターフ [ェイスの実装](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html) :

* getABRMinBitRateが [オーディオ専用のビットレート](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html#getABRMinBitRate()) （64000より大きい）よりも高いことを確認します。
* isABRControlEnabledがオンにな [っている](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html#isABRControlEnabled()) ことを確認します。