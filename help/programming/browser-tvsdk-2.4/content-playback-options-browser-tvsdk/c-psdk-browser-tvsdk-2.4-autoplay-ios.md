---
description: 'null'
seo-description: 'null'
seo-title: iOSでの自動再生
title: iOSでの自動再生
uuid: d15bad24-be50-49e5-90f4-68dbda96fb6d
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---


# iOSでの自動再生{#autoplay-on-ios}

AdobePSDK.MediaPlayerのボリュームAPIが実装されているため、iOSバージョン10以降を実行するデバイスでコンテンツを自動再生できます。 iOSでは、ボリュームがミュートになっている場合にのみ自動再生が許可されます。 ボリュームが0に設定されると、APIはビデオタグの`muted`プロパティを`true`に設定し、それ以外の場合は`muted`プロパティを`false`に設定します。 `play` APIは、ユーザーによる操作やユーザージェスチャを行わずに再生を開始します。

iPhoneで自動再生する場合は、`video`タグの`playsInline`プロパティを`true`に設定します。

```
videoDiv.getElementsByTagName('video')[0].playsInline = true;
```

>[!NOTE]
>
>`playsInline`プロパティを使用すると、フルスクリーンモードを使用しない再生が開始されます。

