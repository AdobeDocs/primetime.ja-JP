---
description: Video Player Ad-Serving Interface Definition(VPAID) は、ビデオ広告を再生するための共通のインターフェイスを提供します。 VPAID は、ユーザーにリッチメディアエクスペリエンスを提供し、発行者が広告のターゲティング、広告インプレッションの追跡、ビデオコンテンツの収益化を改善できます。
title: カスタム広告要件
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# カスタム広告要件 {#custom-ad-requirements}

TVSDK プレーヤーは、デジタルビデオプレーヤー広告インターフェイス定義 (VPAID) 広告を再生し、広告の読み込みステータスを表示できます。 広告にエラーがある場合、または広告の読み込みに時間がかかりすぎる場合、 TVSDK はこれらの広告を無視します。

Video Player Ad-Serving Interface Definition(VPAID) は、ビデオ広告を再生するための共通のインターフェイスを提供します。 VPAID は、ユーザーにリッチメディアエクスペリエンスを提供し、発行者が広告のターゲティング、広告インプレッションの追跡、ビデオコンテンツの収益化を改善できます。

<!--<a id="section_9A358902CBC24999BA34206EE2029616"></a>-->

TVSDK は、次の機能をサポートしています。

* VPAID 仕様のバージョン 1.0 および 2.0
* ビデオオンデマンド (VOD) コンテンツのリニア VPAID 広告
* FlashVPAID 広告

  VPAID 広告はFlashベースである必要があり、広告応答は、VPAID 広告のメディアタイプを `application/x-shockwave-flash`.

次の機能はサポートされていません。

* オーバーレイ広告や動的なコンパニオン広告などの非線形広告
* VPAID 広告のプリロード
* ライブコンテンツ内の VPAID 広告
* JavaScript VPAID 広告

## 読み込みステータス {#section_5F55C0101CD44A65BCFE1D124CBDF239}

TVSDK は、以下のイベントをディスパッチします。

* `AdLoading`
* `AdLoaded`
* `AdStarted`
* `AdPlaying`
* `AdStopped`

次の期間の後に `AdStopped` イベント内で、 TVSDK がビデオコンテンツを再開します。

>[!TIP]
>
>値に 0 を指定した場合、 TVSDK は、広告が読み込まれるか、エラーが発生するまで、広告の読み込みを試みます。

## 広告の無視 {#section_3EA452F420884335AE90DF23C17E416A}

広告の読み込みに時間がかかりすぎる場合や、広告にエラーがある場合、 TVSDK は広告を無視でき、広告ポッド内の次の広告が自動的に再生されます。

次の場合、 `AuditudeSettings.customAdLoadTimeout` に 0 より大きい秒数を指定すると、 TVSDK は、指定された時間まで広告の読み込みを試みます。 広告を読み込めない場合、広告はスキップされます。 例えば、 `AuditudeSettings.customAdLoadTimeout:5`を指定した場合、 TVSDK は広告の読み込みを最大 5 秒間試行します。 広告がまだ読み込まれない場合、その広告は無視されます。
