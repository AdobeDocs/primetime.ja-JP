---
description: TVSDK は、様々なビットレートを持つ複数のプロファイルを持つビデオを再生し、それらを切り替えて、使用可能な帯域幅に基づいて複数の品質レベルを提供できます。
title: 複数のビットレート
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '767'
ht-degree: 0%

---

# 複数のビットレート {#multiple-bit-rates}

TVSDK は、様々なビットレートを持つ複数のプロファイルを持つビデオを再生し、それらを切り替えて、使用可能な帯域幅に基づいて複数の品質レベルを提供できます。

初期、最小、最大のビットレートと、マルチビットレート (MBR) ストリームに対する可変ビットレート (ABR) 切り替えポリシーを設定できます。 TVSDK は、指定した設定内で最適な再生エクスペリエンスを提供するビットレートに自動的に切り替えます。

参照実装では、 [IPlaybackConfig](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html).

| パラメーター | 説明 |
|--- |--- |
| 初期ビットレート： getABRInitialBitRate | 最初のセグメントの目的の再生ビットレート (bps)。 再生が開始すると、最初のセグメントに最も近い（初期ビットレート以上の）プロファイルが使用されます。  最小ビットレートが定義され、初期ビットレートが最小ビットレートより小さい場合、 TVSDK は最小ビットレートよりも小さいビットレートを持つプロファイルを選択します。 同様に、初期レートが最大レートを超える場合、 TVSDK は最大レートを下回る最も高いレートを選択します。 初期ビットレートがゼロまたは未定義の場合、初期ビットレートは ABR ポリシーによって決定されます。  1 秒あたりのバイト数を表す整数値を返します。 |
| 最小ビットレート： getABRMinBitRate | ABR が切り替え可能な最も低いビットレートです。 ABR 切り替えでは、これよりも低いビットレートのプロファイルは無視されます。 bps プロファイルを表す整数値を返します。 |
| 最大ビットレート： getABRMaxBitRate | ABR が切り替え可能な最大許容ビットレートです。 ABR 切り替えでは、これよりも高いビットレートを持つプロファイルは無視されます。 bps プロファイルを表す整数値を返します。 |
| ABR 切り替えポリシー： getABRPolicy | 可能な場合は、再生が徐々に最も高いビットレートのプロファイルに切り替わります。 ABR 切り替えのポリシーを設定できます。このポリシーにより、 TVSDK がプロファイルを切り替える速度が決まります。 デフォルトは「モデレート」です。 <ul><li>*保守的*：帯域幅が現在のビットレートより 50%高い場合、次に高いビットレートを持つプロファイルに切り替えます。 </li><li>*モデレート*：帯域幅が現在のビットレートより 20%高い場合、次に高いビットレートプロファイルに切り替えます。</li><li>*アグレッシブ*：帯域幅が現在のビットレートよりも大きい場合に、最も高いビットレートのプロファイルに即座に切り替えます。</li></ul><br/>初期ビットレートがゼロまたは指定されていない場合、ポリシーが指定されている場合、再生は Conservative の最低ビットレートのプロファイル、Moderate の中央値のビットレートに最も近いプロファイル、Aggressive の最高ビットレートのプロファイルで開始されます。<br/><br/>ポリシーは、最小および最大ビットレートの制約内で機能します（指定されている場合）。  ABRControlParameters 列挙から現在の設定を返します。 <ul><li>ABR_CONSERVATIVE</li><li>ABR_MODERATE </li><li>ABR_AGGRESSIVE</li></ul><br>関連トピック [ABRPolicy](https://help.adobe.com/en_US/primetime/api/psdk/javadoc/com/adobe/mediacore/ABRControlParameters.ABRPolicy.html). |

>[!NOTE]
>
>* TVSDK は、制御パラメーターに厳密に従うよりも連続再生エクスペリエンスを優先するので、 TVSDK のフェイルオーバーメカニズムがこれらの設定を上書きする場合があります。
>* ビットレートが変更されると、 TVSDK は `onProfileChanged` イベント `PlaybackEventListener`.

## リファレンス実装でのカスタム ABR コントロールの有効化 {#section_72A6E7263E1441DD8D7E0690285515E6}

TVSDK では、デフォルトで可変ビットレート (ABR) が有効になっています。 カスタム ABR コントロールを設定することで、Primetime 設定ユーザーインターフェイスを使用して、参照実装のデフォルトの TVSDK 動作を上書きできます。

設定ユーザーインターフェイスを介してカスタム ABR を有効にするには：

* Primetime 設定ダイアログを開きます。
* 選択 **[!UICONTROL ABR controls]**.

  ![](assets/abr-configuration.jpg)

* 次をタップします。 [!UICONTROL Enable ON] 表示するように制御する `OFF`.

The `PlaybackManager` ABR パラメーターを設定するのは、 [isABRControlEnabled](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html) は true(ON) を返します。 false (OFF) を返す場合、 `PlaybackManager` はデフォルトの ABR 制御を使用し、初期ビットレート、最小ビットレート、最大ビットレートがすべて 0 になり、ABR ポリシーが `ABR_MODERATE`.

## 低ビットレート用にを設定 {#section_5451691CBBD24542AD54A474D222CD39}

一部の低ビットレート再生レートの場合、 TVSDK はデフォルトで、オーディオ専用ストリームに切り替わり、再生がフリーズしたように見えます。 プレーヤーが音声のみに切り替わる状況が発生しないように設定できます。

* の実装 [IPlaybackConfig](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html) インターフェイス：

* 以下を確認します。 [getABRMinBitRate](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html#getABRMinBitRate()) は、オーディオのみのビットレート (64000より高い ) を超えます。
* 以下を確認します。 [isABRControlEnabled](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html#isABRControlEnabled()) がオンになっている。
