---
title: 登録レコードを削除
description: 登録リソースを削除
source-git-commit: 0839e9f2eac7eeeadf9bbfafb2bdd76596f4fb06
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# 登録レコードを削除 {#delete-registration-record}

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


## 説明 {#delete-record}

reg コードレコードを削除し、再利用のために reg コードを解放します。 

| エンドポイント | 呼び出し済み  </br>作成者 | 入力   </br>パラメーター | HTTP  </br>メソッド | 応答 | HTTP  </br>応答 |
| --- | --- | --- | --- | --- | --- |
| &lt;reggie_fqdn>/reggie/v1/{requestorId}/regcode/{registrationCode}</br></br>例：</br></br>&lt;reggie_fqdn>/reggie/v1/regcode/ER45RTY | ストリーミングアプリ</br></br>または</br></br>プログラマーサービス | 1.要求者 ID  </br>    （パスコンポーネント）</br>2.  登録コード  </br>    （パスコンポーネント） | DELETE | なし | 204 |

{style=&quot;table-layout:auto&quot;}

</br>

| 入力パラメーター | 説明 |
| --- | --- |
| 要求者 | この操作が有効な ProgrammerRequestorId。 |
| 登録コード | ストリーミングデバイスに表示される登録コード値（認証フローに入力される値）です。 |

{style=&quot;table-layout:auto&quot;}

</br>

### [REST API リファレンスに戻る](http://tve.helpdocsonline.com/rest-api-reference)
