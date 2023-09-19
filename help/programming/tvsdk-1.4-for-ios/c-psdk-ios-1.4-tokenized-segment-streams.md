---
description: コンテンツ配信ネットワーク (CDN) を通じて配信される HLS ストリームでは、マニフェストで認証トークンを使用し、検証のためにセグメントリクエストを使用する場合があります。 これらのトークンは、URL パラメーターとして、または Cookie ヘッダーとして提供できます。
title: トークン化されたセグメントストリーム
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# トークン化されたセグメントストリーム{#tokenized-segment-streams}

コンテンツ配信ネットワーク (CDN) を通じて配信される HLS ストリームでは、マニフェストで認証トークンを使用し、検証のためにセグメントリクエストを使用する場合があります。 これらのトークンは、URL パラメーターとして、または Cookie ヘッダーとして提供できます。

マスターマニフェスト (m3u8) の応答で cookie として提供されたトークンは、セグメントリクエストが同じドメインの場合でも、セグメント (ts) リクエストと共有されません。 セグメントリクエストでこれらの Cookie を共有できるようにするには、 `PTMetadata` プレーヤーアイテムに提供されるインスタンス： 

```
PTMetadata *metadata = [[[PTMetadata alloc] init] autorelease]; 
[metadata setValue:[NSNumber numberWithBool:YES] forKey:kSyncCookiesWithAVAsset]; 
```

ストリームの再生が開始される前に、マスターマニフェスト (m3u8) に追加のリクエストが送信されます。

>[!IMPORTANT]
>
>この cookie 共有機能は、iOS 8 以降を実行するデバイスでのみサポートされます。
