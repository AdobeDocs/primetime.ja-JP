---
description: コンテンツをパッケージ化する場合は、ライセンスサーバーのURLを指定する必要があります。
seo-description: コンテンツをパッケージ化する場合は、ライセンスサーバーのURLを指定する必要があります。
seo-title: コンテンツのパッケージ化
title: コンテンツのパッケージ化
uuid: 2e47a9a2-bbc6-4995-8ce5-6ca6b116349b
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# コンテンツのパッケージ化{#packaging-content}

コンテンツをパッケージ化する場合は、ライセンスサーバーのURLを指定する必要があります。

Adobe Primetime DRMサーバーのURLは、次の形式を使用します。

```
http(s)://<license-server-host:port>/flashaccessserver/<tenant-name>
```

例えば、ポート8080でリス `mylicenseserver.com` ンするライセンスサーバーのホスト名で、テナントがという名前の場合、コンテンツのパッケージ化時に指定するライセンスサーバーのURLに次の構文を使用します *`tenant1`*。

```
https://mylicenseserver.com:8080/flashaccessserver/tenant1
```

各テナントが異なるライセンスサーバーとトランスポート資格情報を使用する場合は、パッケージャーで正しいテナントの証明書を指定していることを確認してください。

サーバーが既知のパッケージャーのコンテンツに対してのみライセンスを発行するようにする場合は、Packagerの証明書をテナント設定ファイルのPackagerホワイトリストに含める必要があります。
