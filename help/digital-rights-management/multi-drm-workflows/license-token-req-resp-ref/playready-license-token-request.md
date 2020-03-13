---
description: PlayReadyライセンストークンインターフェイスは、実稼働およびテストサービスを提供します。
seo-description: PlayReadyライセンストークンインターフェイスは、実稼働およびテストサービスを提供します。
seo-title: PlayReadyライセンストークンリクエスト/レスポンス
title: PlayReadyライセンストークンリクエスト/レスポンス
uuid: 20ebd582-ebb9-4716-8c1e-df3e58d6ec14
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c

---


# PlayReadyライセンストークンリクエスト/レスポンス {#playready-license-token-request-response}

PlayReadyライセンストークンインターフェイスは、実稼働およびテストサービスを提供します。

このHTTPリクエストは、PlayReadyライセンスに交換できるトークンを返します。

**方法：GET, POST** （www-urlエンコードされた本文と、両方のメソッドのパラメーターを含む）

**URL:**

* **実稼働環境：** `https://pr-gen.{prod_domain}/hms/pr/token`

* **テスト：** ` [https://pr-gen.test.expressplay.com/hms/pr/token](https://pr-gen.test.expressplay.com/hms/pr/token)`

* **リクエスト例：**

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

* **応答の例：**

   ```
   {"licenseAcquisitionUrl":"https://expressplay-licensing.axprod.net/LicensingService.ashx",
               "token":"<base64-encoded ExpressPlay token>"}
   ```

## リクエストクエリパラメータ {#section_26F8856641A64A46A3290DBE61ACFAD2}

**表9:トークンクエリパラメーター**

<table id="table_zxg_dyr_pv">  
 <thead> 
  <tr> 
   <th class="entry"><b>クエリパラメータ</b> </th> 
   <th class="entry"><b>説明</b> </th> 
   <th class="entry"><b>必須？</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td><span class="codeph"> customerAuthenticator</span> </td> 
   <td> <p>これは、お客様の実稼働環境とテスト環境に対して1つずつ、お客様のAPIキーです。 これは、ExpressPlayの「Admin Dashboard」タブで確認できます。 </p> </td> 
   <td> はい </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> errorFormat</span> </td> 
   <td>htmlまた <span class="codeph"> は</span> json <span class="codeph"> です</span>。 html <span class="codeph"> (デフォルト</span> )の場合、エラーのHTML表現が応答のエンティティ本体に提供されます。 <p>jsonを指 <span class="codeph"> 定した場合</span> 、JSON形式の構造化された応答が返されます。 詳しくは、 <a href="https://www.expressplay.com/developer/restapi/#json-errors" format="html" scope="external"> JSONエラー</a> を参照してください。 </p> <p>応答のMIMEタイプは、成功した場合は <span class="codeph"> text/uri-list</span> 、HTMLエラー形式の場合は <span class="codeph"> text/html</span> 、JSONエラー形式の場合は <span class="codeph"> application/json</span> です。 </p> </td> 
   <td> いいえ </td> 
  </tr> 
 </tbody> 
</table>

**表10:ライセンスクエリパラメータ**

<table id="table_f1l_fyr_pv">  
 <thead> 
  <tr> 
   <th class="entry"><b>クエリパラメータ</b> </th> 
   <th class="entry"><b>説明</b> </th> 
   <th class="entry"><b>必須？</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td><span class="codeph"> generalFlags</span> </td> 
   <td>ライセンスフラグを表す4バイトの16進文字列。 永続的なライセンスの場合は「00000001」に設定する必要があります。 <p>注意：レンタルライセンス(<span class="codeph"> rightsType=Rental</span>)は永続的である必要があります。 </p> </td> 
   <td> いいえ </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> kek</span> </td> 
   <td> キー暗号化キー(KEK)。 鍵は、鍵ラップアルゴリズム（AES鍵ラップ、RFC3394）を使用してKEKで暗号化されて保存されます。 </td> 
   <td> いいえ </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> kid</span> </td> 
   <td>コンテンツ暗号化キーの16バイトの16進文字列表現または文字列「 <span class="codeph"> ^somestring」です</span>。 「^」の後に続く文字列の長さは、64文字以下にする必要があります。 </td> 
   <td> はい </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> ek</span> </td> 
   <td> 暗号化されたコンテンツキーの16進文字列表現です。 </td> 
   <td> いいえ </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> contentKey</span> </td> 
   <td> コンテンツ暗号化キーの16バイトの16進文字列表現です。 </td> 
   <td>kekと <span class="codeph"> ek</span> または <span class="codeph"> kidを指定し</span> ない <span class="codeph"></span> 。 </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> rightsType</span> </td> 
   <td>権限の種類を指定します。 BuyToOwnまたは <span class="codeph"> Rental</span> が必要 <span class="codeph"> です</span>。 </td> 
   <td> はい </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> rental.periodEndTime</span> </td> 
   <td>レンタル終了日。 この値は、Zゾーン指定子（「ズールー時間」）形式の「RFC 3339」日付/時刻形式か、前に+符号の付いた整数である必要があります。 <p>値が <a href="https://www.ietf.org/rfc/rfc3339.txt" format="html" scope="external"> RFC 3339</a> 日付/時刻形式の場合、ライセンスの絶対有効期限切れ日時を表します。 RFC 3339の日付/時刻の例は、2006-04-14T12:01:10Zです。 </p> <p> 値が前に+符号の付いた整数の場合、トークンが発行された時点からの相対秒数として解釈されます。 この時間が経過すると、コンテンツを再生できなくなります。 rightsTypeが <span class="codeph"> Rentalの場合のみ</span> 有効 <span class="codeph"> です</span>。 </p> </td> 
   <td>はい(rightsTypeが <span class="codeph"> Rentalの場合</span> ) <span class="codeph"> 。</span> </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> rental.playDuration</span> </td> 
   <td>再生が開始された後にコンテンツを再生できる時間（秒単位）です。 rightsTypeがRentalの場合に <span class="codeph"> のみ</span> 有効です。 </td> 
   <td> いいえ </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> analogVideoOPL</span> </td> 
   <td> アナログビデオの出力保護レベルを示す整数値。 有効な範囲は0 ～ 999です。 </td> 
   <td> はい </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> compressedDigitalAudioOPL</span> </td> 
   <td> 圧縮デジタルオーディオの出力保護レベルを示す整数値。 有効な範囲は0 ～ 999です。 </td> 
   <td> はい </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> compressedDigitalVideoOPL</span> </td> 
   <td> 圧縮デジタルビデオの出力保護レベルを示す整数値。 有効な範囲は0 ～ 999です。 </td> 
   <td> はい </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> uncompressedDigitalAudioOPL</span> </td> 
   <td> 非圧縮デジタルオーディオの出力保護レベルを示す整数値。 有効な範囲は0 ～ 999です。 </td> 
   <td> はい </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> uncompressedDigitalVideoOPL</span> </td> 
   <td> 非圧縮デジタルビデオの出力保護レベルを示す整数値。 有効な範囲は0 ～ 999です。 </td> 
   <td> はい </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> unknownOutputBehavior</span> </td> 
   <td>出力が不明な場合の必須の動作。 許可されている値： <span class="codeph"> Allow</span>、 <span class="codeph"> Disallow</span> 、 <span class="codeph"> SDOnly</span> </td> 
   <td> いいえ </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> outputControlFlags</span> </td> 
   <td> その他の出力制御オプションのフラグを示す4バイトの16進値 </td> 
   <td> いいえ </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> extensionType</span> </td> 
   <td>拡張の32ビット識別子を表す任意の4文字の単語。 各文字の8ビットASCIIコードは、識別子の対応する8ビットバイト部分です。 例えば、「a」のASCIIコードは0x61と続くので、識別子の値0x61626364（16進数）は「<span class="codeph"> abcd</span>」と書かれます。 </td> 
   <td> いいえ </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> extensionPayload</span> </td> 
   <td> 拡張のbase64エンコードされた文字列。 </td> 
   <td>extensionTypeが指定されてい <span class="codeph"> る場合</span> 、はい。 </td> 
  </tr> 
 </tbody> 
</table>

## 回答 {#section_0079C31B4AF14DBBB6277CF251FB90E3}

**表11:HTTP応答**

| **HTTPステータスコード** | **説明** | **コンテンツタイプ** | **エンティティボディに次を含む** |
|---|---|---|---|
| `200 OK` | エラーはありません。 | `text/uri-list` | ライセンス取得URLとトークン |
| `400 Bad Request` | 無効な引数 | `text/html` または `application/json` | エラーの説明 |
| `401 Unauthorized` | 認証に失敗しました | `text/html` または `application/json` | エラーの説明 |
| `404 Not found` | 不正なURL | `text/html` または `application/json` | エラーの説明 |
| `50x Server Error` | サーバーエラー | `text/html` または `application/json` | エラーの説明 |

**表12:イベントエラーコード**

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
   <td>認証トークンが無効です：&lt;詳細&gt; <p>注意： 認証子が間違っている場合や、*.test.expressplay.comのテストAPIに本番用認証子を使用してアクセスする場合、またはその逆の場合に、この問題が発生する可能性があります。 </p> <p importance="high">注意：テストSDKおよびアドバンステストツール(ATT)は、 <span class="filepath"> *.test.expressplay.comでのみ機能しますが</span>、実稼働デバイスでは、*.service.expressplay.comを使用する必要があります <span class="filepath"></span>。 </p> </td> 
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
   <td><span class="codeph"> OutputControlFlagは</span> 4バイトをエンコードする必要があります </td> 
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
   <td> -4018 </td> 
   <td>kidが見つかり <span class="codeph"> ません</span> </td> 
  </tr> 
  <tr> 
   <td> -4019 </td> 
   <td> キーストレージサービスからコンテンツキーを取得できませんでした </td> 
  </tr> 
  <tr> 
   <td> -4020 </td> 
   <td><span class="codeph"> kidは</span> 32文字の16進数である必要があります </td> 
  </tr> 
  <tr> 
   <td> -4021 </td> 
   <td><span class="codeph"> kidは</span> ^の後ろに64文字必要です </td> 
  </tr> 
  <tr> 
   <td> -4022 </td> 
   <td>無効な <span class="codeph"> kid</span> </td> 
  </tr> 
  <tr> 
   <td> -4024 </td> 
   <td>無効な暗号化キ <span class="codeph"> ー</span> またはkek </td> 
  </tr> 
  <tr> 
   <td> -5001 </td> 
   <td> 不明な出力タイプのエラー </td> 
  </tr> 
  <tr> 
   <td> -5002 </td> 
   <td> このサービスではPlayReadyオプションが無効です </td> 
  </tr> 
  <tr> 
   <td> -5003 </td> 
   <td> 無効な一般フラグ </td> 
  </tr> 
  <tr> 
   <td> -5004 </td> 
   <td> デバイスIDは32文字の16進数である必要があります </td> 
  </tr> 
  <tr> 
   <td> -5005 </td> 
   <td> 無効なデバイスID </td> 
  </tr> 
  <tr> 
   <td> -5006 </td> 
   <td> OPL値がありません </td> 
  </tr> 
  <tr> 
   <td> -5007 </td> 
   <td>kekまたはcontentKeyの <span class="codeph"> 1つのみ</span><span class="codeph"> 指定できます</span> 。 </td> 
  </tr> 
 </tbody> 
</table>
