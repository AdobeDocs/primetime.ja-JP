---
title: コンテンツのパッケージ化
description: コンテンツのパッケージ化
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---

# コンテンツのパッケージ化{#packaging-content}

コンテンツをパッケージ化する場合は、ライセンスサーバーの URL を指定する必要があります。 Adobe Access Server URL の形式は次のとおりです。

```
http(s):// license-server-host:port/flashaccessserver/tenant-name
```

例えば、ポート 8080 でリッスンしているライセンスサーバーホスト名「mylicenseserver.com」と、パッケージ化時に指定するライセンスサーバー URL は次のようになります。

```
https://mylicenseserver.com:8080/flashaccessserver/tenant1
```

各テナントが異なるライセンスサーバーとトランスポート資格情報を使用している場合は、必ず Packager で正しいテナントの証明書を指定してください。

サーバーが既知のパッケージャーによってパッケージ化されたコンテンツに対してのみライセンスを発行するようにするには、テナント設定ファイルの packager許可リストにパッケージャーの証明書を含めます。
