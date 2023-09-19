---
description: PlayReady ライセンストークンインターフェイスは、実稼動およびテストサービスを提供します。
title: PlayReady ライセンストークンリクエスト/レスポンス
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 4%

---

# PlayReady ライセンストークンリクエスト/レスポンス {#playready-license-token-request-response}

PlayReady ライセンストークンインターフェイスは、実稼動およびテストサービスを提供します。

この HTTP リクエストは、PlayReady ライセンスに交換できるトークンを返します。

**メソッド：GET、POST** （www-url-encoded の本文には、両方のメソッドのパラメータが含まれています）

**URL:**

* **実稼動：** `https://pr-gen.{prod_domain}/hms/pr/token`

* **テスト：** ` [https://pr-gen.test.expressplay.com/hms/pr/token](https://pr-gen.test.expressplay.com/hms/pr/token)`

* **リクエストの例：**

  ```
  <xref href="https: pr-gen.test.expressplay.com="" hms="" pr="" token?customerAuthenticator="201722,1ad8eed133edf43cbcc185f0236828ae&kid=b366360da82e9c6e0b0984002a362cf2&contentKey=b366360da82e9c6e0b0984002a362cf2&rightsType=BuyToOwn&analogVideoOPL=0&compressedDigitalAudioOPL=0&compressedDigitalVideoOPL=0&uncompressedDigitalAudioOPL=0&uncompressedDigitalVideoOPL=0&quot; format=&quot;html&quot; scope=&quot;external&quot;">
  https://pr-gen.test.expressplay.com/hms/pr/token?customerAuthenticator=
   <ExpressPlay customer authenticator identifier>
   &kid=<CEKSID>
   &contentKey=<CEK>
   &rightsType=BuyToOwn
   &analogVideoOPL=0
   &compressedDigitalAudioOPL=0
   &compressedDigitalVideoOPL=0
   &uncompressedDigitalAudioOPL=0
   &uncompressedDigitalVideoOPL=0
  </xref href="https:>
  ```

* **レスポンスのサンプル：**

  ```
  {"licenseAcquisitionUrl":"https://expressplay-licensing.axprod.net/LicensingService.ashx",
              "token":"<base64-encoded ExpressPlay token>"}
  ```

## リクエストクエリパラメーター {#section_26F8856641A64A46A3290DBE61ACFAD2}

**表 9：トークンクエリのパラメータ**

<table id="table_zxg_dyr_pv">  
 <thead> 
  <tr> 
   <th class="entry"><b>クエリパラメーター</b> </th> 
   <th class="entry"><b>説明</b> </th> 
   <th class="entry"><b>必須？</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td><span class="codeph"> customerAuthenticator</span> </td> 
   <td> <p>これは、実稼動環境とテスト環境用に 1 つずつ、顧客 API キーです。 これは、「 ExpressPlay Admin Dashboard 」タブで確認できます。 </p> </td> 
   <td> はい </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> errorFormat</span> </td> 
   <td>次のいずれか <span class="codeph"> html</span> または <span class="codeph"> json</span>. 次の場合 <span class="codeph"> html</span> （デフォルト）HTMLのエラー表現は、応答のエンティティ本文に表示されます。 <p>次の場合 <span class="codeph"> json</span> が指定されている場合、JSON 形式の構造化された応答が返されます。 詳しくは、 <a href="https://www.expressplay.com/developer/restapi/#json-errors" format="html" scope="external"> JSON エラー</a> 」を参照してください。 </p> <p>応答の MIME タイプは、 <span class="codeph"> text/uri-list</span> 成功して <span class="codeph"> text/html</span> (HTMLエラー形式の場合 )、または <span class="codeph"> application/json</span> JSON エラー形式の場合。 </p> </td> 
   <td> いいえ </td> 
  </tr> 
 </tbody> 
</table>

**表 10：ライセンス・クエリー・パラメータ**

<table id="table_f1l_fyr_pv">  
 <thead> 
  <tr> 
   <th class="entry"><b>クエリパラメーター</b> </th> 
   <th class="entry"><b>説明</b> </th> 
   <th class="entry"><b>必須？</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td><span class="codeph"> generalFlags</span> </td> 
   <td>ライセンスフラグを表す 4 バイトの 16 進文字列。 永続的なライセンスの場合は、「00000001」に設定する必要があります。 <p>注意：レンタルライセンス (<span class="codeph"> rightsType=Rental</span>) は永続的である必要があります。 </p> </td> 
   <td> いいえ </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> kek</span> </td> 
   <td> キー暗号化キー (KEK)。 キーは、キーラッピングアルゴリズム（AES キーラップ、RFC3394）を使用して、KEK で暗号化されて格納されます。 </td> 
   <td> いいえ </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> kid</span> </td> 
   <td>コンテンツ暗号化キーまたは文字列の 16 バイトの 16 進文字列表現です <span class="codeph"> ^somestring'</span>. 文字列の後に「^」を付ける長さは 64 文字以下にする必要があります。 </td> 
   <td> はい </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> ek</span> </td> 
   <td> 暗号化されたコンテンツキーの 16 進文字列表現です。 </td> 
   <td> いいえ </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> contentKey</span> </td> 
   <td> コンテンツ暗号化キーの 16 バイトの 16 進文字列表現 </td> 
   <td>はい、ただし <span class="codeph"> kek</span> および <span class="codeph"> ek</span> または <span class="codeph"> kid</span> が指定されている </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> rightsType</span> </td> 
   <td>権限の種類を指定します。 次の条件を満たす必要があります <span class="codeph"> BuyToOwn</span> または <span class="codeph"> レンタル</span>. </td> 
   <td> はい </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> rental.periodEndTime</span> </td> 
   <td>レンタル終了日。 この値は、「Z」ゾーン指定子（「ズール時間」）形式の「RFC 3339」 _日付/時刻形式か、前に「+」記号が付いた整数である必要があります。 <p>値が <a href="https://www.ietf.org/rfc/rfc3339.txt" format="html" scope="external"> RFC 3339</a> 日付/時刻形式の場合は、ライセンスの絶対有効期限日時を表します。 RFC 3339 日時の例は2006-04-14T12です:01:10Z </p> <p> 値が整数の前に「+」記号が付いた場合は、トークンが発行された時点からの相対秒数として解釈されます。 この時間を過ぎると、コンテンツを再生できなくなります。 次の場合にのみ有効です。 <span class="codeph"> rightsType</span> 次に該当 <span class="codeph"> レンタル</span>. </p> </td> 
   <td>はい、いつ <span class="codeph"> rightsType</span> 次に該当 <span class="codeph"> レンタル</span>. </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> rental.playDuration</span> </td> 
   <td>再生が開始された後にコンテンツを再生できる時間（秒）。 次の場合にのみ有効です。 <span class="codeph"> rightsType</span> レンタルです。 </td> 
   <td> いいえ </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> analogVideoOPL</span> </td> 
   <td> アナログビデオの出力保護レベルを示す整数値。 有効範囲は 0 ～ 999 です。 </td> 
   <td> はい </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> compressedDigitalAudioOPL</span> </td> 
   <td> 圧縮デジタルオーディオの出力保護レベルを示す整数値。 有効範囲は 0 ～ 999 です。 </td> 
   <td> はい </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> compressedDigitalVideoOPL</span> </td> 
   <td> 圧縮デジタルビデオの出力保護レベルを示す整数値。 有効範囲は 0 ～ 999 です。 </td> 
   <td> はい </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> uncompressedDigitalAudioOPL</span> </td> 
   <td> 非圧縮デジタルオーディオの出力保護レベルを示す整数値。 有効範囲は 0 ～ 999 です。 </td> 
   <td> はい </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> uncompressedDigitalVideoOPL</span> </td> 
   <td> 非圧縮デジタルビデオの出力保護レベルを示す整数値。 有効範囲は 0 ～ 999 です。 </td> 
   <td> はい </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> unknownOutputBehavior</span> </td> 
   <td>出力が不明な場合の必須の動作。 許可されている値： <span class="codeph"> 許可</span>, <span class="codeph"> 許可しない</span> または <span class="codeph"> SDOnly</span> </td> 
   <td> いいえ </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> outputControlFlags</span> </td> 
   <td> 他の出力制御オプションのフラグを示す 4 バイトの 16 進値 </td> 
   <td> いいえ </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> extensionType</span> </td> 
   <td>拡張機能の 32 ビット識別子を表す任意の 4 文字の単語。 各文字の 8 ビット ASCII コードは、識別子の対応する 8 ビットバイト部分です。 例えば、識別子の値 0x61626364（16 進数）は、「<span class="codeph"> abcd</span>', 'a'の ASCII コードが 0x61 など </td> 
   <td> いいえ </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> extensionPayload</span> </td> 
   <td> 拡張機能の base64 エンコードされた文字列。 </td> 
   <td>はい、いつ <span class="codeph"> extensionType</span> が指定されている。 </td> 
  </tr> 
 </tbody> 
</table>

## 応答 {#section_0079C31B4AF14DBBB6277CF251FB90E3}

**表 11: HTTP 応答**

| **HTTP ステータスコード** | **説明** | **Content-Type** | **エンティティ本文に次を含む** |
|---|---|---|---|
| `200 OK` | エラーはありません。 | `text/uri-list` | ライセンス取得 URL とトークン |
| `400 Bad Request` | 無効な引数 | `text/html` または `application/json` | エラーの説明 |
| `401 Unauthorized` | 認証に失敗しました | `text/html` または `application/json` | エラーの説明 |
| `404 Not found` | 無効な URL | `text/html` または `application/json` | エラーの説明 |
| `50x Server Error` | サーバーエラー | `text/html` または `application/json` | エラーの説明 |

**表 12：イベントエラーコード**

<table id="table_lqb_ycs_pv">  
 <thead> 
  <tr> 
   <th class="entry"><b>コード</b> </th> 
   <th class="entry"><b>説明</b> </th> 
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
   <td>認証トークンが無効です： &lt;details&gt; <p>注意：これは、認証子が間違っている場合や、*.test.expressplay.comにあるテスト API に本番用認証子を使用してアクセスする場合、または本番用認証子を使用してテスト API にアクセスする場合に発生する可能性があります。 </p> <p importance="high">注意：テスト SDK と高度なテストツール (ATT) は、 <span class="filepath"> *.test.expressplay.com</span>に対して、実稼動デバイスはを使用する必要があります。 <span class="filepath"> *.service.expressplay.com</span>. </p> </td> 
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
   <td><span class="codeph"> OutputControlFlag</span> は、4 バイトでエンコードする必要があります </td> 
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
   <td> -4018 </td> 
   <td>見つかりません <span class="codeph"> kid</span> </td> 
  </tr> 
  <tr> 
   <td> -4019 </td> 
   <td> キーストレージサービスからコンテンツキーを取得できませんでした </td> 
  </tr> 
  <tr> 
   <td> -4020 </td> 
   <td><span class="codeph"> kid</span> は、32 文字の 16 進数である必要があります </td> 
  </tr> 
  <tr> 
   <td> -4021 </td> 
   <td><span class="codeph"> kid</span> は、^の後ろの 64 文字にする必要があります </td> 
  </tr> 
  <tr> 
   <td> -4022 </td> 
   <td>無効 <span class="codeph"> kid</span> </td> 
  </tr> 
  <tr> 
   <td> -4024 </td> 
   <td>暗号化が無効です <span class="codeph"> key</span> または kek </td> 
  </tr> 
  <tr> 
   <td> -5001 </td> 
   <td> 不明な出力タイプエラー </td> 
  </tr> 
  <tr> 
   <td> -5002 </td> 
   <td> このサービスでは PlayReady オプションが無効になっています </td> 
  </tr> 
  <tr> 
   <td> -5003 </td> 
   <td> 無効な一般フラグ </td> 
  </tr> 
  <tr> 
   <td> -5004 </td> 
   <td> デバイス ID は 32 文字の 16 進数である必要があります </td> 
  </tr> 
  <tr> 
   <td> -5005 </td> 
   <td> 無効なデバイス ID </td> 
  </tr> 
  <tr> 
   <td> -5006 </td> 
   <td> OPL 値がありません </td> 
  </tr> 
  <tr> 
   <td> -5007 </td> 
   <td>次のうち 1 つのみ： <span class="codeph"> kek</span> または <span class="codeph"> contentKey</span> 指定可能 </td> 
  </tr> 
 </tbody> 
</table>
