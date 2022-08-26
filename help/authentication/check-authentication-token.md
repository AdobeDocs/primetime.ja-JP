---
title: 認証トークンを確認
description: 認証トークンを確認
source-git-commit: 49d5d8c1de263bd63db642d71a5bbb926fa45f96
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---


# 認証トークンを確認 {#check-authentication-token}

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

デバイスに期限切れでない認証トークンがあるかどうかを示します。

| エンドポイント | 呼び出し済み  </br>作成者 | 入力   </br>パラメーター | HTTP  </br>メソッド | 応答 | HTTP  </br>応答 |
| --- | --- | --- | --- | --- | --- |
| &lt;sp_fqdn>/api/v1/checkauthn | ストリーミングアプリ</br></br>または</br></br>プログラマーサービス | 1.requestor （必須）</br>2.  deviceId（必須）</br>3.  device_info/X-Device-Info （必須）</br>4.  _deviceType_ </br>5.  _deviceUser_ （廃止）</br>6.  _appId_ （廃止） | GET | 失敗した場合は、エラーの詳細を含む XML または JSON。 | 200 — 成功   </br>403 — 成功なし |

{style=&quot;table-layout:auto&quot;}


| 入力パラメーター | 説明 |
| --- | --- |
| 要求者 | この操作が有効な ProgrammerRequestorId。 |
| deviceId | デバイス ID バイト。 |
| device_info/</br></br>X-Device-Info | デバイス情報のストリーミング。</br></br>**注意**:この INFO は、URL パラメータとして device_info に渡すことができますが、このパラメータの潜在的なサイズと、GETURL の長さに関する制限により、HTTP ヘッダーで X-Device-Info として渡す必要があります。 </br></br>詳しくは、 [デバイスと接続情報を渡す](http://tve.helpdocsonline.com/passing-device-information). |
| _deviceType_ | デバイスタイプ（Roku、PC など）。</br></br>このパラメータが正しく設定されている場合、ESM は以下の指標を提供します。 [デバイスタイプ別に分類](http://tve.helpdocsonline.com/esm-overview$clientless_device_type) クライアントレスを使用する場合に、Roku、AppleTV、Xbox など、様々な種類の分析を実行できます。</br></br>http://tve.helpdocsonline.com/clientless-device-type-benefits-on-pass-metrics </br>**注意**:device_info はこのパラメータを置き換えます。 |
| _deviceUser_ | デバイスのユーザー識別子。 |
| _appId_ | アプリケーション ID/名前。</br>**注意**:device_info は、このパラメータを置き換えます。 |

{style=&quot;table-layout:auto&quot;}


## 応答（失敗した場合） {#response}

```JSON
    <error>
      <status>403</status>
      <message>Authentication token expired</message>
    </error>
```

### [REST API リファレンスに戻る](http://tve.helpdocsonline.com/rest-api-reference)
