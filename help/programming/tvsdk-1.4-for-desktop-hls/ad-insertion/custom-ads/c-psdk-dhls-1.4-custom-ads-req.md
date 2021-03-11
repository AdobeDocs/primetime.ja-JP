---
description: ビデオプレーヤー広告配信インターフェイス定義(VPAID)は、ビデオ広告を再生するための共通のインターフェイスです。 VPAIDは、ユーザーにリッチメディアの操作性を提供し、発行者は、ターゲット広告の改善、広告インプレッションの追跡、ビデオコンテンツの収益化を行うことができます。
title: カスタム広告要件
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---


# カスタム広告要件{#custom-ad-requirements}

TVSDKプレイヤーは、デジタルビデオプレイヤー広告インターフェイス定義(VPAID)広告を再生し、広告読み込みステータスを表示できます。 広告にエラーがある場合、または広告の読み込みに時間がかかりすぎる場合、TVSDKはこれらの広告を無視します。

ビデオプレーヤー広告配信インターフェイス定義(VPAID)は、ビデオ広告を再生するための共通のインターフェイスです。 VPAIDは、ユーザーにリッチメディアの操作性を提供し、発行者は、ターゲット広告の改善、広告インプレッションの追跡、ビデオコンテンツの収益化を行うことができます。

<!--<a id="section_9A358902CBC24999BA34206EE2029616"></a>-->

TVSDKは、次の機能をサポートしています。

* VPAID仕様のバージョン1.0および2.0
* ビデオオンデマンド(VOD)コンテンツのリニアVPAID広告
* FlashVPAID広告

   VPAID広告はFlashベースである必要があり、広告応答はVPAID広告のメディアタイプを`application/x-shockwave-flash`として識別する必要があります。

次の機能はサポートされていません。

* オーバーレイ広告や動的コンパニオン広告などのノンリニア広告
* VPAID広告のプリロード
* ライブコンテンツ内のVPAID広告
* JavaScript VPAID広告

## ロード状態{#section_5F55C0101CD44A65BCFE1D124CBDF239}

TVSDKは、以下のイベントをディスパッチします。

* `AdLoading`
* `AdLoaded`
* `AdStarted`
* `AdPlaying`
* `AdStopped`

`AdStopped`イベントの後、TVSDKはビデオコンテンツを再開します。

>[!TIP]
>
>値0を指定した場合、TVSDKは広告が読み込まれるか、エラーが発生するまで、広告の読み込みを試みます。

## 広告を無視{#section_3EA452F420884335AE90DF23C17E416A}

広告の読み込みに時間がかかり過ぎるか、広告にエラーがある場合、TVSDKは広告を無視でき、広告ポッド内の次の広告が自動的に再生されます。

`AuditudeSettings.customAdLoadTimeout`設定でゼロより大きい秒数を指定した場合、TVSDKは広告を指定された時間に読み込もうとします。 広告を読み込めない場合、その広告はスキップされます。 例えば、`AuditudeSettings.customAdLoadTimeout:5`を設定した場合、TVSDKは広告の読み込みを最大5秒間試みます。 広告がまだ読み込まれない場合、その広告は無視されます。
