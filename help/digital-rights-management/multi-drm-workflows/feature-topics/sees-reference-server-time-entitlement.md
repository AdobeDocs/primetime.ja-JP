---
description: SEESと協力して、ExpressPlayを使用して時間ベースのエンタイトルメントサービスを有効にする方法を確認します。
seo-description: SEESと協力して、ExpressPlayを使用して時間ベースのエンタイトルメントサービスを有効にする方法を確認します。
seo-title: リファレンスサービスの時間ベースのエンタイトルメント
title: リファレンスサービスの時間ベースのエンタイトルメント
uuid: dd937299-a271-49a9-9b26-eec16f1484df
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c

---


# リファレンスサービス：時間ベースの権利付与 {#reference-service-time-based-entitlement}

SEESと協力して、ExpressPlayを使用して時間ベースのエンタイトルメントサービスを有効にする方法を確認します。

SEESは、クライアントからエンタイトルメント要求（「公開API」を参照）を受け取ります。 SEESサーバーは、CEKとIVを基に検索し、そ `contentID`の要求を追 `expirationTime`加して、ExpressPlayサーバーに転送します。 最終的なExpressPlayトークンはタイムバインドです。 後述の時間ベースのエンタイトルメントシーケンス図を参照してください。 ![](assets/fees-time-based.png)

**表1:クライアントから送信されたライセンスパラメータ**

| クエリパラメータ | 説明 | 必須 |
|---|---|---|
| `contentKey` | コンテンツ暗号化キーの16バイトの16進文字列表現です。 | はい |
| `iv` | コンテンツ暗号化IVの16バイトの16進文字列表現です。 | はい |
| `rentalDuration` | 秒単位のレンタル期間（デフォルト= 0） | いいえ |

**表2:SEESサーバーによって追加されたトークン制限パラメーター**

<table id="table_E979FAD7A61A4832A46667301939FAEB">  
 <thead> 
  <tr> 
   <th class="entry"> クエリパラメータ </th> 
   <th class="entry"> 説明 </th> 
   <th class="entry"> 必須？ </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td><span class="codeph"> expirationTime</span> </td> 
   <td>このトークンの有効期限。 この値は、 <a href="https://www.ietf.org/rfc/rfc3339.txt" format="html" type="external"> RFC 3339</a> 日付/時刻形式の文字列(Zゾーン指定子（「ズールー時間」）、または前に+符号の付いた整数である必要があります。 RFC 3339の日付/時刻の例は、 <span class="codeph"> 2006-04-14T12:01:10Zです</span>。 <p>値がRFC 3339日付/時刻形式の文字列である場合、トークンの絶対有効期限切れ日時を表します。 値が前に+符号の付いた整数の場合、トークンが有効であることを発行後の相対秒数として解釈されます。 例えば、 <span class="codeph"> +60は1分を表し</span> ます。 トークンの最長有効期間（および指定しなかった場合のデフォルト）は30日です。 「+」記号を指定する場合は、エンコードされたフォーム「%2B」を使用します。 </p> </td> 
   <td> いいえ </td> 
  </tr> 
 </tbody> 
</table>

