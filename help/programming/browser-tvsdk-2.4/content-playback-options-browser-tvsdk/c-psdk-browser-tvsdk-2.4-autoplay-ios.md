---
title: iOSでの自動再生
description: iOSでの自動再生
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '93'
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

