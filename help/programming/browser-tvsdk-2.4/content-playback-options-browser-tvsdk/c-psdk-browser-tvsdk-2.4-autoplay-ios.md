---
description: 'null'
seo-description: 'null'
seo-title: iOSでの自動再生
title: iOSでの自動再生
uuid: d15bad24-be50-49e5-90f4-68dbda96fb6d
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# iOSでの自動再生{#autoplay-on-ios}

AdobePSDK.MediaPlayerのボリュームAPIの実装により、iOSバージョン10以上を実行するデバイスでコンテンツを自動再生できます。 iOSでは、ボリュームがミュートになっている場合にのみ自動再生が許可されます。 ボリュームが0に設定されると、APIはビデオタグのプ `muted` ロパティをに設定し、それ以外の場 `true`合はプ `muted` ロパティをに設定しま `false`す。 APIは、ユ `play` ーザーの操作やユーザーの操作を行わなくても再生を開始します。

iPhoneで自動再生する場合は、タグのプ `playsInline` ロパティをに設 `video` 定しま `true`す。

```
videoDiv.getElementsByTagName('video')[0].playsInline = true;
```

>[!NOTE]
>
>プロパティを使 `playsInline` 用すると、フルスクリーンモードなしで再生が開始されます。

