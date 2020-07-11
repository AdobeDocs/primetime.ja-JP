---
seo-title: コンテンツのパッケージ化
title: コンテンツのパッケージ化
uuid: 5d1d4b9d-f241-4291-9577-e9de5a8b92be
translation-type: tm+mt
source-git-commit: 58bb3bedc5b0ac63afd96eb6101d9ad779e6deed
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---


# コンテンツのパッケージ化{#packaging-content}

コンテンツをパッケージ化する場合は、ライセンスサーバーのURLを指定する必要があります。 Adobe Access ServerのURLは次の形式で指定します。

```
http(s):// license-server-host:port/flashaccessserver/tenant-name
```

例えば、ポート8080でリッスンしているライセンスサーバーホスト名「mylicenseserver.com」と、パッケージ化時に指定するライセンスサーバーのURLは、次のようになります。

```
https://mylicenseserver.com:8080/flashaccessserver/tenant1
```

各テナントが異なるLicense ServerとTransport Credentialを使用している場合は、Packagerで正しいテナントの証明書を必ず指定してください。

サーバーが既知のパッケージャーによってパッケージ化されたコンテンツに対してのみライセンスを発行するようにするには、Packagerの証明書をテナント設定ファイルのPackager許可リストに含めます。
