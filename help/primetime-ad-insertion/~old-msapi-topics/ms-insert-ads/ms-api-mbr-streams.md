---
description: 広告挿入のクライアントリクエストは、通常、バリアントM3U8形式のプレイリストに複数のビットレートを指定します。 マニフェストサーバーは、ビットレートごとに別々のM3U8リンクを含む新しいバリアントM3U8ファイルを生成して返します。 また、これらのM3U8を結び付けるための一意のグループIDも生成されます。
title: マルチビットレートストリーム
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---


# マルチビットレートストリーム{#multiple-bit-rate-streams}

広告挿入のクライアントリクエストは、通常、バリアントM3U8形式のプレイリストに複数のビットレートを指定します。 マニフェストサーバーは、ビットレートごとに別々のM3U8リンクを含む新しいバリアントM3U8ファイルを生成して返します。 また、これらのM3U8を結び付けるための一意のグループIDも生成されます。

マニフェストサーバーは、クライアントのBootstrapURL要求の情報を使用して、コンテンツバリアントプレイリストを取得します。 ストリームレベルのコンテンツへのマニフェストサーバーリンクを含む新しいバリアントプレイリストを生成します。 クライアントは、これらを使用して広告挿入リクエストを作成します。 マニフェストサーバーのストリームレベルコンテンツリンクの形式は次のとおりです。

```
https://manifest.auditude.com/auditude/{live/vod}/{publisherAssetID}/{rendition}/
  {groupID}/{base64-encoded url of the bit rate stream}.[m3u8]?{Query parameters}
```

* **`live/vod`** マニフェストサーバーは、コンテンツのプレイリストタイプに基づいてこの値を設定します。ライブ/リニア(#EXT-X-PLAYLIST-TYPE:イベント)またはVOD(#EXT-X-PLAYLIST-TYPE:VOD)

* **`publisherAssetID`** BootstrapURLリクエストで提供される特定のコンテンツに対する発行者の一意のID。

* **`rendition`** マニフェストサーバーは、これをコンテンツストリームのBANDWIDTH値に基づいて設定し、それを使用して広告のビットレートとコンテンツのビットレートとを一致させます。広告のビットレートは、最も低いビットレートの広告レンディションがそうしない限り、コンテンツのビットレートを超えることはできません。

* **`groupID`** マニフェストサーバーはこの値を生成し、それを使用して、クライアントが広告をリクエストするビットレートレンディションに関係なく、広告の配置を一貫性のあるものにします。

* **`base64-encoded url of the bit rate stream`** マニフェストサーバURLセーフベース64は、コンテンツストリームの絶対URLをエンコードする。各ストリームには、独自のURLがあります。

* **`Query parameters`** BootstrapURLリクエストで指定されるクエリパラメーター。

