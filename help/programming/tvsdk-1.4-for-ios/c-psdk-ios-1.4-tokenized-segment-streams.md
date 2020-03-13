---
description: コンテンツ配信ネットワーク(CDN)を介して配信されるHLSストリームは、マニフェストで認証トークンを使用し、検証のためにセグメントリクエストを使用する場合があります。 これらのトークンは、URLパラメーターまたはcookieヘッダーとして提供できます。
seo-description: コンテンツ配信ネットワーク(CDN)を介して配信されるHLSストリームは、マニフェストで認証トークンを使用し、検証のためにセグメントリクエストを使用する場合があります。 これらのトークンは、URLパラメーターまたはcookieヘッダーとして提供できます。
seo-title: トークン化セグメントストリーム
title: トークン化セグメントストリーム
uuid: b17bb5bc-2029-4113-ac44-b1d30aa08ca6
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# トークン化セグメントストリーム{#tokenized-segment-streams}

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

