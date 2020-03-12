---
description: 広告には複数のクリエイティブが含まれ、その中から1つが再生対象として選択される場合があります。
seo-description: 広告には複数のクリエイティブが含まれ、その中から1つが再生対象として選択される場合があります。
seo-title: 有効なMIMEタイプ
title: 有効なMIMEタイプ
uuid: ab2baac9-a9ef-44f1-83a1-2e6e471e3231
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# 有効なMIMEタイプ{#valid-mime-types}

広告には複数のクリエイティブが含まれ、その中から1つが再生対象として選択される場合があります。

MIMEタイプを使用すると、ユーザーが優先順位を付けることのできるクリエイティブタイプを指定できます。 ユーザーが指定するMIMEタイプと、ブラウザーTVSDKがサポートするMIMEタイプを使用して、どのクリエイティブが優先付けされるかが決定されます。

ブラウザーTVSDKで有効なMIMEタイプを設定するには：

```js
var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
var mimeTypes = [“video/mp4”, “application/x-mpegURL”]; 
auditudeSettings.validMimeTypes = mimeTypes; 
```

は文 `mimeTypes` 字列の配列で、各文字列はMIMEタイプを表します。

1つの広告に対して複数のメディアファイルが返される場合、選択はメディアファイルが配列に表示される順序に依存し `validMimeTypes` ます。 インデックスの低いMIMEタイプは、インデックスの高いMIMEタイプよりも優先されます。
