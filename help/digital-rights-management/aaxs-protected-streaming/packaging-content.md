---
seo-title: コンテンツのパッケージ化
title: コンテンツのパッケージ化
uuid: 5d1d4b9d-f241-4291-9577-e9de5a8b92be
translation-type: tm+mt
source-git-commit: 47b2ed65ff0ea4f54a210cf7627ed535782296b9

---


# コンテンツのパッケージ化{#packaging-content}

コンテンツをパッケージ化する場合は、ライセンスサーバーのURLを指定する必要があります。 Adobe Access ServerのURLの形式は次のとおりです。

```
http(s):// license-server-host:port/flashaccessserver/tenant-name
```

例えば、ポート8080でリッスンしているライセンスサーバーホスト名「mylicenseserver.com」と、「tenant1」という名前のテナントの場合、パッケージ化時に指定するライセンスサーバーのURLは、次のようになります。

```
https://mylicenseserver.com:8080/flashaccessserver/tenant1
```

各テナントが異なるライセンスサーバーとトランスポート資格情報を使用する場合は、パッケージャーで正しいテナントの証明書を必ず指定してください。

サーバーが既知のパッケージャーによってパッケージ化されたコンテンツに対してのみライセンスを発行するようにするには、Packagerの証明書をテナント設定ファイルのPackagerホワイトリストに含めます。
