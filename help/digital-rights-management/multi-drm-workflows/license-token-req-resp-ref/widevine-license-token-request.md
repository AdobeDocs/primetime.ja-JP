---
description: Widevineライセンストークンインターフェイスは、実稼働およびテストサービスを提供します。
seo-description: Widevineライセンストークンインターフェイスは、実稼働およびテストサービスを提供します。
seo-title: Widevineライセンストークンリクエスト/レスポンス
title: Widevineライセンストークンリクエスト/レスポンス
uuid: a3522422-7075-49a7-bc55-137ef84ee430
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c

---


# Widevineライセンストークンリクエスト/レスポンス {#widevine-license-token-request-response}

Widevineライセンストークンインターフェイスは、実稼働およびテストサービスを提供します。

このHTTPリクエストは、Widevineライセンスに交換できるトークンを返します。

**方法：GET, POST** （www-urlエンコードされた本文と、両方のメソッドのパラメーターを含む）

**URL:**

* **実稼働環境：** `https://wv-gen.{prod_domain}/hms/wv/token`

* **テスト：** ` [https://wv-gen.test.expressplay.com/hms/wv/token](https://wv-gen.test.expressplay.com/hms/wv/token)`

* **リクエスト例：**

   ```
   https://wv-gen.service.expressplay.com/hms/wv/token?customerAuthenticator= 
   <ExpressPlay customer authenticator identifier>
   ```

* **応答の例：**

   ```
   https://wv.service.expressplay.com/hms/wv/rights/?ExpressPlayToken=<base64-encoded ExpressPlay token>
   ```

<!--<a id="section_1E22012EE4B94BB2974D3B16DE8812D9"></a>-->

**表13:トークンクエリパラメーター**

<table id="table_ww1_hcs_pv">  
 <thead> 
  <tr> 
   <th class="entry"> <b>クエリパラメータ</b> </th> 
   <th class="entry"> <b>説明</b> </th> 
   <th class="entry"> <b>必須？</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td> <span class="codeph"> customerAuthenticator </span> </td> 
   <td> <p>これは、お客様の実稼働環境とテスト環境に対して1つずつ、お客様のAPIキーです。 これは、ExpressPlayの「Admin Dashboard」タブで確認できます。 </p> </td> 
   <td> はい </td> 
  </tr> 
  <tr> 
   <td> <span class="codeph"> errorFormat </span> </td> 
   <td> htmlま <span class="codeph"> たは </span> json <span class="codeph"></span>。 <p>html(デ <span class="codeph"> フォ </span> ルト)の場合、エラーのHTML表現が応答のエンティティ本体に提供されます。 jsonを指 <span class="codeph"> 定 </span> した場合、JSON形式の構造化された応答が返されます。 詳しくは、 <a href="https://www.expressplay.com/developer/restapi/#json-errors" format="html" scope="external"> JSONエラーを </a> 参照してください。 </p> <p>応答のMIMEタイプは、成功時の <span class="codeph"> text uri-list、 </span> text <span class="codeph"> text html error、またはjson </span> application <span class="codeph"> error時のtext </span> text <span class="codeph"> text html error、あるいはjson application </span><span class="codeph"></span> formatのtext uri-listです。 </p> </td> 
   <td> いいえ </td> 
  </tr> 
 </tbody> 
</table>

**表14:ライセンスクエリパラメータ**

| クエリパラメータ | 説明 | 必須？ |
|--- |--- |--- |
| `generalFlags` | ライセンスフラグを表す4バイトの16進文字列。 許可される値は「0000」のみです | いいえ |
| `kek` | キー暗号化キー(KEK)。 鍵は、鍵ラップアルゴリズム（AES鍵ラップ、RFC3394）を使用してKEKで暗号化されて保存されます。 | いいえ |
| `kid` | コンテンツ暗号化キーまたは文字列の16バイトの16進文字列表現です `^somestring'`。 文字列の後に続く文字列の長さは、64文 `^` 字以下にする必要があります。 例については、下のメモを参照してください。 | はい |
| `ek` | 暗号化されたコンテンツキーの16進文字列表現です。 | いいえ |
| `contentKey` | コンテンツ暗号化キーの16バイトの16進文字列表現です。 | とまたはが指定され `kek` ていな `ek` い場合は `kid` ○ |
| `contentId` | コンテンツID | いいえ |
| `securityLevel` | 指定できる値は1 ～ 5です。 <ul><li>1 = `SW_SECURE_CRYPTO`</li><li> 2 = `SW_SECURE_DECODE` </li><li> 3 = `HW_SECURE_CRYPTO` </li><li> 4 = `HW_SECURE_DECODE` </li><li> 5 = `HW_SECURE_ALL`</li></ul> | はい |
| `hdcpOutputControl` | 指定できる値は0、1、2です。 <ul><li>0 = `HDCP_NONE` </li><li> 1 = `HDCP_V1` </li><li> 2 = `HDCP_V2`</li></ul> | はい |
| `licenseDuration` * | ライセンスの期間（秒単位）。 指定しなかった場合、期間に制限がないことを示します。 詳細は下記のメモを参照してください。 | いいえ |
| `wvExtension` | コンマ区切りの文字列として、extensionTypeとextensionPayloadを短い形式でラップしたもの。 以下の形式を参照してください。 例： `…&wvExtension=wudo,AAAAAA==&…` | いいえ、任意の数を使用できます。 |

バージョン `licenseDuration`情報： <ol><li> 再生が開始さ `licenseDuration` れてから秒後に停止します。 </li><li> 再生を無制限の時間停止/再開できるようにするには、を省略します(デフォ `licenseDuration` ルトで無限に設定されます)。 それ以外の場合は、エンドユーザーがストリームを楽しめる時間を指定します。 </li></ol>

**表15:トークン制限クエリパラメーター**

| クエリパラメータ | 説明 | 必須？ |
|--- |--- |--- |
| `expirationTime` | このトークンの有効期限。 この値は、 [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt) 日付/時刻形式の文字列(Zゾーン指定子（「ズールー時間」）、または+記号の前に付いた整数である必要があります。 RFC 3339の日付/時刻の例は、2006-04-14T12:01:10Zです。 <br> 値が [RFC 3339](https://www.ietf.org/rfc/rfc3339.txt) 日付/時刻形式の文字列である場合、トークンの絶対有効期限切れ日時を表します。 値が前に+記号が付いた整数の場合、発行からトークンが有効な相対秒数として解釈されます。 例えば、1分を `+60` 指定します。 <br> トークンの有効期間の最大値とデフォルト値（指定しない場合）は30日です。 | いいえ |

**表16:クエリパラメーターの相関**

| **クエリパラメータ** | **説明** | **必須？** |
|---|---|---|
| `cookie` | 最長32文字の任意の文字列。トークンに格納され、トークン交換サーバーによって記録されます。 引き換えサーバーのログエントリと、サービスプロバイダーのサーバーのログエントリを関連付けるために使用できます。 | いいえ |

<!--<a id="section_6BFBD314C77C40C4B172ABBDD2D8D80E"></a>-->

**表17:HTTP応答**

| **HTTPステータスコード** | **説明** | **コンテンツタイプ** | **エンティティボディに次を含む** |
|---|---|---|---|
| `200 OK` | エラーはありません。 | `text/uri-list` | ライセンス取得URL +トークン |
| `400 Bad Request` | 無効な引数 | `text/html` または `application/json` | エラーの説明 |
| `401 Unauthorized` | 認証に失敗しました | `text/html` または `application/json` | エラーの説明 |
| `404 Not found` | 不正なURL | `text/html` または `application/json` | エラーの説明 |
| `50x Server Error` | サーバーエラー | `text/html` または `application/json` | エラーの説明 |

**表18:イベントエラーコード**

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
   <td> 認証トークンが無効です：&lt;詳細&gt; <p>注意： 認証子が間違っている場合や、*.test.expressplay.comのテストAPIに本番用認証子を使用してアクセスする場合、またはその逆の場合に、この問題が発生する可能性があります。 </p> <p importance="high">注意： テストSDKおよびアドバンステストツール(ATT)は、 <span class="filepath"> *.test.expressplay.comでのみ機能します。一方、実稼働デバ </span>イスでは、 <span class="filepath"> *.service.expressplay.comを使用する必要があります。 </span> </p>. </td> 
  </tr> 
  <tr> 
   <td> -2019 </td> 
   <td> 使用可能なトークンが不十分 </td> 
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
   <td> kidが見つかり <span class="filepath"> ません </span> </td> 
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
   <td> -6005 </td> 
   <td> 無効なキーデータが指定されました </td> 
  </tr> 
  <tr> 
   <td> -6007 </td> 
   <td> 無効なレンタル期間が指定されました </td> 
  </tr> 
  <tr> 
   <td> -7002 </td> 
   <td> デバイスIDのバインディングはWidevineではサポートされていません </td> 
  </tr> 
  <tr> 
   <td> -7003 </td> 
   <td> セキュリティレベルの値がありません </td> 
  </tr> 
  <tr> 
   <td> -7004 </td> 
   <td> 無効なセキュリティレベル値 </td> 
  </tr> 
  <tr> 
   <td> -7006 </td> 
   <td> HDCP出力制御値がありません </td> 
  </tr> 
  <tr> 
   <td> -7007 </td> 
   <td> 無効なライセンス期間が指定されました </td> 
  </tr> 
  <tr> 
   <td> -7008 </td> 
   <td> Widevineライセンスの生成に失敗しました </td> 
  </tr> 
  <tr> 
   <td> -7009 </td> 
   <td> 無効なWVExtensionパラ <span class="codeph"> メータが指 </span> 定されました </td> 
  </tr> 
  <tr> 
   <td> -7011 </td> 
   <td> Widevineオプションが無効 </td> 
  </tr> 
 </tbody> 
</table>