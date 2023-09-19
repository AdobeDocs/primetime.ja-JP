---
title: ドメイン登録解除要求の処理
description: ドメイン登録解除要求の処理
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# ドメイン登録解除要求の処理 {#handle-domain-de-registration-requests}

クライアントアプリケーションがドメインを離れる必要がある場合は、 `DRMManager.removeFromDeviceGroup()`ActionScriptAPI または `leaveLicenseDomain()` ドメインの登録解除プロセスを開始するためのiOS API。 ドメインの登録解除は、2 つの段階のプロセスです。 クライアントは、最初に登録解除のプレビューリクエストを送信します。 ドメインサーバは、要求を調べ、クライアントがドメインを離脱できるかどうかを判断する。 コンピューターが現在ドメインに含まれていない場合は、エラーが返される場合があります。 応答が成功すると、クライアントはそのドメインの資格情報と、そのドメインに対して発行されたライセンスが削除されます。 その後、登録解除リクエストを送信します。

* リクエストハンドラークラスは、 `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationHandler`
* リクエストメッセージクラスは、 `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationRequestMessage`
* クライアントとサーバーの両方がプロトコルバージョン 5 をサポートしている場合、要求 URL は「Domain Server URL in metadata: + 」です。 [!DNL /flashaccess/dereg/v4]&quot;. それ以外の場合、要求 URL は、「メタデータのドメインサーバー URL」+「 [!DNL /flashaccess/dereg/v3]&quot;

ドメイン登録解除要求を処理する際、サーバーは `getRequestPhase()` を使用して、クライアントがプレビュー段階にあるか登録解除段階にあるかを判断します。 プレビューフェーズでは、ドメインサーバーは要求を調べ、要求が拒否されるので、クライアントがドメインを離脱できるかどうかを判断します。例えば、マシンが現在ドメインに属していない場合は要求が拒否されます。 登録解除フェーズで、サーバーは、マシンがドメインを離れたという事実を記録します。 第 2 段階が失敗する可能性を最小限に抑えるために、サーバーは、実際の登録解除要求と同じロジックをプレビュー要求で評価することを強くお勧めします。
