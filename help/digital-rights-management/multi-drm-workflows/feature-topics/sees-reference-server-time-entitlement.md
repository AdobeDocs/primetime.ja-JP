---
description: SEESと連携して、ExpressPlayを使用して時間ベースのエンタイトルメントサービスを有効にする方法を確認します。
title: リファレンスサービスの時間ベースのエンタイトルメント
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---


# リファレンスサービス：時間ベースのエンタイトルメント{#reference-service-time-based-entitlement}

SEESと連携して、ExpressPlayを使用して時間ベースのエンタイトルメントサービスを有効にする方法を確認します。

SEESは、クライアントからエンタイトルメント要求（「公開API」の節を参照）を受け取ります。 SEESサーバーは、`contentID`に基づいてCEKとIVを調べ、`expirationTime`を追加して、リクエストをExpressPlayサーバーに転送します。 最後のExpressPlayトークンはタイムバインドです。 以下の時間ベースのエンタイトルメントシーケンス図を参照してください。![](assets/fees-time-based.png)

**表1:クライアントから送信されたライセンスパラメータ**

| クエリパラメータ | 説明 | 必須 |
|---|---|---|
| `contentKey` | コンテンツ暗号化キーの16バイトの16進文字列表現です | はい |
| `iv` | コンテンツ暗号化IVの16バイトの16進文字列表現です。 | はい |
| `rentalDuration` | 秒単位のレンタル期間（デフォルト= 0） | いいえ |

**表2:SEESサーバによって追加されたトークン制限パラメータ**

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
   <td>このトークンの有効期限。 この値は、Zゾーン指定子（「ズールー時間」）の<a href="https://www.ietf.org/rfc/rfc3339.txt" format="html" type="external"> RFC 3339</a>日付/時刻形式の文字列か、前に+符号の付いた整数である必要があります。 RFC 3339日付/時刻の例は、<span class="codeph"> 2006-04-14T12:01:10Z</span>です。 <p>値がRFC 3339日付/時刻形式の文字列である場合は、トークンの絶対的な有効期限切れ日時を表します。 値が前に+符号の付いた整数である場合、発行後のトークンの有効な相対秒数として解釈されます。 例えば、<span class="codeph"> +60</span>は1分を表します。 トークンの有効期間の最大値（および指定しない場合のデフォルト）は30日です。 「+」記号を指定する場合は、エンコードされたフォーム「%2B」を使用します。 </p> </td> 
   <td> いいえ </td> 
  </tr> 
 </tbody> 
</table>

