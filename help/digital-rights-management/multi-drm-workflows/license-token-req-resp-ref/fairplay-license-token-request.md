---
description: FairPlay ライセンストークンインターフェイスは、実稼動およびテストサービスを提供します。
title: FairPlay ライセンストークンリクエスト/レスポンス
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 4%

---

# FairPlay ライセンストークンのリクエストと応答 {#fairplay-license-token-request-response}

FairPlay ライセンストークンインターフェイスは、実稼動およびテストサービスを提供します。 このリクエストは、FairPlay ライセンスに交換できるトークンを返します。

**メソッド：GET、POST** （www-url-encoded の本文には、両方のメソッドのパラメータが含まれています）

**URL:**

* **実稼動：** `https://fp-gen.{prod_domain}/hms/fp/token`

* **テスト：** `https://fp-gen.test.expressplay.com/hms/fp/token`

* **リクエストの例：**

```<xref href="https: pr-gen.test.expressplay.com="" hms="" pr="" token?customerAuthenticator="201722,1ad8eed133edf43cbcc185f0236828ae&kid=b366360da82e9c6e0b0984002a362cf2&contentKey=b366360da82e9c6e0b0984002a362cf2&rightsType=BuyToOwn&analogVideoOPL=0&compressedDigitalAudioOPL=0&compressedDigitalVideoOPL=0&uncompressedDigitalAudioOPL=0&uncompressedDigitalVideoOPL=0&quot; format=&quot;html&quot; scope=&quot;external&quot;">
  https://fp-gen.test.expressplay.com/hms/fp/token?customerAuthenticator= 
   <ExpressPlay customer authenticator identifier> 
   &kid=<CEKSID> 
   &contentKey=<CEK> 
   &rightsType=BuyToOwn 
   &analogVideoOPL=0 
   &compressedDigitalAudioOPL=0 
   &compressedDigitalVideoOPL=0 
   &uncompressedDigitalAudioOPL=0 
   &uncompressedDigitalVideoOPL=0
```

* **レスポンスのサンプル：**

  ```
  https://fp.service.expressplay.com:80/hms/fp/rights/?ExpressPlayToken=<base64-encoded ExpressPlay token>
  ```

**リクエストクエリパラメーター**

**表 3：トークンクエリのパラメータ**

| クエリパラメーター | 説明 | 必須？ |
|--- |--- |--- |
| customerAuthenticator クエリパラメータ customerAuthenticator FairPlay としての顧客認証子 | これは、実稼動環境とテスト環境用に 1 つずつ、顧客 API キーです。 これは、「 ExpressPlay Admin Dashboard 」タブで確認できます。 | はい |
| errorFormat | html または json。 html（デフォルト）の場合、HTMLのエラー表現が応答のエンティティ本文に提供されます。 json を指定した場合、JSON 形式の構造化された応答が返されます。 詳しくは、 [JSON エラー](https://www.expressplay.com/developer/restapi/#json-errors) 」を参照してください。 応答の MIME タイプは、成功時は text/uri-list、HTMLエラー形式の場合は text/html、JSON エラー形式の場合は application/json です。 | いいえ |

**表 4：ライセンスクエリーパラメータ**

| **クエリパラメーター** | **説明** | **必須？** |
|---|---|---|
| `generalFlags` | ライセンスフラグを表す 4 バイトの 16 進文字列。 許可されている値は「0000」のみです。 | いいえ |
| `kek` | キー暗号化キー (KEK)。 キーは、キーラッピングアルゴリズム（AES キーラップ、RFC3394）を使用して、KEK で暗号化されて格納されます。 次の場合 `kek` が指定され、 `kid` または `ek` パラメータを指定する必要があります。 *しかし、両方は*. | いいえ |
| `kid` | コンテンツ暗号化キーまたは文字列の 16 バイトの 16 進文字列表現です `'^somestring'`. 文字列の長さの後に `'^'` は 64 文字以下にする必要があります。 | いいえ |
| `ek` | 暗号化されたコンテンツキーの 16 進文字列表現です。 | いいえ |
| `contentKey` | コンテンツ暗号化キーの 16 バイトの 16 進文字列表現 | はい、ただし `kek` および `ek` または `kid` が提供されます。 |
| `iv` | コンテンツ暗号化 IV の 16 バイトの 16 進文字列表現 | はい |
| `rentalDuration` | 秒単位のレンタル期間（デフォルト — 0） | いいえ |
| `fpExtension` | 短い形式のラッピング `extensionType` および `extensionPayload`をコンマ区切りの文字列として指定します。 例： [...] `&fpExtension=wudo,AAAAAA==&`[...] | いいえ、任意の数を使用できます |

**表 5：トークン制限クエリー・パラメータ**

<table id="table_ar3_lsx_pv">  
 <thead> 
  <tr> 
   <th class="entry"> <b>クエリパラメーター</b> </th> 
   <th class="entry"> <b>説明</b> </th> 
   <th class="entry"> <b>必須？</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td> <span class="codeph"> expirationTime </span> </td> 
   <td> このトークンの有効期限。 この値は、 <a href="https://www.ietf.org/rfc/rfc3339.txt" format="html" scope="external"> RFC 3339 </a> 「Z」ゾーン指定子（「ズール時間」）での日付/時刻形式、または前に「+」記号が付いた整数。 RFC 3339 日時の例は次のとおりです。 <span class="codeph"> 2006-04-14T12:01:10Z </span>. <p>値が <a href="https://www.ietf.org/rfc/rfc3339.txt" format="html" scope="external"> RFC 3339 </a> 日付/時刻形式の場合は、トークンの絶対的な有効期限切れの日時を表します。 値が整数の前に「+」記号が付いた場合、発行からトークンが有効であることを相対秒数として解釈されます。 </p> 例： <span class="codeph"> +60 </span> 1 分を指定します。 トークンの有効期間は、最大とデフォルト（指定されていない場合）で 30 日です。 </td> 
   <td> いいえ </td> 
  </tr> 
 </tbody> 
</table>

**表 6：相関クエリー・パラメータ**

| **クエリパラメーター** | **説明** | **必須？** |
|---|---|---|
| `cookie` | 最大 32 文字の任意の文字列。トークンに格納され、トークン交換サーバーによって記録されます。 これは、引き換えサーバーのログエントリと、サービスプロバイダーのサーバーのログエントリを関連付けるために使用できます。 | いいえ |

**応答**

**表 7:HTTP 応答**

| **HTTP ステータスコード** | **説明** | **Content-Type** | **エンティティ本文に次を含む** |
|---|---|---|---|
| `200 OK` | エラーはありません。 | `text/uri-list` | ライセンス取得 URL +トークン |
| `400 Bad Request` | 無効な引数 | `text/html` または `application/json` | エラーの説明 |
| `401 Unauthorized` | 認証に失敗しました | `text/html` または `application/json` | エラーの説明 |
| `404 Not found` | 無効な URL | `text/html` または `application/json` | エラーの説明 |
| `50x Server Error` | サーバーエラー | `text/html` または `application/json` | エラーの説明 |

**表 8：イベントエラーコード**

<table id="table_i2c_zsx_pv">  
 <thead> 
  <tr> 
   <th class="entry"> <b>コード</b> </th> 
   <th class="entry"> <b>説明</b> </th> 
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
   <td> 認証トークンが無効です： &lt;details&gt; <p>注意：これは、認証子が正しくない場合、または <span class="filepath"> *.test.expressplay.com </span> 本番用認証子の使用（または本番用認証子の使用） </p> <p importance="high">注意：テスト SDK と高度なテストツール (ATT) は、 <span class="filepath"> *.test.expressplay.com </span>に対して、実稼動デバイスはを使用する必要があります。 <span class="filepath"> *.service.expressplay.com </span>. </p> </td> 
  </tr> 
  <tr> 
   <td> -2019 </td> 
   <td> 使用可能なトークンが不十分です </td> 
  </tr> 
  <tr> 
   <td> -2020 </td> 
   <td> 権限タイプがありません </td> 
  </tr> 
  <tr> 
   <td> -2021 </td> 
   <td> 無効な権限タイプ </td> 
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
   <td> kid がありません </td> 
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
   <td> <span class="codeph"> kid </span> は、^の後ろの 64 文字にする必要があります </td> 
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
   <td> -6001 </td> 
   <td> 無効 <span class="codeph"> FPExtension </span> 指定されたパラメーター </td> 
  </tr> 
  <tr> 
   <td> -6002 </td> 
   <td> 無効な FP トークンタイプ </td> 
  </tr> 
  <tr> 
   <td> -6003 </td> 
   <td> 無効 <span class="codeph"> iv </span> 指定されたパラメータ </td> 
  </tr> 
  <tr> 
   <td> -6004 </td> 
   <td> FP の CKC を生成できませんでした </td> 
  </tr> 
  <tr> 
   <td> -6005 </td> 
   <td> 無効なキーデータが指定されました </td> 
  </tr> 
  <tr> 
   <td> -6006 </td> 
   <td> FairPlay サポートのためのサービスが許可されていません </td> 
  </tr> 
  <tr> 
   <td> -6007 </td> 
   <td> 無効なレンタル期間が指定されました </td> 
  </tr> 
  <tr> 
   <td> -6008 </td> 
   <td> FairPlay では、デバイス ID のバインディングはサポートされていません </td> 
  </tr> 
  <tr> 
   <td> -6009 </td> 
   <td> FairPlay オプションが無効です </td> 
  </tr> 
 </tbody> 
</table>
