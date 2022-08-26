---
title: ショートメディアトークンの取得
description: ショートメディアトークンを取得する
source-git-commit: 0839e9f2eac7eeeadf9bbfafb2bdd76596f4fb06
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---


# ショートメディアトークンの取得 {#obtain-short-media-token}

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

ショートメディアトークンを取得します。  

| エンドポイント | 呼び出し済み  </br>作成者 | 入力   </br>パラメーター | HTTP  </br>メソッド | 応答 | HTTP  </br>応答 |
| --- | --- | --- | --- | --- | --- |
| &lt;sp_fqdn>/api/v1/mediatoken</br></br>  または</br></br>&lt;sp_fqdn>/api/v1/tokens/media</br></br>例：</br></br>&lt;sp_fqdn>/api/v1/tokens/media | ストリーミングアプリ</br></br>または</br></br>プログラマーサービス | 1.requestor （必須）</br>2.  deviceId（必須）</br>3.  resource （必須）</br>4.  device_info/X-Device-Info （必須）</br>5.  _deviceType_</br> 6.  _deviceUser_ （廃止）</br>7.  _appId_ （廃止） | GET | Base64 エンコードされたメディアトークンを含む XML または JSON、失敗した場合はエラーの詳細。 | 200 — 成功  </br>403 — 成功なし |

{style=&quot;table-layout:auto&quot;}

<!--
| Endpoint | Called  </br>By | Input   </br>Params | HTTP  </br>Method | Response | HTTP  </br>Response |
| --- | --- | --- | --- | --- | --- |
| `<SP_FQDN>/api/v1/mediatoken`</br></br>  or</br></br>`<SP_FQDN>/api/v1/tokens/media`</br></br>For example:</br></br>`<SP_FQDN>/api/v1/tokens/media` | Streaming App</br></br>or</br></br>Programmer Service | <ol><li>requestor (Mandatory)</l><li>deviceId (Mandatory)</li><li>resource (Mandatory)</li><li>device_info/X-Device-Info (Mandatory)</li><li>_deviceType_</li><li>_deviceUser_ (Deprecated)</li><li>_appId_ (Deprecated)</li></ol> | GET | XML or JSON containing an Base64 encoded media token or error details if unsuccessful. | 200 - Success  </br>403 - No Success |
-->

</br>

| 入力パラメーター | 説明 |
| --- | --- |
| 要求者 | この操作が有効な ProgrammerRequestorId。 |
| deviceId | デバイス ID バイト。 |
| リソース | resourceId（または MRSS フラグメント）を含む文字列。ユーザーが要求したコンテンツを識別し、MVPD 認証エンドポイントによって認識されます。 |
| device_info/</br></br>X-Device-Info | デバイス情報のストリーミング。</br></br>**注意**:この INFO は URL パラメータとして渡すことができますが、このパラメータの潜在的なサイズとGETURL の長さの制限により、HTTP ヘッダーで X-Device-Info として渡す必要があります。 </br></br>詳しくは、 [デバイスと接続情報を渡す](http://tve.helpdocsonline.com/passing-device-information). |
| _deviceType_ | デバイスタイプ（Roku、PC など）。</br></br>このパラメータが正しく設定されている場合、ESM は以下の指標を提供します。 [デバイスタイプ別に分類](http://tve.helpdocsonline.com/esm-overview$clientless_device_type) クライアントレスを使用する場合に、Roku、AppleTV、Xbox など、様々な種類の分析を実行できます。</br></br>http://tve.helpdocsonline.com/clientless-device-type-benefits-on-pass-metrics </br></br>**注意**:device_info はこのパラメータを置き換えます。 |
| _deviceUser_ | デバイスのユーザー識別子。</br></br>**注意**：使用する場合、deviceUser は [登録コードを作成](http://tve.helpdocsonline.com/registration-code-request) リクエスト。 |
| _appId_ | アプリケーション ID/名前。 </br></br>**注意**:device_info は、このパラメータを置き換えます。 使用する場合、 `appId` は、 [登録コードを作成](http://tve.helpdocsonline.com/create-registration-page-/-login-uri) リクエスト。 |

{style=&quot;table-layout:auto&quot;}

### レスポンスのサンプル {#response}

**XML:**

```XML
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <play>
        <expires>1348649569000</expires>
        <mvpdId>sampleMvpdId</mvpdId>
        <requestor>sampleRequestorId</requestor>
        <resource>sampleResourceId</resource>
        <serializedToken>PHNpZ25hdH[...]</serializedToken>
        <userId>sampleScrambledUserId</userId>
    </play>
```



**JSON:**

```JSON
    {
        "resource": "sampleResourceId",
        "requestor": "sampleRequestorId",
        "expires": "1348649614000",
        "serializedToken": "PHNpZ25hdH[...]",
        "userId": "sampleScrambledUserId",
        "mvpdId": "sampleMvpdId"
    }
```

 

### Media Verification Library の互換性

フィールド `serializedToken` 「Obtain Short Media Token」呼び出しからの Base64 エンコードされたトークンは、Adobe Medium検証ライブラリと照合して検証できます。

[REST API リファレンスに戻る](http://tve.helpdocsonline.com/rest-api-reference)
