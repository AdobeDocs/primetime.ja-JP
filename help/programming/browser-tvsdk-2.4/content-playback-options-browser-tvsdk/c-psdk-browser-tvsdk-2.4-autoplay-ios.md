---
title: iOSでの自動再生
description: iOSでの自動再生
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---

# iOSでの自動再生{#autoplay-on-ios}

AdobePSDK.MediaPlayer のボリューム API が実装されると、iOSバージョン 10 以降を実行するデバイスでコンテンツを自動再生できます。 iOSでは、ボリュームがミュートされている場合にのみ自動再生が許可されます。 ボリュームが 0 に設定されている場合、API は `muted` に対するビデオタグのプロパティ `true`、それ以外の場合は `muted` プロパティはに設定されます。 `false`. The `play` API は、ユーザーの操作やユーザーのジェスチャーを行わずに再生を開始します。

iPhoneで自動再生の場合、 `playsInline` のプロパティ `video` タグを `true`.

```
videoDiv.getElementsByTagName('video')[0].playsInline = true;
```

>[!NOTE]
>
>の使用 `playsInline` プロパティは、全画面モードを使用せずに再生を開始します。
