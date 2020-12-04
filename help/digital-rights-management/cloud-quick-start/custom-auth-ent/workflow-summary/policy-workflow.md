---
seo-title: ポリシーワークフローの詳細
title: ポリシーワークフローの詳細
uuid: b355fcf6-3416-440f-9b30-a155e20f9f74
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 0%

---


# BEESワークフロー{#bees-workflow}

**サマリ：**

* **ポリシー**  — このポリシーを使用してパッケージ化されたすべてのコンテンツにBEESが必要であることを示すDRM BEES対応ポリシーを作成します。
* **パッケージ化** - BEES対応のDRMポリシーを使用してコンテンツをパッケージ化します。
* **認証**  — クライアントデバイスを認証し、Primetime DRM APIまたはPrimetime APIを使用して、このトークンをPrimetime Cloud DRMに関連付けます。これを行うと、クライアントデバイスは、この認証トークンをPrimetime Cloud DRMまで、すべてのライセンス要求と共に送信します。 Primetime Cloud DRMはこのトークンを処理せず、代わりにBEESエンドポイントに（不透明なBLOBとして）渡して処理します。
* **ライセンス**  — 保護されたコンテンツのライセンスを要求します。クライアントデバイスは、以前に設定した認証トークンを自動的に呼び出しに追加します。
* **エンタイトルメント** - Primetime Cloud DRMでは、コンテンツがBEESを必要とするポリシーでパッケージ化されていることが判断されます。Primetime Cloud DRMは、BEESエンドポイントに送信するJSONリクエストを作成します。 BEESの応答は、Primetime Cloud DRMに対して、ライセンスを発行するかどうか、およびオプションでどのDRMポリシーを使用するかについて指示します。

## ポリシーワークフローの詳細{#policy-workflow-details}

Primetime Cloud DRMは、ライセンスリクエストを処理する際に、リクエスト内のDRMポリシーを解析し、コンテンツを表示する前にバックエンドエンタイトルメントサービスの呼び出しが必要かどうかを判断します。 BEESが&#x200B;*is*&#x200B;を呼び出す必要がある場合、Primetime Cloud DRMはBEESリクエストを作成し、DRMポリシーを解析して、BEESリクエスト用に指定されたBEES URLエンドポイントを取得します。

BEES要件を示すDRMポリシーを適用します。ポリシーで次の2つのカスタムプロパティを指定します。

    * `policy.customProp.1=bees.required=&lt;true>`
    * `policy.customProp.2=bees.url=&lt;url to=&quot;&quot; your=&quot;&quot; BEES=&quot;&quot; endpoint=&quot;&quot;>`

<!--<a id="example_F617FC49A4824C0CB234C92E57D876D3"></a>-->

例えば、Primetime DRMポリシーマネージャー([!DNL AdobePolicyManager.jar])を使用する場合、次の2つのカスタムプロパティを[!DNL flashaccesstools.properties]設定ファイルに指定します。

* `policy.customProp.1=bees.required=true`
* `policy.customProp.2=bees.url=https://mybeesserver.example.com/bees`

>[!NOTE]
>
>既に別のプロパティに`policy.customProp.1`または`policy.customProp.2`を使用している場合は、新しいプロパティに一意の番号を使用します。

## パッケージワークフローの詳細{#package-workflow-details}

Adobeのアクセス保護コンテンツをパッケージ化する際に、BEES対応のDRMポリシーの1つをコンテンツに適用する必要があります。

## 認証ワークフローの詳細{#authentication-workflow-details}

BEESエンドポイントでエンタイトルメントの決定を行うには、クライアントデバイスが認証情報を提供する必要があります。 これは、独自の顧客固有の認証トークンを使用して行います。

Primetime Cloud DRMは、このトークンを理解する必要はありません。このトークンは、BEESエンドポイントに渡されるだけです。 クライアントデバイスは、このトークンを作成または取得し、`DRMManager.setAuthenticationToken()` APIを使用して設定します。

次の手順を実行して、このトークンをPrimetime Cloud DRMに関連付け、ライセンスリクエストと共に送信します。

Primetime Cloud DRM用にパッケージ化されたコンテンツのDRMメタデータを使用して`DRMManager`オブジェクトをインスタンス化します。

`setAuthenticationToken()`メソッドは、指定されたバイト配列を、`DRMManager`のインスタンス化に使用されたDRMメタデータで指定されたLicense Server URLに関連付けます。

```java
//client device acquires auth token needed by your BEES endpoint  
DRMManager mgr = new DRMManager(<DRM Metadata of CloudDRM content>);  
mgr.setAuthenticationToken(<auth token>);
```

`.setAuthenticationToken`を呼び出し、パラメーターにnullを指定してトークンをクリアするまで、トークンはすべてのライセンスリクエストと共に送信されます。

## ライセンスワークフローの詳細{#license-workflow-details}

`mgr.loadVoucher()`を呼び出して、Primetime Cloud DRMにライセンスを要求します。

## エンタイトルメントリクエストと応答の詳細{#entitlement-request-and-response-details}

Primetime Cloud DRMは、コンテンツがBEES対応DRMポリシーでパッケージ化されたと判断すると、DRMポリシーで指定されたBEESエンドポイントに送信する次のJSON要求を構築します。

```
{
    "title":"Entitlement Request",
    "type":"object",
    "properties": {
        "messageID": {
            "type":"string",
            "description":"Unique ID for this message. Used to confirm that the
                           returned response is for this particular message."
        },
        "version": {
            "type":"string",
            "description":"BEES Request Version. Currently 1."
        },
        "contentID": {
            "type":"string",
            "description":"Content ID (GUID)"
        },
        "customerSpecificAuthToken": {
            "type":"string",
            "description":"Base64-encoded authentication token. Must be set
                           explicitly by client before making the license request."
        }
    },
    "required": [
        "messageID",
        "version",
        "contentID"
    ]
}
```

BEESエンドポイントから、次の応答が必要です。

```
{
    "title":"Entitlement Response",
    "type":"object",
    "properties": {
        "messageID": {
            "type":"string",
            "description":"ID of the Entitlement Request that this Response is
                           handling. Must exactly match the ID of the request
                           or this response will be rejected."
        },
        "version": {
            "type":"string",
            "description":"BEES Response Version. Currently 1."
        },
        "isAllowed": {
            "type":"boolean",
            "description":"Grant the license or not."
        },
        "policy": {
            "type":"string",
            "description":"Base64-encoded policy to enforce  If no policy is
                           provided, the policy that was packaged with the content
                           during packaging time will be used to generate the license."
        },
        "error": {
            "type":"integer",
            "description":"An error number produced by the entitlement server.
                           Will be passed to the client as the 'code' field of
                           the server error response."
        },
        "errorText": {
            "type":"string",
            "description":"Additional error information produced by the
                           entitlement server. Will be passed to the client as
                           the 'text' field of the server error response."
        }
    },
    "required": [
        "messageID",
        "version",
        "isAllowed"
    ]
}
```

Primetime Cloud DRMは、応答を使用して、要求元のデバイスにライセンスを発行するかどうか、および新しいDRMポリシーをライセンス生成プロセスに置き換えるかどうかを決定します。 `isAllowed`が`true`で、応答にポリシーが指定されていない場合は、コンテンツのパッケージ化時に使用される元のDRMポリシーを使用してライセンスが生成されます。