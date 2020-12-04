---
description: pttrackingmode=simpleまたはptplayer=ios-mobilewebの場合、マニフェストサーバーは、マスターM3U8を含むJSON形式のファイルを返します。このファイルは、クライアントがコンテンツを記述するM3U8ファイルを要求する際に使用するURLです。
seo-description: pttrackingmode=simpleまたはptplayer=ios-mobilewebの場合、マニフェストサーバーは、マスターM3U8を含むJSON形式のファイルを返します。このファイルは、クライアントがコンテンツを記述するM3U8ファイルを要求する際に使用するURLです。
seo-title: バリアントマニフェストプレイリストを要求するURLのJSON形式
title: バリアントマニフェストプレイリストを要求するURLのJSON形式
uuid: 9f9693d0-3c93-4555-b20c-7f4576742f41
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9
workflow-type: tm+mt
source-wordcount: '133'
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
