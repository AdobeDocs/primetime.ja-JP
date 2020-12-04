---
description: 'null'
keywords: creative selection rules;AdobeTVSDKConfig
seo-description: 'null'
seo-title: クリエイティブ選択ルールの適用
title: クリエイティブ選択ルールの適用
uuid: 2f009776-201c-418e-aa8f-cb409d0046d8
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---


# クリエイティブ選択ルールの適用{#apply-creative-selection-rules}

TVSDKは、次の方法でクリエイティブ選択ルールを適用します。

* TVSDKは、最初にすべての`default`ルールを適用し、次にゾーン固有のルールを適用します。
* TVSDKは、現在のゾーンIDに対して定義されていないルールを無視します。
* TVSDKがデフォルトのルールを適用すると、ゾーン固有のルールは、`default`ルールで選択されたクリエイティブに対する`host` （ドメイン）の一致に基づいて、クリエイティブの優先順位をさらに変更できます。

* 追加のゾーンルールを含むサンプルルールファイルでは、TVSDKが`default`ルールを適用すると、M3U8クリエイティブドメインに[!DNL my.domain.com]または[!DNL a.bcd.com]が含まれず、広告ゾーンが`1234`の場合、クリエイティブが再順序付けされ、FlashVPAIDクリエイティブが最初に再生されます。 それ以外の場合は、MP4広告が再生され、JavaScriptにダウンします。

* TVSDKがネイティブ（[!DNL .mp4]、[!DNL .flv]など）再生できない広告クリエイティブを選択した場合、TVSDKは再パッケージ化リクエストを発行します。

TVSDKで処理できる広告タイプは、`AuditudeSettings`の`validMimeTypes`設定を通じて定義されます。