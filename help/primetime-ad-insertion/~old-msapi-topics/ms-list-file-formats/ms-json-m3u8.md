---
description: pttrackingmode=simpleまたはptplayer=ios-mobilewebの場合、マニフェストサーバーは、マスターM3U8を含むJSON形式のファイルを返します。このファイルは、クライアントがコンテンツを記述するM3U8ファイルを要求する際に使用するURLです。
title: バリアントマニフェストプレイリストを要求するURLのJSON形式
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 0%

---


# バリアントマニフェストプレイリスト{#json-format-for-url-for-requesting-variant-manifest-playlist}をリクエストするURLのJSON形式

`pttrackingmode=simple`または`ptplayer=ios-mobileweb`の場合、マニフェストサーバーはマスターM3U8を含むJSON形式のファイルを返します。これは、クライアントがコンテンツを記述するM3U8ファイルを要求する際に使用するURLです。

これは、`Master-M3U8` URLを含むJSONファイルの形式です。

```
{
"Master-M3U8": "https://manifest.auditude.com/auditude/variant/{publisherAssetID}/
  {sessionId}/{Base 64 of the url of the content}.m3u8
  ?u={Ad Request Id}
  &z={Ad Zone Id}
  &pttrackingmode=simple
  &pttrackingversion=v1
  &{other query parameters}"
}
```
