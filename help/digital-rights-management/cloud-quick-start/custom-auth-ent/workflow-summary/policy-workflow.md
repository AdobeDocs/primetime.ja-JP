---
title: ポリシーワークフローの詳細
description: ポリシーワークフローの詳細
copied-description: true
exl-id: e3daf7a9-def0-48a9-8190-adb25eec7b59
source-git-commit: 0019a95fa9ca6d21249533d559ce844897ab67cf
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 0%

---

# ハチのワークフロー {#bees-workflow}

**概要：**

* **ポリシー**  — チスポリシーを使用してパッケージ化されたすべてのコンテンツに BEES が必要であることを示す DRM BEES 対応ポリシーを作成します。
* **パッケージ** - BEES 対応の DRM ポリシーを使用してコンテンツをパッケージ化します。
* **認証**  — クライアントデバイスを認証し、Primetime DRM API または Primetime API を使用して、このトークンを Primetime Cloud DRM に関連付けます。 これをおこなうと、クライアントデバイスはこの認証トークンを Primetime Cloud DRM まで、すべてのライセンスリクエストと共に送信します。 Primetime Cloud DRM はこのトークンを処理しませんが、代わりに BEES エンドポイントに（不透明な塗りとして）渡して処理します。
* **ライセンス**  — 保護されたコンテンツのライセンスをリクエストします。 クライアントデバイスは、以前に設定した認証トークンを自動的に呼び出しに追加します。
* **使用権限** - Primetime Cloud DRM は、コンテンツが BEES を必要とするポリシーでパッケージ化されたかを判断します。 Primetime Cloud DRM は、BEES エンドポイントに送信する JSON リクエストを構築します。 BEES の応答は、Primetime Cloud DRM に対して、ライセンスを発行するかどうか、および必要に応じて、使用する DRM ポリシーを指示します。

## ポリシーワークフローの詳細 {#policy-workflow-details}

Primetime Cloud DRM がライセンスリクエストを処理する場合、リクエスト内の DRM ポリシーを解析して、コンテンツを表示する前にバックエンドエンタイトルメントサービスの呼び出しが必要かどうかを判断します。 もし蜂が呼ぶなら *が* 必須の場合、Primetime Cloud DRM は BEES リクエストを作成し、DRM ポリシーを解析して BEES リクエストに対して指定された BEES URL エンドポイントを取得します。

BEES 要件を示す DRM ポリシーを適用し、ポリシーで次の 2 つのカスタムプロパティを指定します。

* `policy.customProp.1=bees.required=<true | false>`
* `policy.customProp.2=bees.url=<url to your BEES endpoint>`

<!--<a id="example_F617FC49A4824C0CB234C92E57D876D3"></a>-->

例えば、Primetime DRM Policy Manager ( [!DNL AdobePolicyManager.jar]) の場合、次の 2 つのカスタムプロパティを [!DNL flashaccesstools.properties] 設定ファイル：

* `policy.customProp.1=bees.required=true`
* `policy.customProp.2=bees.url=https://mybeesserver.example.com/bees`

>[!NOTE]
>
>既に `policy.customProp.1` または `policy.customProp.2` 別のプロパティの場合は、新しいプロパティに一意の番号を使用します。

## パッケージワークフローの詳細 {#package-workflow-details}

Adobeのアクセスで保護されたコンテンツをパッケージ化する際に、BEES 対応の DRM ポリシーの 1 つをコンテンツに適用する必要があります。

## 認証ワークフローの詳細 {#authentication-workflow-details}

BEES エンドポイントがエンタイトルメントの決定をおこなうには、クライアントデバイスが認証情報を提供する必要があります。 これを実現するには、独自の顧客固有の認証トークンを使用します。

Primetime Cloud DRM は、このトークンを理解する必要はありません。単に、このトークンを BEES エンドポイントに渡します。 クライアントデバイスは、このトークンの作成または取得と、 `DRMManager.setAuthenticationToken()` API

次の手順を実行して、このトークンを Primetime Cloud DRM に関連付け、ライセンスリクエストと共に送信します。

をインスタンス化します。 `DRMManager` オブジェクトには、Primetime Cloud DRM 用にパッケージ化されたコンテンツの DRM メタデータが含まれます。

この `setAuthenticationToken()` メソッドは、指定されたバイト配列と、のインスタンス化に使用された DRM メタデータで指定されたライセンスサーバー URL を関連付けることで機能します `DRMManager`.

```java
//client device acquires auth token needed by your BEES endpoint  
DRMManager mgr = new DRMManager(<DRM Metadata of CloudDRM content>);  
mgr.setAuthenticationToken(<auth token>);
```

を呼び出してトークンがクリアされるまで、トークンはすべてのライセンス要求と共に送信されます。 `.setAuthenticationToken` パラメーターに null を使用します。

## ライセンスワークフローの詳細{#license-workflow-details}

を呼び出して、Primetime Cloud DRM からライセンスをリクエストします。 `mgr.loadVoucher()`.

## 使用権限のリクエストと応答の詳細{#entitlement-request-and-response-details}

Primetime Cloud DRM は、コンテンツが BEES 対応の DRM ポリシーでパッケージ化されたと判断すると、DRM ポリシーで指定された BEES エンドポイントに送信する次の JSON リクエストを作成します。

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

BEES エンドポイントから、次の応答が期待されます。

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

Primetime Cloud DRM は応答を使用して、要求元のデバイスにライセンスを発行するかどうか、および新しい DRM ポリシーをライセンス生成プロセスに置き換えるかどうかを決定します。 If `isAllowed` が `true` 応答にポリシーが指定されていない場合は、コンテンツのパッケージ化時に使用された元の DRM ポリシーがライセンスの生成に使用されます。
