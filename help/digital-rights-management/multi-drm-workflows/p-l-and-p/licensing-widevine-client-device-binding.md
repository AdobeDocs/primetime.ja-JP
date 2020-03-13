---
description: 場合によっては、コンテンツを購入またはレンタルする際に、エンドユーザーが複数のデバイスでコンテンツを再生するのを制限したい場合があります。 お客様がExpressplayを使用している場合は、Expressplay APIを使用して、ユーザーのExpressplayトークンをユーザーのコンピューターにバインドすることで、これを行うことができます。
seo-description: 場合によっては、コンテンツを購入またはレンタルする際に、エンドユーザーが複数のデバイスでコンテンツを再生するのを制限したい場合があります。 お客様がExpressplayを使用している場合は、Expressplay APIを使用して、ユーザーのExpressplayトークンをユーザーのコンピューターにバインドすることで、これを行うことができます。
seo-title: デバイスの連結
title: デバイスの連結
uuid: 351fa33c-4226-4ed5-829c-56b563166fec
translation-type: tm+mt
source-git-commit: ed1430bdcb590a53fa69b324ef340ad636b2fa7c

---


# デバイスの連結{#device-binding}

場合によっては、コンテンツを購入またはレンタルする際に、エンドユーザーが複数のデバイスでコンテンツを再生するのを制限したい場合があります。 お客様がExpressplayを使用している場合は、Expressplay APIを使用して、ユーザーのExpressplayトークンをユーザーのコンピューターにバインドすることで、これを行うことができます。

APIは次の方法で使用できます。

1. cookieを生成します。
1. 生成されたcookieをクエリ文字列(cookie=`<cookie>`)またはヘッダーとして添付して、ダミーのトークン生成リクエストを送信します。
1. 例えば、ダミーコンテンツを再生することで、ユーザーのマシンから上記のトークンを使用してExpressplayライセンスサーバーにライセンスリクエストを送信するようにします。

   このダミーのライセンスリクエストが成功すると、ユーザーのdevice_id（ユーザーのデバイス上のDRM実装によって計算または生成される）がExpressplayバックエンドのcookieに関連付けられます。 このcookieは次の方法で使用されます。

   * コンテンツの購入時/レンタル時に、コードは関連するcookie( https://www.expressplay.com/developer/restapi/#record-retrieval [](https://www.expressplay.com/developer/restapi/#record-retrieval))を送信することで、ExpressPlayのバックエンドでユーザーのdevice_idを照会します。
   * 購入したコンテンツのキー(CEK)、keyID(CEKSID)、ポリシー、その他の情報を含むトークン生成リクエストを送信し、上記のcookieとdevice_idをそれぞれ相関パラメーターとトークン制限パラメーターとして添付し `cookie``deviceid` ます。

   * このトークンをユーザーに提供します。

      このプロセスは、ユーザーのdevice_idにバインドされたコンテンツのトークンを生成します。 ユーザーのマシンがこのトークンを使用してライセンスリクエストを送信すると、Expressplayバックエンドは、トークンのdevice_idとライセンスリクエストのdevice_idをクロスチェックします。

      このワークフローは、サンプルのExpressPlayエンタイトルメントサーバーによって実装されます。
