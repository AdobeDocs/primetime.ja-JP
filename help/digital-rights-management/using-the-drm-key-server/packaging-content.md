---
seo-title: コンテンツのパッケージ化
title: コンテンツのパッケージ化
uuid: 366c8470-b7ef-4a39-83c2-151ba9be9a32
translation-type: tm+mt
source-git-commit: 1547eb3dd220fafc08df923f40504736c16a866c
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---


# コンテンツのパッケージ化{#packaging-content}

リモートキー配信用にコンテンツをパッケージ化する場合は、リモートキー配信が必要であることを指定するポリシーを使用します。 キーサーバーURLは、HLSコンテンツのM3U8（マニフェストファイル）に含まれている必要があります。 Primetime DRMキーサーバーのURLの形式は次のとおりです。

```
https://key-server-host:port/faxsks/tenant-name/key
```

例えば、ポート443でリッスンしているキーサーバーのホスト名[!DNL mykeyserver.com]と、`tenant1`という名前のテナントの場合、M3U8で指定するキーサーバーのURLは次のようになります。

```
https://mykeyserver.com:443/faxsks/tenant1/key
```

iOSとXbox 360の両方のクライアントに同じURLを使用できます。 また、サーバーがクライアントタイプごとに個別のテナントを使用して設定されている場合は、異なるURLを使用できます。

ライセンスサーバのURLが正しく設定された実行中のライセンスサーバを指している限り、キーサーバを必要としないクライアントでも同じコンテンツを再生できます。
