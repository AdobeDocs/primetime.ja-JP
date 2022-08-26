---
title: 事前に認証されたリソースのリストを取得
description: 事前に認証されたリソースのリストを取得
source-git-commit: 49d5d8c1de263bd63db642d71a5bbb926fa45f96
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---


# 事前に認証されたリソースのリストを取得 {#retrieve-list-of-preauthorized-resources}

>[!NOTE]
>
>このページのコンテンツは、情報提供の目的でのみ提供されます。 この API を使用するには、Adobeの現在のライセンスが必要です。 不正な使用は許可されていません。

## REST API エンドポイント {#clientless-endpoints}

&lt;reggie_fqdn>:

* 実稼動 — [api.auth.adobe.com](http://api.auth.adobe.com/)
* ステージング — [api.auth-staging.adobe.com](http://api.auth-staging.adobe.com/)

&lt;sp_fqdn>:

* 実稼動 — [api.auth.adobe.com](http://api.auth.adobe.com/)
* ステージング — [api.auth-staging.adobe.com](http://api.auth-staging.adobe.com/)

</br>

## 説明 {#description}

事前に認証されたリソースのリストを取得するためのAdobe Primetime認証へのリクエスト。

API には次の 2 つのセットがあります。1 つはストリーミングアプリまたはプログラマーサービス用のセットで、もう 1 つは 2 つ目のスクリーン Web アプリ用のセットです。 このページでは、ストリーミングアプリまたはプログラマーサービス用の API について説明します。


| エンドポイント | 呼び出し済み  </br>作成者 | 入力   </br>パラメーター | HTTP  </br>メソッド | 応答 | HTTP  </br>応答 |
| --- | --- | --- | --- | --- | --- |
| &lt;sp_fqdn>/api/v1/preauthorize | ストリーミングアプリ</br></br>または</br></br>プログラマーサービス | 1.requestor （必須）</br>2.  deviceId（必須）</br>3.  リソースリスト（必須）</br>4.  device_info/X-Device-Info （必須）</br>5.  _deviceType_</br> 6.  _deviceUser_ （廃止）</br>7.  _appId_ （廃止） | GET | 個々の事前認証の決定またはエラーの詳細を含む XML または JSON。 以下のサンプルを参照してください。 | 200 — 成功</br></br>400 — 無効なリクエスト</br></br>401 — 未認証</br></br>405 — 許可されていないメソッド  </br></br>412 — 事前条件に失敗しました</br></br>500 — 内部サーバーエラー |


| 入力パラメーター | 説明 |
| --- | --- |
| 要求者 | この操作が有効な ProgrammerRequestorId。 |
| deviceId | デバイス ID バイト。 |
| リソースリスト | ユーザーがアクセス可能なコンテンツを識別し、MVPD 認証エンドポイントによって認識される resourceIds のコンマ区切りリストを含む文字列。 |
| device_info/</br></br>X-Device-Info | デバイス情報のストリーミング。</br></br>**注意**:この INFO は URL パラメータとして渡すことができますが、このパラメータの潜在的なサイズとGETURL の長さの制限により、HTTP ヘッダーで X-Device-Info として渡す必要があります。 </br></br>詳しくは、 [デバイスと接続情報を渡す](http://tve.helpdocsonline.com/passing-device-information). |
| _deviceType_ | デバイスタイプ（Roku、PC など）。</br></br>このパラメータが正しく設定されている場合、ESM は以下の指標を提供します。 [デバイスタイプ別に分類](http://tve.helpdocsonline.com/esm-overview$clientless_device_type) クライアントレスを使用する場合に、Roku、AppleTV、Xbox など、様々な種類の分析を実行できます。</br></br>http://tve.helpdocsonline.com/clientless-device-type-benefits-on-pass-metrics </br></br>**注意**:device_info はこのパラメータを置き換えます。 |
| _deviceUser_ | デバイスのユーザー識別子。 |
| _appId_ | アプリケーション ID/名前。 </br></br>**注意**:device_info は、このパラメータを置き換えます。 |



### レスポンスのサンプル {#sample-response}

 

**XML:**

```XML
HTTP/1.1 200 OK
Adobe-Request-Id : 7af28ec2-a068-45c2-8009-f5443049baf4
Adobe-Response-Confidence : full
Content-Type: application/xml; charset=utf-8

<resources>
  <resource>
    <id>TestStream1</id>
    <authorized>true</authorized>
  </resource>
  <resource>
    <id>TestStream2</id>
    <authorized>false</authorized>
    <error>
      <status>403</status>
      <code>authorization_denied_by_mvpd</code>
      <message>User not authorized</message>
      <details>Your subscription package does not include the "TestStream3" channel.</details>
      <helpUrl>https://tve.helpdocsonline.com/errors/preauthorization_denied</helpUrl>
      <trace>0453f8c8-167a-4429-8784-cd32cfeaee58</trace>
      <action>none</action>
    </error>
  </resource>
</resources>
```
 
</br>

**JSON:**

```JSON
HTTP/1.1 200 OK
Adobe-Request-Id : 7af28ec2-a068-45c2-8009-f5443049baf4
Adobe-Response-Confidence : full
Content-Type: application/json; charset=utf-8
 
{
   "resources" : [
        {
            "id" : "TestStream1",
            "authorized" : true
        },
        {
            "id" : "TestStream3",
            "authorized" : false,
            "error" : {
               "status" : 403,
               "code" : "authorization_denied_by_mvpd",
               "message" : "User not authorized",
               "details" : "Your subscription package does not include the "TestStream3" channel.",
               "helpUrl" : "https://tve.helpdocsonline.com/errors/preauthorization_denied",
               "trace" : "0453f8c8-167a-4429-8784-cd32cfeaee58",
               "action" : "none"
            }
        } 
    ]
}
```


### [REST API リファレンスに戻る](http://tve.helpdocsonline.com/rest-api-reference)
