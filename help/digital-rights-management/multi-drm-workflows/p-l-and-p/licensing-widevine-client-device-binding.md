---
description: 場合によっては、コンテンツを購入またはレンタルする際に、エンドユーザーが複数のデバイスでコンテンツを再生できないように制限する必要があります。 お客様が Expressplay を使用している場合は、Expressplay API を使用して、ユーザーの Expressplay トークンをユーザーのマシンにバインドすることで、これをおこなうことができます。
title: デバイスのバインディング
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# デバイスのバインディング{#device-binding}

場合によっては、コンテンツを購入またはレンタルする際に、エンドユーザーが複数のデバイスでコンテンツを再生できないように制限する必要があります。 お客様が Expressplay を使用している場合は、Expressplay API を使用して、ユーザーの Expressplay トークンをユーザーのマシンにバインドすることで、これをおこなうことができます。

API は以下の方法で使用できます。

1. cookie を生成します。
1. 生成された cookie をクエリ文字列 (cookie=`<cookie>`) またはをヘッダーとして追加します。
1. ユーザーのマシンに、上記のトークンを使用して、例えばダミーのコンテンツを再生するなどして、Expressplay ライセンスサーバーにライセンスリクエストを送信させます。

   このダミーのライセンスリクエストが成功すると、はユーザーの device_id（ユーザーのデバイスの DRM 実装で計算または生成）を Expressplay バックエンドの cookie に関連付けます。 この cookie は、その後、次の方法で使用されます。

   * コンテンツの購入時/レンタル時に、コードは関連する Cookie( [https://www.expressplay.com/developer/restapi/#record-retrieval](https://www.expressplay.com/developer/restapi/#record-retrieval))
   * 購入したコンテンツのキー (CEK)、キー ID(CEKSID)、ポリシーおよびその他の情報を含むトークン生成リクエストを送信し、上記の cookie および device_id を、それぞれ `cookie` 相関パラメーターと `deviceid` トークン制限パラメーター。

   * このトークンをユーザーに提供します。

     このプロセスは、ユーザーの device_id にバインドされたコンテンツのトークンを生成します。 ユーザーのマシンがこのトークンを使用してライセンスリクエストを送信すると、Expressplay バックエンドは、ライセンスリクエストの device_id を使用してトークンの device_id をクロスチェックします。

     このワークフローは、サンプルの Expressplay エンタイトルメントサーバーが実装しています。
