---
description: 場合によっては、コンテンツの購入やレンタルを行う際に、エンドユーザーが複数のデバイスでコンテンツを再生するのを制限したい場合があります。 お客様がExpressplayを使用している場合は、Expressplay APIを使用してユーザーのExpressplayトークンをユーザーのマシンにバインドすることで、これを行うことができます。
title: デバイスバインディング
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---


# デバイスバインディング{#device-binding}

場合によっては、コンテンツの購入やレンタルを行う際に、エンドユーザーが複数のデバイスでコンテンツを再生するのを制限したい場合があります。 お客様がExpressplayを使用している場合は、Expressplay APIを使用してユーザーのExpressplayトークンをユーザーのマシンにバインドすることで、これを行うことができます。

APIは次の方法で使用できます。

1. Cookieを生成します。
1. 生成されたcookieをクエリ文字列(cookie=`<cookie>`)またはヘッダーとして添付して、ダミートークン生成リクエストを送信します。
1. ユーザーのコンピューターに、上記のトークンを使用して、例えばダミーコンテンツを再生するなどして、Expressplayライセンスサーバーにライセンスリクエストを送信するように指示します。

   このダミーライセンスリクエストが成功すると、ユーザーのdevice_id（ユーザーのデバイス上のDRM実装によって計算または生成される）がExpressplayバックエンドのcookieに関連付けられます。 このcookieは次の方法で使用されます。

   * コンテンツの購入時/レンタル時に、コードクエリは関連するcookie([https://www.expressplay.com/developer/restapi/#record-retrieval](https://www.expressplay.com/developer/restapi/#record-retrieval))を送信することで、ユーザーのdevice_idに対して式がバックエンドを再生します。
   * 購入したコンテンツのキー(CEK)、keyID(CEKSID)、ポリシー、その他の情報と共に、`cookie`相関パラメーターと`deviceid`トークン制限パラメーターのそれぞれに上記のcookieとdevice_idを割り当てて、トークン生成リクエストを送信します。

   * このトークンをユーザーに提供します。

      このプロセスは、ユーザーのdevice_idにバインドされたコンテンツのトークンを生成します。 ユーザーのマシンがこのトークンを持つライセンスリクエストを送信すると、Expressplayバックエンドは、トークンのdevice_idとライセンスリクエストのdevice_idをクロスチェックします。

      このワークフローは、サンプルのExpressplayエンタイトルメントサーバーによって実装されます。
