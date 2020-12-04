---
description: コンテンツ配信ネットワーク(CDN)経由で配信されるHLSストリームは、マニフェストの認証トークンと、検証用のセグメントリクエストを使用する場合があります。 これらのトークンは、URLパラメーターとして、またはcookieヘッダーとして提供できます。
seo-description: コンテンツ配信ネットワーク(CDN)経由で配信されるHLSストリームは、マニフェストの認証トークンと、検証用のセグメントリクエストを使用する場合があります。 これらのトークンは、URLパラメーターとして、またはcookieヘッダーとして提供できます。
seo-title: トークン化セグメントストリーム
title: トークン化セグメントストリーム
uuid: b17bb5bc-2029-4113-ac44-b1d30aa08ca6
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---


# トークン化されたセグメントストリーム{#tokenized-segment-streams}

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

