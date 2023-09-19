---
description: コンテンツをパッケージ化する場合は、ライセンスサーバー URL を指定する必要があります。
title: コンテンツのパッケージ化
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---

# コンテンツのパッケージ化{#packaging-content}

コンテンツをパッケージ化する場合は、ライセンスサーバー URL を指定する必要があります。

Adobe Primetime DRM サーバーの URL の形式は次のとおりです。

```
http(s)://<license-server-host:port>/flashaccessserver/<tenant-name>
```

例えば、ライセンスサーバーのホスト名の場合は、 `mylicenseserver.com` このサーバーは、ポート 8080 と呼ばれるテナントでリッスンします。 *`tenant1`*&#x200B;を使用する場合、コンテンツをパッケージ化する際に指定するライセンスサーバー URL に対して次の構文を使用します。

```
https://mylicenseserver.com:8080/flashaccessserver/tenant1
```

各テナントが異なるライセンスサーバーとトランスポート資格情報を使用している場合は、Packager で正しいテナントの証明書を必ず指定してください。

サーバーが既知のパッケージャーのコンテンツに対してのみライセンスを発行する場合は、テナント設定ファイルの packager許可リストにパッケージャーの証明書を含める必要があります。
