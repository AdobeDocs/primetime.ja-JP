---
description: 'null'
keywords: creative selection rules;AdobeTVSDKConfig
seo-description: 'null'
seo-title: クリエイティブ選択ルールの適用
title: クリエイティブ選択ルールの適用
uuid: 66e55f95-25ce-4838-b222-63ee34e535d1
translation-type: tm+mt
source-git-commit: 3fdae2b6babb578d2cacff970fd9c7b53ad2c5dc

---


# クリエイティブ選択ルールの適用 {#apply-creative-selection-rules}

TVSDKは、次の方法でクリエイティブの選択ルールを適用します。

* TVSDKは、最初にすべての `default` ルールを適用し、次にゾーン固有のルールを適用します。
* TVSDKは、現在のゾーンIDに対して定義されていないルールを無視します。
* TVSDKがデフォルトのルールを適用すると、ゾーン固有のルールは、ルールで選択されたクリエイティブに対する `host` （ドメイン）の一致に基づいて、クリエイティブの優先順位をさらに変更で `default` きます。

* 追加のゾーンルールを含むサンプルルールファイルでは、TVSDKがルールを適用すると、M3U8クリエイティブドメインにまたはが含まれていない場合、または広告ゾーンが含まれている場合、クリエイティブは再順序付けされ、 `default``my.domain.com``a.bcd.com``1234`Flash VPAIDクリエイティブが最初に再生されます。 それ以外の場合は、MP4広告が再生され、JavaScriptが再生されます。

* TVSDKがネイティブに再生できない（など）広告クリエイティブが選択さ [!DNL .mp4]れている場合、TVSDK [!DNL .flv]は再パッケージ化リクエストを発行します。

TVSDKで処理できる広告タイプは、の設定を通じて定義され `validMimeTypes` ます `AuditudeSettings`。

<!-- 

In Android 2.5 API docs, I see a 
<span class="codeph"> setValidMimeTypes</span> but not a 
<span class="codeph"> getValidMimeTypes</span>.

 -->

