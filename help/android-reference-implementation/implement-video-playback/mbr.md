---
description: TVSDKは、様々なビットレートを持つ複数のプロファイルを持つビデオを再生でき、ビットレートを切り替えて、使用可能な帯域幅に基づいて複数の品質レベルを提供できます。
seo-description: TVSDKは、様々なビットレートを持つ複数のプロファイルを持つビデオを再生でき、ビットレートを切り替えて、使用可能な帯域幅に基づいて複数の品質レベルを提供できます。
seo-title: マルチビットレート
title: マルチビットレート
uuid: 46eac41e-0b2a-42e3-8a88-54ad9fe34212
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 0%

---


# マルチビットレート{#multiple-bit-rates}

TVSDKは、様々なビットレートを持つ複数のプロファイルを持つビデオを再生でき、ビットレートを切り替えて、使用可能な帯域幅に基づいて複数の品質レベルを提供できます。

イニシャル、最小および最大ビットレートと、マルチビットレート(MBR)ストリーム用の可変ビットレート(ABR)切り替えポリシーを設定できます。 TVSDKは、指定された設定内で最高の再生エクスペリエンスを提供するビットレートに自動的に切り替えます。

参照の実装は、[IPlaybackConfig](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html)に以下のABRパラメーターを設定します。

| パラメータ | 説明 |
|--- |--- |
| 初期ビットレート： getABRInitialBitRate | 最初のセグメントに対する目的の再生ビットレート（ビット/秒）。 再生開始の場合、最初のセグメントには、初期ビットレートと同じかそれ以上の最も近いプロファイルが使用されます。  最小ビットレートが定義され、初期ビットレートが最小ビットレートより小さい場合、最小ビットレートを超える最小ビットレートを持つプロファイルがTVSDKによって選択されます。 同様に、初期レートが最大レートを超える場合は、最大レートを下回る最も高いレートがTVSDKによって選択されます。 初期ビットレートが0または未定義の場合、初期ビットレートはABRポリシーによって決定されます。  1秒あたりのバイトプロファイルを表す整数値を返します。 |
| 最小ビットレート： getABRMinBitRate | ABRで切り替え可能な最小許容ビットレートです。 ABR切り替えでは、これより低いビットレートのプロファイルは無視されます。 ビット/秒プロファイルを表す整数値を返します。 |
| 最大ビットレート： getABRMaxBitRate | ABRで切り替え可能な最大許容ビットレートです。 ABR切り替えでは、これより大きいビットレートのプロファイルは無視されます。 ビット/秒プロファイルを表す整数値を返します。 |
| ABR切り替えポリシー： getABRPolicy | 可能な場合は、再生時のビットレートが徐々に最も高いプロファイルに切り替わります。 ABR切り替えポリシーを設定できます。これにより、TVSDKがプロファイルを切り替える速度が決まります。 デフォルト値はModerateです。 <ul><li>*保守的*:帯域幅が現在のビットレートより50 %以上大きい場合は、次に大きいビットレートを持つプロファイルに切り替えます。 </li><li>*モデレート*:帯域幅が現在のビットレートより20%高い場合に、次に高いビットレートプロファイルに切り替えます。</li><li>*アグレッシブ*:帯域幅が現在のビットレートよりも大きい場合、高いビットレートプロファイルに即座に切り替えます。</li></ul><br/>初期ビットレートが0であるか、指定されていない場合にポリシーを指定すると、Conservative（保守）のビットレートプロファイルが最も低い再生開始、Moderate（中央値）のプロファイルのビットレートに最も近いプロファイル、Aggressiveのビットレートプロファイルが最も高い再生が表示されます。<br/><br/>このポリシーは、最小および最大ビットレートが指定されている場合は、それらの制限内で機能します。ABRControlParameters列挙から現在の設定を返します。 <ul><li>ABR_CONSERVATIVE</li><li>ABR_MODERATE </li><li>ABR_AGGRESSIVE</li></ul><br>ABRPolicyも参照して [ください](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/ABRControlParameters.ABRPolicy.html)。 |

>[!NOTE]
>
>* TVSDKは、制御パラメーターに厳密に従うよりも継続的な再生エクスペリエンスのほうが優先されるので、TVSDKのフェイルオーバーメカニズムがこれらの設定をオーバーライドする可能性があります。
>* ビットレートが変更されると、TVSDKは`onProfileChanged`イベントを`PlaybackEventListener`にディスパッチします。


## 参照実装でのカスタムABRコントロールの有効化{#section_72A6E7263E1441DD8D7E0690285515E6}

可変ビットレート(ABR)は、TVSDKでデフォルトで有効になっています。 カスタムABRコントロールを設定すると、Primetime Settingsユーザーインターフェイスを使用して、参照実装のデフォルトのTVSDK動作を上書きできます。

設定ユーザーインターフェイスを通してカスタムABRを有効にするには：

* Primetime設定ダイアログを開きます。
* **[!UICONTROL ABR controls]**&#x200B;を選択します。

   ![](assets/abr-configuration.jpg)

* [!UICONTROL Enable ON]コントロールをタップして`OFF`を表示します。

`PlaybackManager`は、[isABRControlEnabled](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html)がtrue(ON)を返した場合にのみABRパラメーターを設定します。 false(OFF)を返す場合、`PlaybackManager`はデフォルトのABR制御を使用し、初期、最小、最大の各ビットレートがすべて0になり、ABRポリシーは`ABR_MODERATE`になります。

## 低ビットレートに設定{#section_5451691CBBD24542AD54A474D222CD39}

一部の低ビットレート再生レートの場合、TVSDKは、デフォルトで、オーディオ専用ストリームに切り替わり、再生が停止したように表示されます。 プレーヤーがオーディオのみに切り替わる状況が発生しないように設定できます。

* [IPlaybackConfig](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html)インターフェイスを実装します。

* [getABRMinBitRate](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html#getABRMinBitRate())がオーディオ専用ビットレート（64000より大きい）よりも大きいことを確認します。
* [isABRControlEnabled](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html#isABRControlEnabled())がオンになっていることを確認します。