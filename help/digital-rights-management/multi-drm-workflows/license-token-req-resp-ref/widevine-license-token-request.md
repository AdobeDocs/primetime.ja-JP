---
description: Widevine ライセンストークンインターフェイスは、実稼動およびテストサービスを提供します。
title: Widevine ライセンストークンリクエスト/レスポンス
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '858'
ht-degree: 5%

---

# Widevine ライセンストークンリクエスト/レスポンス {#widevine-license-token-request-response}

Widevine ライセンストークンインターフェイスは、実稼動およびテストサービスを提供します。

この HTTP リクエストは、Widevine ライセンスに交換できるトークンを返します。

**メソッド：GET、POST** （www-url-encoded の本文には、両方のメソッドのパラメータが含まれています）

**URL:**

* **実稼動：** `https://wv-gen.{prod_domain}/hms/wv/token`

* **テスト：** ` [https://wv-gen.test.expressplay.com/hms/wv/token](https://wv-gen.test.expressplay.com/hms/wv/token)`

* **リクエストの例：**

  ```
  https://wv-gen.service.expressplay.com/hms/wv/token?customerAuthenticator= 
  <ExpressPlay customer authenticator identifier>
  ```

* **レスポンスのサンプル：**

  ```
  https://wv.service.expressplay.com/hms/wv/rights/?ExpressPlayToken=<base64-encoded ExpressPlay token>
  ```

<!--<a id="section_1E22012EE4B94BB2974D3B16DE8812D9"></a>-->

**表 13：トークン・クエリー・パラメータ**

<table id="table_ww1_hcs_pv">  
 <thead> 
  <tr> 
   <th class="entry"> <b>クエリパラメーター</b> </th> 
   <th class="entry"> <b>説明</b> </th> 
   <th class="entry"> <b>必須？</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td> <span class="codeph"> customerAuthenticator </span> </td> 
   <td> <p>これは、実稼動環境とテスト環境用に 1 つずつ、顧客 API キーです。 これは、「 ExpressPlay Admin Dashboard 」タブで確認できます。 </p> </td> 
   <td> はい </td> 
  </tr> 
  <tr> 
   <td> <span class="codeph"> errorFormat </span> </td> 
   <td> 次のいずれか <span class="codeph"> html </span> または <span class="codeph"> json </span>. <p>次の場合 <span class="codeph"> html </span> （デフォルト）HTMLのエラー表現は、応答のエンティティ本文に表示されます。 次の場合 <span class="codeph"> json </span> が指定されている場合、JSON 形式の構造化された応答が返されます。 詳しくは、 <a href="https://www.expressplay.com/developer/restapi/#json-errors" format="html" scope="external"> JSON エラー </a> 」を参照してください。 </p> <p>応答の MIME タイプは、 <span class="codeph"> text/uri-list </span> 成功して <span class="codeph"> text/html </span> 対象： <span class="codeph"> html </span> エラーフォーマット、または <span class="codeph"> application/json </span> 対象： <span class="codeph"> json </span> エラーフォーマット。 </p> </td> 
   <td> いいえ </td> 
  </tr> 
 </tbody> 
</table>

**表 14：ライセンス・クエリー・パラメータ**

| クエリパラメーター | 説明 | 必須？ |
|--- |--- |--- |
| `generalFlags` | ライセンスフラグを表す 4 バイトの 16 進文字列。 許可されている値は「0000」のみです | いいえ |
| `kek` | キー暗号化キー (KEK)。 キーは、キーラッピングアルゴリズム（AES キーラップ、RFC3394）を使用して、KEK で暗号化されて格納されます。 | いいえ |
| `kid` | コンテンツ暗号化キーまたは文字列の 16 バイトの 16 進文字列表現です `^somestring'`. 文字列の長さの後に `^` は 64 文字以下にする必要があります。 例については、以下のメモを確認してください。 | はい |
| `ek` | 暗号化されたコンテンツキーの 16 進文字列表現です。 | いいえ |
| `contentKey` | コンテンツ暗号化キーの 16 バイトの 16 進文字列表現 | はい、ただし `kek` および `ek` または `kid` が指定されている |
| `contentId` | コンテンツ ID | いいえ |
| `securityLevel` | 使用できる値は 1 ～ 5 です。 <ul><li>1 = `SW_SECURE_CRYPTO`</li><li> 2 = `SW_SECURE_DECODE` </li><li> 3 = `HW_SECURE_CRYPTO` </li><li> 4 = `HW_SECURE_DECODE` </li><li> 5 = `HW_SECURE_ALL`</li></ul> | はい |
| `hdcpOutputControl` | 使用できる値は 0、1、2 です。 <ul><li>0 = `HDCP_NONE` </li><li> 1 = `HDCP_V1` </li><li> 2 = `HDCP_V2`</li></ul> | はい |
| `licenseDuration` * | ライセンスの期間（秒）。 指定されていない場合は、期間に制限がないことを示します。 詳細は、以下のメモを確認してください。 | いいえ |
| `wvExtension` | extensionType と extensionPayload をコンマ区切りの文字列としてラッピングした短い形式です。 以下の形式を参照してください。 例： `…&wvExtension=wudo,AAAAAA==&…` | いいえ、任意の数を使用できます |

について `licenseDuration`: <ol><li> 再生が停止します `licenseDuration` 再生開始後の秒数。 </li><li> 再生を無制限の時間に停止/再開できるようにするには、を省略します。 `licenseDuration` （デフォルトでは無限に設定されます）。 それ以外の場合は、エンドユーザーがストリームを楽しめる時間を指定します。 </li></ol>

**表 15：トークン制限クエリー・パラメータ**

| クエリパラメーター | 説明 | 必須？ |
|--- |--- |--- |
| `expirationTime` | このトークンの有効期限。 この値は、 [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt) 「Z」ゾーン指定子（「ズール時間」）での日付/時刻形式、または前に+記号が付いた整数。 RFC 3339 日時の例は2006-04-14T12です:01:10Z <br> 値が [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt) 日付/時刻形式の場合は、トークンの絶対的な有効期限切れの日時を表します。 値が整数の前に+記号が付いた場合、発行からトークンが有効であることを相対秒数として解釈します。 例： `+60` 1 分を指定します。 <br> トークンの有効期間は、最大とデフォルト（指定されていない場合）で 30 日です。 | いいえ |

**表 16：相関クエリー・パラメータ**

| **クエリパラメーター** | **説明** | **必須？** |
|---|---|---|
| `cookie` | 最大 32 文字の任意の文字列。トークンに格納され、トークン交換サーバーによって記録されます。 引き換えサーバーのログエントリと、サービスプロバイダーのサーバーのログエントリを関連付けるために使用できます。 | いいえ |

<!--<a id="section_6BFBD314C77C40C4B172ABBDD2D8D80E"></a>-->

**表 17: HTTP 応答**

| **HTTP ステータスコード** | **説明** | **Content-Type** | **エンティティ本文に次を含む** |
|---|---|---|---|
| `200 OK` | エラーはありません。 | `text/uri-list` | ライセンス取得 URL +トークン |
| `400 Bad Request` | 無効な引数 | `text/html` または `application/json` | エラーの説明 |
| `401 Unauthorized` | 認証に失敗しました | `text/html` または `application/json` | エラーの説明 |
| `404 Not found` | 無効な URL | `text/html` または `application/json` | エラーの説明 |
| `50x Server Error` | サーバーエラー | `text/html` または `application/json` | エラーの説明 |

**表 18：イベントエラーコード**

<table id="table_agj_gqx_pv">  
 <thead> 
  <tr> 
   <th class="entry"> コード </th> 
   <th class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td> -2002 </td> 
   <td> 無効なトークン有効期限： &lt;details&gt; </td> 
  </tr> 
  <tr> 
   <td> -2003 </td> 
   <td> 無効な IP アドレス </td> 
  </tr> 
  <tr> 
   <td> -2005 </td> 
   <td> 無効なコンテンツ暗号化キー： &lt;details&gt; </td> 
  </tr> 
  <tr> 
   <td> -2008 </td> 
   <td> 無効な出力制御フラグが指定されました： &lt;details&gt; </td> 
  </tr> 
  <tr> 
   <td> -2017 </td> 
   <td> 認証トークンを指定する必要があります </td> 
  </tr> 
  <tr> 
   <td> -2018 </td> 
   <td> 認証トークンが無効です： &lt;details&gt; <p>注意：これは、認証子が間違っている場合や、*.test.expressplay.comにあるテスト API に本番用認証子を使用してアクセスする場合、または本番用認証子を使用してテスト API にアクセスする場合に発生する可能性があります。 </p> <p importance="high">注意：テスト SDK と高度なテストツール (ATT) は、 <span class="filepath"> *.test.expressplay.com </span>に対して、実稼動デバイスはを使用する必要があります。 <span class="filepath"> *.service.expressplay.com </span> </p>. </td> 
  </tr> 
  <tr> 
   <td> -2019 </td> 
   <td> 使用可能なトークンが不十分です </td> 
  </tr> 
  <tr> 
   <td> -2022 </td> 
   <td> レンタル期間の終了時間がありません </td> 
  </tr> 
  <tr> 
   <td> -2023 </td> 
   <td> レンタル再生時間がありません </td> 
  </tr> 
  <tr> 
   <td> -2025 </td> 
   <td> 無効なレンタル再生時間 </td> 
  </tr> 
  <tr> 
   <td> -2027 </td> 
   <td> コンテンツ暗号化キーは 32 桁の 16 進数である必要があります </td> 
  </tr> 
  <tr> 
   <td> -2030 </td> 
   <td> ExpressPlay 管理エラー： &lt;details&gt; </td> 
  </tr> 
  <tr> 
   <td> -2031 </td> 
   <td> 無効なサービスアカウント </td> 
  </tr> 
  <tr> 
   <td> -2033 </td> 
   <td> 無効な cookie </td> 
  </tr> 
  <tr> 
   <td> -2034 </td> 
   <td> 無効な出力制御、指定された範囲外の値 </td> 
  </tr> 
  <tr> 
   <td> -2035 </td> 
   <td> 対応する値が指定されていません </td> 
  </tr> 
  <tr> 
   <td> -2036 </td> 
   <td> 拡張子のタイプは 4 文字にする必要があります </td> 
  </tr> 
  <tr> 
   <td> -2037 </td> 
   <td> 拡張機能のペイロードは Base64 エンコードする必要があります </td> 
  </tr> 
  <tr> 
   <td> -2040 </td> 
   <td> <span class="codeph"> OutputControlFlag </span> は、4 バイトでエンコードする必要があります </td> 
  </tr> 
  <tr> 
   <td> -3004 </td> 
   <td> 無効なエラーフォーマットが指定されました： &lt;format&gt; </td> 
  </tr> 
  <tr> 
   <td> -4001 </td> 
   <td> デバイスを認証できませんでした </td> 
  </tr> 
  <tr> 
   <td> -4010 </td> 
   <td> 無効なトークン </td> 
  </tr> 
  <tr> 
   <td> -4018 </td> 
   <td> 見つかりません <span class="filepath"> kid </span> </td> 
  </tr> 
  <tr> 
   <td> -4019 </td> 
   <td> キーストレージサービスからコンテンツキーを取得できませんでした </td> 
  </tr> 
  <tr> 
   <td> -4020 </td> 
   <td> <span class="codeph"> kid </span> は、32 文字の 16 進数である必要があります </td> 
  </tr> 
  <tr> 
   <td> -4021 </td> 
   <td> <span class="codeph"> kid </span> は、「^」の後ろの 64 文字にする必要があります </td> 
  </tr> 
  <tr> 
   <td> -4022 </td> 
   <td> 無効 <span class="codeph"> kid </span> </td> 
  </tr> 
  <tr> 
   <td> -4024 </td> 
   <td> 無効な暗号化キーまたは <span class="codeph"> kek </span> </td> 
  </tr> 
  <tr> 
   <td> -5003 </td> 
   <td> 無効な一般フラグ </td> 
  </tr> 
  <tr> 
   <td> -6005 </td> 
   <td> 無効なキーデータが指定されました </td> 
  </tr> 
  <tr> 
   <td> -6007 </td> 
   <td> 無効なレンタル期間が指定されました </td> 
  </tr> 
  <tr> 
   <td> -7002 </td> 
   <td> デバイス ID のバインディングは Widevine ではサポートされていません </td> 
  </tr> 
  <tr> 
   <td> -7003 </td> 
   <td> セキュリティレベルの値がありません </td> 
  </tr> 
  <tr> 
   <td> -7004 </td> 
   <td> セキュリティレベルの値が無効です </td> 
  </tr> 
  <tr> 
   <td> -7006 </td> 
   <td> HDCP 出力制御値がありません </td> 
  </tr> 
  <tr> 
   <td> -7007 </td> 
   <td> 無効なライセンス期間が指定されました </td> 
  </tr> 
  <tr> 
   <td> -7008 </td> 
   <td> Widevine ライセンスの生成に失敗しました </td> 
  </tr> 
  <tr> 
   <td> -7009 </td> 
   <td> 無効 <span class="codeph"> WVExtension </span> 指定されたパラメーター </td> 
  </tr> 
  <tr> 
   <td> -7011 </td> 
   <td> Widevine オプションが無効です </td> 
  </tr> 
 </tbody> 
</table>
