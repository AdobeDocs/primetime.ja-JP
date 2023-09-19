---
title: コンテンツのパッケージ化
description: コンテンツのパッケージ化
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---

# コンテンツのパッケージ化{#packaging-content}

リモートキー配信用にコンテンツをパッケージ化する場合は、リモートキー配信が必要であることを指定するポリシーを使用します。 HLS コンテンツの M3U8（マニフェストファイル）にキーサーバー URL を含める必要があります。 Primetime DRM キーサーバーの URL の形式は次のとおりです。

```
https://key-server-host:port/faxsks/tenant-name/key
```

例：キーサーバーのホスト名 [!DNL mykeyserver.com] ポート 443 でリッスンし、次の名前を持つテナント `tenant1`M3U8 で指定する主要なサーバ URL は次のとおりです。

```
https://mykeyserver.com:443/faxsks/tenant1/key
```

iOSと Xbox 360 の両方のクライアントに同じ URL を使用できます。 また、サーバーがクライアントタイプごとに別々のテナントで設定されている場合は、異なる URL を使用できます。

ライセンスサーバー URL が正しく設定された実行中のライセンスサーバーを指している限り、キーサーバーを必要としないクライアントでも、同じコンテンツが再生される場合があります。
