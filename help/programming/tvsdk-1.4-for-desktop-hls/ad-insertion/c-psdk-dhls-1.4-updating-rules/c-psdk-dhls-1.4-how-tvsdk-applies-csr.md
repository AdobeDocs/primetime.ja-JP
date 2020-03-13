---
description: 'null'
seo-description: 'null'
seo-title: クリエイティブ選択ルールの適用
title: クリエイティブ選択ルールの適用
uuid: 464c32db-1c96-4d91-97ce-f1d95e57c062
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# クリエイティブ選択ルールの適用{#applying-creative-selection-rules}

TVSDKは、次の方法でクリエイティブの選択ルールを適用します。

* TVSDKは、最初にすべての `default` ルールを適用し、次にゾーン固有のルールを適用します。
* TVSDKは、現在のゾーンIDに対して定義されていないルールを無視します。
* TVSDKがデフォルトのルールを適用すると、ゾーン固有のルールは、ルールで選択されたクリエイティブに対する `host` （ドメイン）の一致に基づいて、クリエイティブの優先順位をさらに変更で `default` きます。

* 追加のゾーンルールを含むサンプルルールファイルでは、TVSDKがルールを適用すると、M3U8クリエイティブドメインにまたはが含まれていない場合、または広告ゾーンが含まれている場合、クリエイティブは再順序付けされ、 `default`[!DNL my.domain.com][!DNL a.bcd.com]`1234`Flash VPAIDクリエイティブが最初に再生されます。 それ以外の場合は、MP4広告が再生され、JavaScriptが再生されます。

* TVSDKがネイティブに再生できない（など）広告クリエイティブが選択さ [!DNL .mp4]れている場合、TVSDK [!DNL .flv]は再パッケージ化リクエストを発行します。

TVSDKで処理できる広告タイプは、の設定を通じて定義され `validMimeTypes` ます `AuditudeSettings`。
