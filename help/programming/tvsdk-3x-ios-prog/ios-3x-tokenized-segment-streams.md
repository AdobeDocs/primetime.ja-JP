---
description: コンテンツ配信ネットワーク(CDN)経由で配信されるHLSストリームは、マニフェストの認証トークンと、検証用のセグメントリクエストを使用する場合があります。 これらのトークンは、URLパラメーターとして、またはcookieヘッダーとして提供できます。
seo-description: コンテンツ配信ネットワーク(CDN)経由で配信されるHLSストリームは、マニフェストの認証トークンと、検証用のセグメントリクエストを使用する場合があります。 これらのトークンは、URLパラメーターとして、またはcookieヘッダーとして提供できます。
seo-title: トークン化セグメントストリーム
title: トークン化セグメントストリーム
uuid: 62e3b858-2605-4960-b504-9010674f80ad
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---


# トークン化セグメントストリーム{#tokenized-segment-streams}

コンテンツ配信ネットワーク(CDN)経由で配信されるHLSストリームは、マニフェストの認証トークンと、検証用のセグメントリクエストを使用する場合があります。 これらのトークンは、URLパラメーターとして、またはcookieヘッダーとして提供できます。

マスターマニフェスト(m3u8)応答に対してcookieとして指定されたトークンは、セグメントリクエストが同じドメインに対するものでも、セグメント(ts)リクエストと共有されません。 セグメントリクエストでこれらのcookieの共有を有効にするには、プレイヤー項目に指定された`PTMetadata`インスタンスに次のプロパティを設定します。 

```
PTMetadata *metadata = [[[PTMetadata alloc] init] autorelease]; 
[metadata setValue:[NSNumber numberWithBool:YES] forKey:kSyncCookiesWithAVAsset]; 
```

ストリームの再生が開始する前に、追加のリクエストがマスターマニフェスト(m3u8)に対して行われます。

>[!IMPORTANT]
>
>このcookie共有機能は、iOS 8以降を実行するデバイスでのみサポートされます。

