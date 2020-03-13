---
description: FairPlayライセンストークンインターフェイスは、実稼働およびテストサービスを提供します。
seo-description: FairPlayライセンストークンインターフェイスは、実稼働およびテストサービスを提供します。
seo-title: FairPlayライセンストークンリクエスト/レスポンス
title: FairPlayライセンストークンリクエスト/レスポンス
uuid: 10d4a760-8895-4fb3-8288-1c3a640df587
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c

---


# FairPlayライセンストークンのリクエストと応答 {#fairplay-license-token-request-response}

FairPlayライセンストークンインターフェイスは、実稼働およびテストサービスを提供します。 このリクエストは、FairPlayライセンスに交換できるトークンを返します。

**方法：GET, POST** （www-urlエンコードされた本文と、両方のメソッドのパラメーターを含む）

**URL:**

* **実稼働環境：** `https://fp-gen.{prod_domain}/hms/fp/token`

* **テスト：** `https://fp-gen.test.expressplay.com/hms/fp/token`

* **リクエスト例：**

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

* **応答の例：**

   ```
   https://fp.service.expressplay.com:80/hms/fp/rights/?ExpressPlayToken=<base64-encoded ExpressPlay token>
   ```

**リクエストクエリパラメータ**

**表4:トークンクエリパラメーター**

| クエリパラメータ | 説明 | 必須？ |
|--- |--- |--- |
| customerAuthenticatorクエリパラメーターとしての顧客認証子customerAuthenticator FairPlay | これは、お客様の実稼働環境とテスト環境に対して1つずつ、お客様のAPIキーです。 これは、ExpressPlayの「Admin Dashboard」タブで確認できます。 | はい |
| errorFormat | htmlまたはjson。 html（デフォルト）の場合、応答のエンティティ本体にエラーのHTML表現が提供されます。 jsonを指定した場合、JSON形式の構造化された応答が返されます。 詳しくは、 [JSONエラー](https://www.expressplay.com/developer/restapi/#json-errors) （英語）を参照してください。 応答のMIMEタイプは、成功時はtext/uri-list、HTMLエラー形式の場合はtext/html、JSONエラー形式の場合はapplication/jsonです。 | いいえ |

**表4:ライセンスクエリパラメータ**

| **クエリパラメータ** | **説明** | **必須？** |
|---|---|---|
| `generalFlags` | ライセンスフラグを表す4バイトの16進文字列。 許可される値は「0000」のみです。 | いいえ |
| `kek` | キー暗号化キー(KEK)。 鍵は、鍵ラップアルゴリズム（AES鍵ラップ、RFC3394）を使用してKEKで暗号化されて保存されます。 を指定 `kek` する場合は、またはのいず `kid` れかのパラメ `ek` ータを指定する必要がありますが、両方を指 *定する必要はありません*。 | いいえ |
| `kid` | コンテンツ暗号化キーまたは文字列の16バイトの16進文字列表現です `'^somestring'`。 文字列の後に続く文字列の長さは、64文 `'^'` 字以下にする必要があります。 | いいえ |
| `ek` | 暗号化されたコンテンツキーの16進文字列表現です。 | いいえ |
| `contentKey` | コンテンツ暗号化キーの16バイトの16進文字列表現です。 | とまたはが指定されていな `kek` い限り、 `ek` は `kid` いとします。 |
| `iv` | コンテンツ暗号化IVの16バイトの16進文字列表現です。 | はい |
| `rentalDuration` | 秒単位のレンタル期間（デフォルト — 0） | いいえ |
| `fpExtension` | 短い形式の折り返しと、コ `extensionType` ンマ区 `extensionPayload`切りの文字列です。 For example: […] `&fpExtension=wudo,AAAAAA==&`[…] | いいえ、任意の数を使用できます。 |

**表5:トークン制限クエリパラメーター**

<table id="table_ar3_lsx_pv">  
 <thead> 
  <tr> 
   <th class="entry"> <b>クエリパラメータ</b> </th> 
   <th class="entry"> <b>説明</b> </th> 
   <th class="entry"> <b>必須？</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td> <span class="codeph"> expirationTime </span> </td> 
   <td> このトークンの有効期限。 この値は、 <a href="https://www.ietf.org/rfc/rfc3339.txt" format="html" scope="external"> RFC 3339の日付/時刻形式の </a> Zゾーン指定子（「ズールー時間」）での文字列か、前に+記号が付いた整数である必要があります。 RFC 3339の日付/時刻の例は、 <span class="codeph"> 2006-04-14T12:01:10Zです </span>。 <p>値が <a href="https://www.ietf.org/rfc/rfc3339.txt" format="html" scope="external"> RFC 3339日付/時刻形式の </a> 文字列である場合、トークンの絶対有効期限切れ日時を表します。 値が前に+符号の付いた整数である場合、発行からトークンが有効な相対秒数として解釈されます。 </p> 例えば、 <span class="codeph"> +60は1分 </span> を表します。 トークンの有効期間の最大値とデフォルト値（指定しない場合）は30日です。 </td> 
   <td> いいえ </td> 
  </tr> 
 </tbody> 
</table>

**表6:クエリパラメーターの相関**

| **クエリパラメータ** | **説明** | **必須？** |
|---|---|---|
| `cookie` | 最長32文字の任意の文字列で、トークンに格納され、トークン交換サーバーによって記録されます。 これは、引き換えサーバーのログエントリと、サービスプロバイダーのサーバーのログエントリとの間の関係を示すために使用できます。 | いいえ |

**回答**

**表7:HTTP応答**

| **HTTPステータスコード** | **説明** | **コンテンツタイプ** | **エンティティボディに次を含む** |
|---|---|---|---|
| `200 OK` | エラーはありません。 | `text/uri-list` | ライセンス取得URL +トークン |
| `400 Bad Request` | 無効な引数 | `text/html` または `application/json` | エラーの説明 |
| `401 Unauthorized` | 認証に失敗しました | `text/html` または `application/json` | エラーの説明 |
| `404 Not found` | 不正なURL | `text/html` または `application/json` | エラーの説明 |
| `50x Server Error` | サーバーエラー | `text/html` または `application/json` | エラーの説明 |

**表8:イベントエラーコード**

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
   <td> 無効なトークンの有効期限：&lt;詳細&gt; </td> 
  </tr> 
  <tr> 
   <td> -2003 </td> 
   <td> 無効なIPアドレス </td> 
  </tr> 
  <tr> 
   <td> -2005 </td> 
   <td> 無効なコンテンツ暗号化キー：&lt;詳細&gt; </td> 
  </tr> 
  <tr> 
   <td> -2008 </td> 
   <td> 無効な出力制御フラグが指定されました：&lt;詳細&gt; </td> 
  </tr> 
  <tr> 
   <td> -2017 </td> 
   <td> 認証トークンを指定する必要があります </td> 
  </tr> 
  <tr> 
   <td> -2018 </td> 
   <td> 認証トークンが無効です：&lt;詳細&gt; <p>注意： これは、認証子が間違っている場合や、 <span class="filepath"> *.test.expressplay.comのテストAPIに本番用認証子を使用してアクセスする場合、または本番用認証子を使用してテストAPI </span> にアクセスする場合に発生する可能性があります。 </p> <p importance="high">注意： テストSDKおよびアドバンステストツール(ATT)は、 <span class="filepath"> *.test.expressplay.comでのみ機能します。一方、実稼働デバ </span>イスは、*.service.expressplay.comを使用する必要がありま <span class="filepath"></span>す。 </p> </td> 
  </tr> 
  <tr> 
   <td> -2019 </td> 
   <td> 使用可能なトークンが不十分 </td> 
  </tr> 
  <tr> 
   <td> -2020 </td> 
   <td> 権限タイプがありません </td> 
  </tr> 
  <tr> 
   <td> -2021 </td> 
   <td> 無効な権限の種類 </td> 
  </tr> 
  <tr> 
   <td> -2022 </td> 
   <td> レンタル期間の終了時間がありません </td> 
  </tr> 
  <tr> 
   <td> -2023 </td> 
   <td> レンタル再生期間がありません </td> 
  </tr> 
  <tr> 
   <td> -2025 </td> 
   <td> 無効なレンタル再生期間 </td> 
  </tr> 
  <tr> 
   <td> -2027 </td> 
   <td> コンテンツの暗号化キーは32桁の16進数である必要があります </td> 
  </tr> 
  <tr> 
   <td> -2030 </td> 
   <td> ExpressPlay Adminエラー：&lt;詳細&gt; </td> 
  </tr> 
  <tr> 
   <td> -2031 </td> 
   <td> サービスアカウントが無効 </td> 
  </tr> 
  <tr> 
   <td> -2033 </td> 
   <td> 無効なcookie </td> 
  </tr> 
  <tr> 
   <td> -2034 </td> 
   <td> 無効な出力制御、値が指定範囲外 </td> 
  </tr> 
  <tr> 
   <td> -2035 </td> 
   <td> 対応する値が指定されていません </td> 
  </tr> 
  <tr> 
   <td> -2036 </td> 
   <td> 拡張子のタイプは4文字にする必要があります </td> 
  </tr> 
  <tr> 
   <td> -2037 </td> 
   <td> 拡張のペイロードはBase64エンコードする必要があります </td> 
  </tr> 
  <tr> 
   <td> -2040 </td> 
   <td> <span class="codeph"> OutputControlFlagは4バイ </span> トをエンコードする必要があります </td> 
  </tr> 
  <tr> 
   <td> -3004 </td> 
   <td> 無効なエラー形式が指定されました：&lt;形式&gt; </td> 
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
   <td> kidが見つかりません </td> 
  </tr> 
  <tr> 
   <td> -4019 </td> 
   <td> キーストレージサービスからコンテンツキーを取得できませんでした </td> 
  </tr> 
  <tr> 
   <td> -4020 </td> 
   <td> <span class="codeph"> kidは32 </span> 文字の16進数である必要があります </td> 
  </tr> 
  <tr> 
   <td> -4021 </td> 
   <td> <span class="codeph"> kidは^ </span> の後ろに64文字必要です </td> 
  </tr> 
  <tr> 
   <td> -4022 </td> 
   <td> 無効な <span class="codeph"> kid </span> </td> 
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
   <td> 無効なFPExtensionパラメ <span class="codeph"> ータが指定さ </span> れました </td> 
  </tr> 
  <tr> 
   <td> -6002 </td> 
   <td> 無効なFPトークンタイプ </td> 
  </tr> 
  <tr> 
   <td> -6003 </td> 
   <td> 無効な <span class="codeph"> ivパラメー </span> タが指定されました </td> 
  </tr> 
  <tr> 
   <td> -6004 </td> 
   <td> FPのCKCの生成に失敗しました </td> 
  </tr> 
  <tr> 
   <td> -6005 </td> 
   <td> 無効なキーデータが指定されました </td> 
  </tr> 
  <tr> 
   <td> -6006 </td> 
   <td> サービスがFairPlayのサポートに対して承認されていません </td> 
  </tr> 
  <tr> 
   <td> -6007 </td> 
   <td> 無効なレンタル期間が指定されました </td> 
  </tr> 
  <tr> 
   <td> -6008 </td> 
   <td> デバイスIDのバインディングはFairPlayではサポートされていません </td> 
  </tr> 
  <tr> 
   <td> -6009 </td> 
   <td> FairPlayオプションが無効 </td> 
  </tr> 
 </tbody> 
</table>