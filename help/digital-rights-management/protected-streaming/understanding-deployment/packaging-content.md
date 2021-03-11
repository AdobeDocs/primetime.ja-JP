---
description: コンテンツをパッケージ化する場合は、ライセンスサーバーのURLを指定する必要があります。
title: コンテンツのパッケージ化
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---


# コンテンツのパッケージ化{#packaging-content}

コンテンツをパッケージ化する場合は、ライセンスサーバーのURLを指定する必要があります。

Adobe PrimetimeDRMサーバーのURLは次の形式を使用します。

```
http(s)://<license-server-host:port>/flashaccessserver/<tenant-name>
```

例えば、ポート8080をリッスンするライセンスサーバーホスト名`mylicenseserver.com`とテナント名&#x200B;*`tenant1`*&#x200B;の場合、コンテンツのパッケージ化時に指定するライセンスサーバーURLに次の構文を使用します。

```
https://mylicenseserver.com:8080/flashaccessserver/tenant1
```

各テナントが異なるライセンスサーバーとトランスポート資格情報を使用する場合は、パッケージャーで正しいテナントの証明書を指定していることを確認してください。

サーバーが既知のパッケージャーのコンテンツに対してのみライセンスを発行するようにする場合は、テナント設定ファイルのpackager許可リストにパッケージャーの証明書を含める必要があります。
