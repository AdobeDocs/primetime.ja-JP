---
title: REST API リファレンス
description: Rest api リファレンス
source-git-commit: 4c3a0dd56b4ef99ac8c57cfde61f792088b0ff4d
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# REST API リファレンス {#rest-api-reference}

>[!NOTE]
>
>このページのコンテンツは、情報提供の目的でのみ提供されます。 この API を使用するには、Adobeの現在のライセンスが必要です。 不正な使用は許可されていません。

## 応答形式 {#response-formats}


>[!NOTE]
>
> これらのサービスで提供される API は、XML または JSON（応答を返す API の場合）で応答を返すことができます。 リクエストで応答形式を指定する方法は 3 つあります。
>* HTTP Accept ヘッダーを&quot;application/xml&quot;に設定します。</code>&quot;または&quot;application/json</code>&quot;
>* リクエストペイロードで、「format=xml」というパラメーターを指定します。</code>&quot;または&quot;format=json</code>&quot;</li>
>* 拡張子.xml を使用して Web サービスエンドポイントを呼び出す</code> または.json</code>. 例： &quot;/regcode.xml</code>&quot;または&quot;/regcode.json&quot;</code>&quot;
>
>上記のメソッドのいずれかを指定できます。 形式が競合する複数のメソッドを指定すると、エラーや望ましくない出力が発生する場合があります。

## REST API エンドポイント {#clientless-endpoints}

&lt;reggie_fqdn>:

* 実稼動 — [api.auth.adobe.com](http://api.auth.adobe.com/)
* ステージング — [api.auth-staging.adobe.com](http://api.auth-staging.adobe.com/)

&lt;sp_fqdn>:

* 実稼動 — [api.auth.adobe.com](http://api.auth.adobe.com/)
* ステージング — [api.auth-staging.adobe.com](http://api.auth-staging.adobe.com/)

</br>


## Web サービスの概要 {#web_srvs_summary}

次の表に、クライアントレスアプローチで使用可能な Web サービスを示します。 詳しくは、Web サービスエンドポイントをクリックしてください（リクエストと応答、入力パラメーター、HTTP メソッドなど）。


| Sr | Web サービスエンドポイント | 説明 | [診断。  </br>参照](http://tve.helpdocsonline.com/api-reference-v2-test#illustration). | ホスト時刻 | 呼び出し元 |
| --- | --- | --- | --- | --- | --- |
| 1. | [&lt;reggie_fqdn>/reggie/v1/  </br>  {requestorId}/regcode](http://tve.helpdocsonline.com/registration-code-request) | ランダムに生成された登録コードとログインページの URI を返します | 2 | Adobe  </br>Reg Code Service | スマートデバイス |
| 2. | [&lt;reggie_fqdn>/reggie/v1/  </br>  {requestorId}/regcode/  </br>  {registrationCode}](http://tve.helpdocsonline.com/return-registration-record) | 登録コード UUID、登録コード、ハッシュ化されたデバイス ID を含む登録コードレコードを返します | 8 | Adobe  </br>Reg Code Service | Primetime 認証 |
| 3. | [&lt;sp_fqdn>/api/v1/config/  </br>  {requestorId}](http://tve.helpdocsonline.com/provide-mvpd-list) | リクエスト元の設定済み MVPD のリストを返します | 5 | Adobe  </br>Primetime  </br>認証  </br>サービス | ログイン  </br>Web  </br>アプリ |
| 4. | [&lt;sp_fqdn>/api/v1/authenticate](http://tve.helpdocsonline.com/initiate-authentication) | MVPD 選択イベントを通知して AuthN プロセスを開始します。 認証データベースにレコードを作成します。このレコードは、MVPD から正常な応答を受け取ったときに紐付けされます（手順 13）。 | 7 | Adobe  </br>Primetime  </br>認証  </br>サービス | ログイン  </br>Web  </br>アプリ |
| 5. | SAML アサーションコンシューマ | Primetime 認証と MVPD 間の既存の SAML ワークフロー | 13 | Primetime  </br>認証  </br>サービス | Primetime 認証 |
| 6. | [&lt;sp_fqdn>/api/v1/checkauthn/  </br>  {registrationCode}](http://tve.helpdocsonline.com/check-authentication-flow-by-second-screen-web-app) | ログイン Web アプリは、試行されたログインフローが成功したかどうかを確認できます |  | Primetime  </br>認証   </br>サービス | ログイン   </br>Web   </br>アプリ |
| 7. | [&lt;sp_fqdn>/api/v1/tokens/authn](http://tve.helpdocsonline.com/rest-api-retrieve-authentication-token) | AuthN トークン関連のメタデータを取得します | 15 | Primetime  </br>認証  </br>サービス | スマートデバイス |
| 8. | [&lt;reggie_fqdn>/reggie/v1/  </br>  {requestorId}/regcode/  </br>  {registrationCode}](http://tve.helpdocsonline.com/delete-registration-record) | reg コードレコードを削除し、reg コードを解放して再利用します | 16 | Adobe  </br>Reg Code Service | Primetime 認証 |
| 9. | [&lt;sp_fqdn>/api/v1/authorize](http://tve.helpdocsonline.com/initiate-authorization) | 承認応答を取得します。 | 17 | Primetime  </br>認証  </br>サービス | スマートデバイス |
| 10. | [&lt;sp_fqdn>/api/v1/checkauthn](http://tve.helpdocsonline.com/check-authentication-token) | デバイスに期限切れでない AuthN トークンがあるかどうかを示します。 |  | Primetime  </br>認証  </br>サービス | スマートデバイス |
| 11. | [&lt;sp_fqdn>/api/v1/tokens/authn](http://tve.helpdocsonline.com/rest-api-retrieve-authentication-token) | AuthN トークンが見つかった場合は、そのトークンを返します。 |  | Primetime  </br>認証  </br>サービス | スマートデバイス |
| 12. | [&lt;sp_fqdn>/api/v1/tokens/authz](http://tve.helpdocsonline.com/retrieve-authorization-token) | AuthZ トークンが見つかった場合は、そのトークンを返します。 |  | Primetime  </br>認証  </br>サービス | スマートデバイス |
| 13. | [&lt;sp_fqdn>/api/v1/tokens/media](http://tve.helpdocsonline.com/obtain-short-media-token) | 見つかった場合、Short Media トークンを返します（/api/v1/mediatoken と同じ） |  | Primetime  </br>認証  </br>サービス | スマートデバイス |
| 14. | [&lt;sp_fqdn>/api/v1/mediatoken](http://tve.helpdocsonline.com/obtain-short-media-token) | ショートメディアトークンを取得 |  | Primetime  </br>認証  </br>サービス | スマートデバイス |
| 15. | [&lt;sp_fqdn>/api/v1/preauthorize](http://tve.helpdocsonline.com/retrieve-list-of-preauthorized-resources) | 事前に認証されたリソースのリストを取得します |  | Primetime  </br>認証  </br>サービス | スマートデバイス |
| 16. | [&lt;sp_fqdn>/api/v1/preauthorize/{code}](http://tve.helpdocsonline.com/retrieve-list-of-preauthorized-resources-by-way-of-web-app) | 事前に認証されたリソースのリストを取得します |  | Primetime  </br>認証  </br>サービス | Web アプリにログイン |
| 17. | [&lt;sp_fqdn>/api/v1/logout](http://tve.helpdocsonline.com/logout) | ストレージから AuthN および AuthZ トークンを削除 |  | Primetime  </br>認証   </br>サービス | スマートデバイス |
| 18. | [&lt;sp_fqdn>/api/v1/tokens/usermetadata](http://tve.helpdocsonline.com/user-metadata-call) | 認証フローの完了後にユーザーメタデータを取得する | 該当なし | 該当なし | スマートデバイス |
| 19. | [&lt;sp_fqdn>/api/v1/authenticate/freepreview](http://tve.helpdocsonline.com/free-preview-for-temp-pass-and-promotional-temp-pass) | 一時パスまたはプロモーション一時パスの認証トークンを作成する | 該当なし | Primetime  </br>認証  </br>サービス | スマートデバイス |

{style=&quot;table-layout:auto&quot;}

## REST API セキュリティ {#security}

安全な通信を実現するために、すべての Primetime 認証クライアントレス API は、HTTPS プロトコルを使用して呼び出す必要があります。 さらに、呼び出される API のほとんどには、 [動的クライアントの登録](http://tve.helpdocsonline.com/dynamic-client-registration).


## 関連情報 {#related}

* [REST API の概要](http://tve.helpdocsonline.com/reset-api-overview)
* [サーバー間クックブック](http://tve.helpdocsonline.com/server-to-server-cookbook)
* [クライアント/サーバー間クックブック](http://tve.helpdocsonline.com/client-to-server)
* [/authenticate request で&#39;&amp;&#39;reg\_code を使用しない（テクニカルノート）](https://tve.zendesk.com/entries/23648011-Clientless-Avoid-using-reg-code-in-authenticate-request)
