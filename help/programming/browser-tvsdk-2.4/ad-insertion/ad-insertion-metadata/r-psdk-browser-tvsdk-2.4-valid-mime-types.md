---
description: 広告には複数のクリエイティブが含まれ、その中から 1 つが再生対象として選択されている場合があります。
title: 有効な MIME タイプ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 0%

---

# 有効な MIME タイプ{#valid-mime-types}

広告には複数のクリエイティブが含まれ、その中から 1 つが再生対象として選択されている場合があります。

MIME タイプを使用すると、ユーザーが優先できるクリエイティブタイプを指定できます。 ユーザーが指定する MIME タイプと、Browser TVSDK がサポートする MIME タイプを使用して、優先順位付けするクリエイティブを決定します。

Browser TVSDK で有効な MIME タイプを設定するには：

```js
var auditudeSettings = new AdobePSDK.AuditudeSettings(); 
var mimeTypes = [“video/mp4”, “application/x-mpegURL”]; 
auditudeSettings.validMimeTypes = mimeTypes; 
```

場所 `mimeTypes` は文字列の配列で、各文字列は mime タイプを表します。

1 つの広告に対して複数のメディアファイルが返される場合の選択は、メディアファイルの表示順に応じて異なります。 `validMimeTypes` 配列。 インデックスの低い MIME タイプは、インデックスの高い MIME タイプよりも優先されます。
