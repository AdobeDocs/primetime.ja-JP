---
keywords: クリエイティブ選択ルール；AdobeTVSDKConfig
title: クリエイティブ選択ルールを適用
description: クリエイティブ選択ルールを適用
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---

# クリエイティブ選択ルールを適用 {#apply-creative-selection-rules}

TVSDK は、以下の方法でクリエイティブ選択ルールを適用します。

* TVSDK は、すべてを適用します `default` ルールを最初に設定し、次にゾーン固有のルールを設定します。
* TVSDK は、現在のゾーン ID に対して定義されていないルールを無視します。
* TVSDK がデフォルトのルールを適用すると、ゾーン固有のルールによって、 `host` （ドメイン）が `default` ルール。

* 追加のゾーンルールが含まれるサンプルルールファイルでは、 TVSDK が `default` ルール (M3U8 クリエイティブドメインに [!DNL my.domain.com] または [!DNL a.bcd.com] 広告ゾーンは `1234`に設定すると、クリエイティブは並べ替えられ、FlashVPAID クリエイティブがある場合は最初に再生されます。 それ以外の場合は、MP4 広告が再生され、その後 JavaScript が再生されます。

* 広告クリエイティブが選択されている場合、 TVSDK はネイティブで再生できません ( [!DNL .mp4], [!DNL .flv]など )、 TVSDK は再パッケージ化リクエストを発行します。

TVSDK で処理できる広告タイプは、 `validMimeTypes` 設定 `AuditudeSettings`.
