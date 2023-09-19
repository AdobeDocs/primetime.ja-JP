---
title: ドメイン登録解除要求の処理
description: ドメイン登録解除要求の処理
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# ドメイン登録解除要求の処理{#handling-domain-de-registration-requests}

クライアントアプリケーションがドメインを離れる必要がある場合は、 `DRMManager.removeFromDeviceGroup()`ActionScriptAPI または `leaveLicenseDomain()` ドメインの登録解除プロセスを開始するためのiOS API。 ドメインの登録解除は、2 つの段階のプロセスです。 クライアントは、最初に登録解除のプレビューリクエストを送信します。 ドメインサーバーは要求を調べ、クライアントがドメインを離脱できるかどうかを判断します（マシンが現在ドメインに含まれていない場合は、エラーが返される場合があります）。 応答が成功すると、クライアントはドメインの資格情報と、そのドメインに発行されたライセンスを削除し、登録解除要求を送信します。

* リクエストハンドラークラスは、 `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationHandler`
* リクエストメッセージクラスは、 `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationRequestMessage`
* クライアントとサーバーの両方がプロトコルバージョン 5 をサポートしている場合、要求 URL は「Domain Server URL in metadata: + &quot;/flashaccess/dereg/v4」です。 それ以外の場合、要求 URL は、メタデータのドメインサーバー URL です。&quot; + &quot;/flashaccess/dereg/v3&quot;

ドメイン登録解除要求を処理する際、サーバーは `getRequestPhase()` を使用して、クライアントがプレビュー段階にあるか登録解除段階にあるかを判断します。 プレビューフェーズで、ドメインサーバーはリクエストを調べ、クライアントがドメインを離脱できるかどうかを判断します（例えば、マシンが現在ドメインに属していない場合は、リクエストが拒否される可能性があります）。 登録解除フェーズで、サーバーは、マシンがドメインを離れたという事実を記録します。 第 2 段階が失敗する可能性を最小限に抑えるために、サーバーは、実際の登録解除要求と同じロジックをプレビュー要求で評価することを強くお勧めします。
