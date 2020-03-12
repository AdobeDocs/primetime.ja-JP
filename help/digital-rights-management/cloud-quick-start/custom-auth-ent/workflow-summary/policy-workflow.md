---
seo-title: ポリシーワークフローの詳細
title: ポリシーワークフローの詳細
uuid: b355fcf6-3416-440f-9b30-a155e20f9f74
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5

---


# ミツバチのワークフロー {#bees-workflow}

**概要：**

* **ポリシー** — このポリシーを使用してパッケージ化されたすべてのコンテンツにBEESが必要であることを示すDRM BEES対応ポリシーを作成します。
* **パッケージ** - BEES対応のDRMポリシーを使用してコンテンツをパッケージ化します。
* **認証** — クライアントデバイスを認証し、Primetime DRM APIまたはPrimetime APIを使用して、このトークンをPrimetime Cloud DRMに関連付けます。 この操作を行うと、クライアントデバイスは、この認証トークンをすべてのライセンス要求と共にPrimetime Cloud DRMに送信します。 Primetime Cloud DRMは、このトークンを処理せず、代わりに（不透明なBLOBとして）BEESエンドポイントに渡して処理します。
* **ライセンス** — 保護されたコンテンツのライセンスを要求します。 クライアントデバイスは、以前に設定した認証トークンを自動的に呼び出しに追加します。
* **権利付与** - Primetime Cloud DRMでは、コンテンツがBEESを必要とするポリシーでパッケージ化されていると判断されます。 Primetime Cloud DRMは、BEESエンドポイントに送信するJSONリクエストを作成します。 BEESの応答では、Primetime Cloud DRMに対して、ライセンスを発行するかどうか、およびオプションでどのDRMポリシーを使用するかを指示します。

## ポリシーワークフローの詳細 {#policy-workflow-details}

Primetime Cloud DRMは、ライセンス要求を処理する際に、要求内のDRMポリシーを解析し、コンテンツを表示する前にバックエンドエンタイトルメントサービスの呼び出しが必要かどうかを判断します。 BEES呼び出しが必要な *場合* 、Primetime Cloud DRMはBEESリクエストを作成し、DRMポリシーを解析してBEESリクエストの指定されたBEES URLエンドポイントを取得します。

BEES要件を示すDRMポリシーを適用し、ポリシーで次の2つのカスタムプロパティを指定します。

    * `policy.customProp.1=bees.required=&lt;true| false>`
    * `policy.customProp.2=bees.url=&lt;BEESエンドポイントのURL>`

<!--<a id="example_F617FC49A4824C0CB234C92E57D876D3"></a>-->

例えば、Primetime DRM Policy Manager ( [!DNL AdobePolicyManager.jar])を使用する場合、設定ファイルで次の2つのカスタムプロパティを指 [!DNL flashaccesstools.properties] 定します。

* `policy.customProp.1=bees.required=true`
* `policy.customProp.2=bees.url=https://mybeesserver.example.com/bees`

>[!NOTE]
>
>既にまたは別のプロパティを使 `policy.customProp.1` 用して `policy.customProp.2` いる場合は、新しいプロパティに一意の番号を使用します。

## パッケージワークフローの詳細 {#package-workflow-details}

Adobe Accessで保護されたコンテンツのパッケージ化中に、BEETS対応のDRMポリシーの1つをコンテンツに適用する必要があります。

## 認証ワークフローの詳細 {#authentication-workflow-details}

BEESエンドポイントがエンタイトルメントの決定を行うためには、クライアントデバイスが認証情報を提供する必要があります。 これは、独自の顧客固有の認証トークンを使用して行います。

Primetime Cloud DRMは、このトークンを理解する必要はありません。このトークンをBEESエンドポイントに渡すだけです。 クライアントデバイスは、このトークンを作成または取得し、 `DRMManager.setAuthenticationToken()` APIを使用して設定します。

次の手順を実行して、このトークンをPrimetime Cloud DRMに関連付け、ライセンスリクエストと共に送信します。

Primetime Cloud DRM用にパ `DRMManager` ッケージ化されたコンテンツのDRMメタデータを使用してオブジェクトをインスタンス化します。

このメソ `setAuthenticationToken()` ッドは、指定されたバイト配列を、インスタンス化に使用されたDRMメタデータで提供されたLicense Server URLに関連付けることで動作しま `DRMManager`す。

```java
//client device acquires auth token needed by your BEES endpoint  
DRMManager mgr = new DRMManager(<DRM Metadata of CloudDRM content>);  
mgr.setAuthenticationToken(<auth token>);
```

パラメーターにnullを指定して呼び出すことでトークンがクリアされるまで、トークンはすべてのライセ `.setAuthenticationToken` ンス要求と共に送信されます。

## ライセンスワークフローの詳細{#license-workflow-details}

を呼び出して、Primetime Cloud DRMからライセンスを要求しま `mgr.loadVoucher()`す。

## エンタイトルメントリクエストと応答の詳細{#entitlement-request-and-response-details}

Primetime Cloud DRMは、コンテンツがBEES対応のDRMポリシーでパッケージ化されたと判断すると、DRMポリシーで指定されたBEESエンドポイントに送信する次のJSON要求を構築します。

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

BEESエンドポイントから、次の応答が期待されます。

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

Primetime Cloud DRMは、応答を使用して、要求元のデバイスに対してライセンスを発行するかどうか、および新しいDRMポリシーをライセンス生成プロセスに置き換えるかどうかを決定します。 が指定さ `isAllowed` れて `true` いて、応答にポリシーが指定されていない場合は、コンテンツのパッケージ化時に使用された元のDRMポリシーがライセンスの生成に使用されます。