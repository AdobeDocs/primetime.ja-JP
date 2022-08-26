---
title: ユーザーメタデータ
description: ユーザーメタデータ
source-git-commit: 49d5d8c1de263bd63db642d71a5bbb926fa45f96
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# ユーザーメタデータ {#user-metadata}

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

認証済みユーザーに関して MVPD が共有したメタデータを取得します。

<div>


| エンドポイント | 呼び出し済み  </br>作成者 | 入力   </br>パラメーター | HTTP  </br>メソッド | 応答 | HTTP  </br>応答 |
| --- | --- | --- | --- | --- | --- |
| &lt;sp_fqdn>/api/v1/tokens/usermetadata | ストリーミングアプリ</br></br>または</br></br>プログラマーサービス | 1.要求者</br>2.  deviceId（必須）</br>3.  device_info/X-Device-Info （必須）</br>4.  deviceType</br>5.  deviceUser （非推奨）</br>6.  appId （非推奨） | GET | 失敗した場合は、ユーザーメタデータまたはエラーの詳細を含む XML または JSON。 | 200 — 成功</br></br>404 — メタデータが見つかりません</br></br>412 — 無効な AuthN トークン（期限切れのトークンなど） |


| 入力パラメーター | 説明 |
| --- | --- |
| 要求者 | この操作が有効な ProgrammerRequestorId。 |
| deviceId | デバイス ID バイト。 |
| device_info/</br></br>X-Device-Info | デバイス情報のストリーミング。</br></br>**注意**:この INFO は URL パラメータとして渡すことができますが、このパラメータの潜在的なサイズとGETURL の長さの制限により、HTTP ヘッダーで X-Device-Info として渡す必要があります。 </br></br>詳しくは、 [デバイスと接続情報を渡す](http://tve.helpdocsonline.com/passing-device-information). |
| _deviceType_ | デバイスタイプ（Roku、PC など）。</br></br>このパラメータが正しく設定されている場合、ESM は以下の指標を提供します。 [デバイスタイプ別に分類](http://tve.helpdocsonline.com/esm-overview$clientless_device_type) クライアントレスを使用する場合に、Roku、AppleTV、Xbox など、様々な種類の分析を実行できます。</br></br>http://tve.helpdocsonline.com/clientless-device-type-benefits-on-pass-metrics </br></br>**注意**:device_info はこのパラメータを置き換えます。 |
| _deviceUser_ | デバイスのユーザー識別子。</br></br>**注意**：使用する場合、deviceUser は [登録コードを作成](http://tve.helpdocsonline.com/registration-code-request) リクエスト。 |
| _appId_ | アプリケーション ID/名前。 </br></br>**注意**:device_info は、このパラメータを置き換えます。 使用する場合、 `appId` は、 [登録コードを作成](http://tve.helpdocsonline.com/create-registration-page-/-login-uri) リクエスト。 |

>[!NOTE]
> 
>ユーザーメタデータ情報は、認証フローの完了後に使用できる必要がありますが、MVPD やメタデータタイプに応じて、認証フローで更新できます。

</br>

## レスポンスのサンプル {#sample-response}

呼び出しが成功すると、サーバーは、以下に示す構造と同じ構造の XML（デフォルト）または JSON オブジェクトで応答します。

```JSON
    {
        updated: 1334243471,
        encrypted: ["encryptedProp"],
        data: {
              zip: ["12345", "34567"],
              maxRating: { 
                  "MPAA": "PG-13",
                  "VCHIP": "TV-Y", 
                  "URL": "http://exam.pl/e/manage/ratings"
              },
              householdID: "3456",
              userID: "BgSdasfsdk23/dsaf3+saASesadgfsShggssd=",
              channelID: ["channel-1", "channel-2"]
    }
```

 

オブジェクトのルートには、次の 3 つのノードがあります。

* *更新済み*:メタデータが最後に更新された時刻を表す UNIX タイムスタンプを指定します。 このプロパティは、認証フェーズでメタデータを生成する際に、サーバーによって最初に設定されます。 以降の呼び出し（メタデータの更新後）では、タイムスタンプが増分されます。

* *データ*:には、実際のメタデータ値が含まれます。 

* *暗号化*:暗号化されたプロパティをリストする配列です。 特定のメタデータ値を復号するには、プログラマは、メタデータに対して Base64 デコードを実行し、その結果の値に対して RSA 復号を適用する必要があります (Adobeは、プログラマの公開証明書を使用してサーバ上のメタデータを暗号化します )。

エラーが発生した場合、サーバーは詳細なエラーメッセージを指定する XML または JSON オブジェクトを返します。

**詳細情報：** [ユーザーメタデータ](http://tve.helpdocsonline.com/user-metadata-v2)


### [REST API リファレンスに戻る](http://tve.helpdocsonline.com/rest-api-reference)
