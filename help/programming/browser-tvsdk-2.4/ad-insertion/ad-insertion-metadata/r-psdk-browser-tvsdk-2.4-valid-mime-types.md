---
description: 広告には複数のクリエイティブが含まれる場合があり、その中から1つが再生対象として選択されます。
seo-description: 広告には複数のクリエイティブが含まれる場合があり、その中から1つが再生対象として選択されます。
seo-title: 有効なMIMEタイプ
title: 有効なMIMEタイプ
uuid: ab2baac9-a9ef-44f1-83a1-2e6e471e3231
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---


# 有効なMIMEタイプ{#valid-mime-types}

広告には複数のクリエイティブが含まれる場合があり、その中から1つが再生対象として選択されます。

MIMEタイプを使用して、ユーザーに優先順位を付けることのできるクリエイティブタイプを指定できます。 ユーザーが指定するMIMEタイプと、Browser TVSDKがサポートするMIMEタイプを使用して、優先順位を付けるクリエイティブを決定します。

ブラウザーTVSDKで有効なMIMEタイプを設定するには：

```js
var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
var mimeTypes = [“video/mp4”, “application/x-mpegURL”]; 
auditudeSettings.validMimeTypes = mimeTypes; 
```

`mimeTypes`は文字列の配列で、各文字列はMIMEタイプを表します。

1つの広告に対して複数のメディアファイルが返される場合、選択は`validMimeTypes`配列でメディアファイルが表示される順序に依存します。 インデックスの低いMIME型は、インデックスの高いMIME型よりも優先されます。
