---
description: コンテンツ配信ネットワーク(CDN)を介して配信されるHLSストリームは、マニフェストで認証トークンを使用し、検証のためにセグメントリクエストを使用する場合があります。 これらのトークンは、URLパラメーターまたはcookieヘッダーとして提供できます。
seo-description: コンテンツ配信ネットワーク(CDN)を介して配信されるHLSストリームは、マニフェストで認証トークンを使用し、検証のためにセグメントリクエストを使用する場合があります。 これらのトークンは、URLパラメーターまたはcookieヘッダーとして提供できます。
seo-title: トークン化セグメントストリーム
title: トークン化セグメントストリーム
uuid: 62e3b858-2605-4960-b504-9010674f80ad
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# トークン化セグメントストリーム {#tokenized-segment-streams}

コンテンツ配信ネットワーク(CDN)を介して配信されるHLSストリームは、マニフェストで認証トークンを使用し、検証のためにセグメントリクエストを使用する場合があります。 これらのトークンは、URLパラメーターまたはcookieヘッダーとして提供できます。

マスターマニフェスト(m3u8)応答でcookieとして提供されたトークンは、セグメントリクエストが同じドメインに対するものであっても、セグメント(ts)リクエストと共有されません。 セグメントリクエストでこれらのcookieの共有を有効にするには、プレーヤーアイテムに提供されたインスタ `PTMetadata` ンスで次のプロパティを設定します。

```
PTMetadata *metadata = [[[PTMetadata alloc] init] autorelease]; 
[metadata setValue:[NSNumber numberWithBool:YES] forKey:kSyncCookiesWithAVAsset]; 
```

ストリームの再生が開始される前に、マスターマニフェスト(m3u8)に追加のリクエストが行われます。

>[!IMPORTANT]
>
>このcookie共有機能は、iOS 8以降を実行するデバイスでのみサポートされます。

