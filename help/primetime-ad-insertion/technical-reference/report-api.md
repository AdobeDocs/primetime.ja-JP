---
title: レポート API
description: Auditude レポート API
source-git-commit: 7f958c83a4dd481221feb4a266440b920ac7d195
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# レポート API {#report-api}

ユーザーインターフェイスには、お客様とイネーブルメント (Adobe) チームの役割が管理されています。 お客様はポータルにアクセスし、設定を作成および編集できます。 また、ユーザーインターフェイスでの広告インプレッションのレポートを表示することもできます。

API はバックグラウンドで動作し、顧客や管理者がバックエンドインフラストラクチャとの通信を容易にします。

## API エンドポイント {#report-api-endpoint}

### 実稼動 {#production}

`https://dai-primetime.adobe.io/report`

### サンドボックス {#sandbox}

`https://dai-sandbox1-primetime.adobe.io/report`

## クエリパラメーター


| 名前 | 有意性 | 値のタイプ | 必須？ | デフォルト値 | 制約 | 例/有効なサンプル値 |
|----------|-----------------------------------------------------------------------------------------------|----------------|----------------|---------------------|------------------------------------------------------------------------------------|-------------------------------------------------------------------------|
| endDate | レポートデータの終了日 | 日付 | Y | なし | UTC-8 で昨日より新しくない | ######## |
| フィルター | 1 つ以上の列のフィルター | 文字列 | N | なし | ad_config_id 、 zone_id | ad_config_id=990,900;state=active |
|  |  |  |  |  | リクエストで metaData が「true」に設定されている場合は、名前でフィルタリングすることもできます。 |  |
|  |  |  |  |  |  | 複数のフィルターキーはセミコロンで区切ります。 |
|  |  |  |  |  |  | フィルターキーの値のリストを指定するには、値をコンマで区切って指定します |
| groupBy | オンタイム（年\|月\|日）または ad_config_id でグループ化します。 Adconfig は AdRule と同義語です。 | 文字列 | N | なし | y \| m \| d , ad_config_id | m 、 ad_config_id |
|  |  |  |  |  |  |  |
|  |  |  |  |  |  | groupBy のオンタイムの場合は、y または m または d のいずれかを指定します。 |
|  |  |  |  |  |  |  |



## ヘッダー {#headers}

| 名前 | 値のタイプ | 必須 | 値の例 | 有意性 |
|-----------------------|----------------|---------------|-------------------------------------|------------------------------------|
| 確定 | 文字列 | Y | CSV のテキスト/csv | API からの応答のタイプが必要です |
|  |  |  | application/json または&#39;*/*&#39; （JSON の場合） |  |
| 認証トークン | 文字列 | Y | xyz | 認証トークン |
| x-api-key | 文字列 | Y | xyz | API キー |
| x-gw-ims-org-id | 文字列 | Y | xyz12345 | IMS 組織アカウントの ID |

* Adobe.io の JWT 認証のヘルプページで説明されている手順に従って、認証トークン（アクセストークンとも呼ばれます）を生成できます。
   >[!NOTE]
   >認証トークンの有効期限は 24 時間なので、繰り返しスクリプトを使用して Report API を使用する場合は、有効期限の前に、またはトークンが有効でないことに関する OAUTH エラーが発生した際に、必ず認証トークンを生成してください。

* リクエストヘッダーで正しい値を設定し、認証トークンを生成するには（JWT 認証を使用）、アカウントの以下の設定を知っておく必要があります。 これらの値を取得するには、Primetime サポートチームにお問い合わせください。
テクニカルアカウント ID

   * 組織 ID
   * Api_key
   * Client_secret

## 出力 {#output}

デフォルトでのレポート API クエリの結果は、JSON 形式で表されます。この形式は、リクエストされたディメンション（groupby パラメーター）の様々な値に対するインプレッション数を指定します。 出力例を次に示します。

```JSON
[
    {
        "dates": "07-2020",
        "total_impressions": 213007041
    },
    {
        "dates": "08-2020",
        "total_impressions": 174711626
    },
    {
        "dates": "09-2020",
        "total_impressions": 102863153
    }
]
```

## エラーコードと文字列 {#error-codes-strings}

### エラー応答の形式 {#error-response-format}

マクロ&#39;code&#39;のレンダリングエラー：パラメータに指定された値が無効です `com.atlassian.confluence.ext.code.render.InvalidValueException`

```Shell
{
"error_code": "<ERROR_CODE>",
"message": "<ERROR_MESSAGE>"
}
```

次の表に、レポート API から返されるエラーコードとメッセージを示します。 認証レイヤーに関するエラーについては、 [エラーコードドキュメント](https://experienceleague.adobe.com/docs/experience-platform/landing/troubleshooting.html?lang=en#errors-and-troubleshooting) Adobe.io の

| エラーコード | エラーメッセージ |
|-----------------------|------------------------------------------|
| 4001007 | ユーザーの詳細が無効です。 |
| 4001008 | すべてのゾーンが同じアカウントからではありません。 |
| 5001010 | 内部エラーが発生しました。 |
| 4001011 | 日付は必須の形式で送信されません。 |
| 4001012 | 日付が範囲外です。 |
| 4001013 | 必須パラメーターがありません。 |
| 4001014 | アカウントのゾーンの一覧は空です。 |
| 4001015 | 要求に無効なフィルターキーがあります。 |
| 4001016 | リクエストの GroupBy オプションが無効です。 |
| 4001017 | リクエストで無効な ID が指定されています |

## サンプル呼び出しと期待される結果 {#sample-calls-expected-results}

次に、アクセストークンを使用して2020-07-01 ～ 2021-06-30の間の月別のインプレッション数を取得する curl コマンドを示します。

**レポート API 呼び出しの例**

```shell
curl --location --request GET 'https://dai-sandbox1-primetime.adobe.io/report?startDate=2020-07-01&endDate=2021-06-30&groupBy=m&unpaged=true' \
--header 'x-api-key: <API_KEY>' \
--header 'x-gw-ims-org-id: <ORG_ID>' \
--header 'Authorization: Bearer <ACCESS_TOKEN_STRING>' \
--header 'Accept: application/json'
```

| 呼び出し/使用例 | 期待される結果 |
|---|---|
| 開始日と終了日のGETを含むレポートを取得： [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2021-01-01 header :Accept = application/json または */* | このアカウントに属するすべての広告が含まれる、次のパラメーターを持つ JSON |
| GroupBy = d \| m \| yGETのレポートを取得： [API_ENDPOINT]//report?startDate=2020-01-01&amp;endDate=2020-05-01&amp;groupBy=d \| m \| y ヘッダー：Accept = application/json または */* | 次のパラメーターを持つ JSON。このアカウントの日付に属するすべての広告が含まれます（mm-dd-yyyy \| mm-yyyy \| yyyy 形式） total_impressions |
| GroupBy = ad_config_idGETでレポートを取得： [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-05-01&amp;groupBy=ad_config_id header :Accept = application/json または */* | このアカウントに属するすべての広告が含まれる、次のパラメーターを持つ JSON |
| GroupBy = d \| m \| y および ad_config_idGETを使用してレポートを取得： [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-05-01&amp;groupBy=d,ad_config_id header :Accept = application/json または */* | 次のパラメーターを持つ JSON。ad_config_id アカウントに属するすべての広告が日付（mm-dd-yyyy \| mm-yyyy \| yyyy 形式）total_impressions |
| metaData=true および groupBy=d \| m \| yGETを含むレポートを取得： [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-05-01&amp;metaData=true&amp;groupBy=ad_config_id header :Accept = application/json または */* | このアカウントに属するすべての広告が含まれる、次のパラメーターを持つ JSON。 ad_config_id name total_impressions |
| groupBy=d \| m \| y および ad_config_idGETを使用してレポートを取得： [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-05-01&amp;metaData=true&amp;groupBy=d \| m \| y,ad_config_id ヘッダー：Accept = application/json または */* | このアカウントに属するすべての広告が含まれる、次のパラメーターを持つ JSON。ad_config_id 名 total_impressions dates （mm-dd-yyyy \| mm-yyyy \| yyyy 形式） |
| レポートを取得して、指定した日付範囲（unpaged = true を含む）のすべての行を取得します。 [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-01-31&amp;groupBy=d&amp;unpaged=true | 返された JSON 配列内の 31 エントリ |
| 有効なページクエリパラメーターGETを使用してレポートを取得： [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-01-31&amp;page=0&amp;size=5&amp;groupBy=d | 返される配列の 5 個のエントリ |
| CSV 形式のGETを使用したレポートの取得： [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-01-10 header :Accept = text/csv | CSV 文字列が、ヘッダーと共に返されます。total_impressions |
| CSV 形式のレポートを取得し、groupBy = d \| m \| yGET: [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-01-10&amp;groupBy=d\|m\|y header :Accept = text/csv | CSV 文字列が、ヘッダーと共に返されます。total_impressions の日付（mm-dd-yyyy \| mm-yyyy \| yyyy 形式） |
| CSV 形式でレポートを取得し、 metadata = trueGET: [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-01-10&amp;metaData=true header :Accept = text/csv | CSV 文字列が、ヘッダーと共に返されます。total_impressions |
| CSV 形式、metadata = true および groupBy = d \| m \| yGETを使用してレポートを取得： [API_ENDPOINT]/report?startDate=2020-01-01&amp;endDate=2020-01-10&amp;metaData=true&amp;groupBy=d\|m\|y header :Accept = text/csv | CSV 文字列が、ヘッダーと共に返されます。total_impressions の日付（mm-dd-yyyy \| mm-yyyy \| yyyy 形式） |


## レポート API のスロットリングポリシー {#report-api-throttling-policy}

* 5 秒の間に、各ユーザーに対して 5 つの API リクエストが許可されます。
* ユーザーが制限を超えると、応答は 5 秒遅れます。
* 5 秒以内に 10 件を超える呼び出しをおこなった場合、「429 Too many requests」という応答で拒否されます。
