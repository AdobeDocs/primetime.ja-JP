---
title: 認証の開始
description: 認証の開始
source-git-commit: 0839e9f2eac7eeeadf9bbfafb2bdd76596f4fb06
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 認証の開始 {#initiate-authentication}

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

MVPD 選択イベントを通知することで、認証プロセスを開始します。 Primetime 認証データベースにレコードを作成します。このレコードは、MVPD から正常な応答を受け取ったときに紐付けされます。 



| エンドポイント | 呼び出し済み  </br>作成者 | 入力   </br>パラメーター | HTTP  </br>メソッド | 応答 | HTTP  </br>応答 |
| --- | --- | --- | --- | --- | --- |
| &lt;sp_fqdn>/api/v1/authenticate | AuthN モジュール | 1.requestor_id（必須）</br>2.  mso_id（必須）</br>3.  reg_code（必須）</br>4.  domain_name（必須）</br>5.  noflash=true -  </br>    （必須、残余パラメータ）</br>6.  no_iframe=true（必須、残差パラメータ）</br>7.  追加のパラメーター（オプション）</br>8.  redirect_url（必須） | GET | Login Web App が MVPD ログインページにリダイレクトされます。 | 完全なリダイレクト実装の場合は 302 |

{style=&quot;table-layout:auto&quot;}


| 入力パラメーター | 説明 |
| --- | --- |
| requestor_id | この操作が有効なプログラマーリクエスト元。 |
| mso_id | この操作が有効な MVPD ID です。 |
| reg_code | Reggie サービスによって生成された登録コード。 |
| domain_name | 元のドメイン。 |
| redirect_url | 認証完了後のログイン Web アプリのリダイレクト URL。 |

{style=&quot;table-layout:auto&quot;}

</br>

>[!IMPORTANT]
> 
>**重要：必須のパラメーター —** クライアント側の実装に関係なく、上記のすべてのパラメーターは必須です。
>
>
>例：    
>
>
```
>domain_name=loginwebapp.com
>mso_id=sampleMvpdId
>reg_code=RO0885W
>requestor_id=sampleRequestorId
>noflash=true
>redirect_url=http://loginwebapp.com
>```

>[!IMPORTANT]
> 
>**重要：オプションのパラメーター**
>
>また、呼び出しには、次のような他の機能を有効にするオプションのパラメーターを含めることができます。
>
> * generic\_data - [プロモーション TempPass](https://tve.helpdocsonline.com/promotional-temp-pass)
>
>```JSON
>Example:
>   generic_data=("email":"email@domain.com")
>```


### **メモ** {#notes}

* の値 `domain_name` パラメーターは、Primetime 認証で登録されているドメイン名の 1 つに設定する必要があります。 詳しくは、 [登録と初期化](http://tve.helpdocsonline.com/new-programmer-overview$reg_and_init).

* [/authenticate request で&#39;&amp;&#39;reg\_code を使用しない（テクニカルノート）](https://tve.helpdocsonline.com/clientless:-avoid-using-&#39;&amp;&#39;reg_code-in-/authenticate-request)

* この `redirect_url` パラメーターは、順序の最後のパラメーターである必要があります

* の値 `redirect_url` パラメーターは URL エンコードされている必要があります

[REST API リファレンスに戻る](http://tve.helpdocsonline.com/rest-api-reference)