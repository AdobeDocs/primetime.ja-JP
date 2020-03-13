---
seo-title: ドメイン登録解除要求の処理
title: ドメイン登録解除要求の処理
uuid: 6f056b2b-374d-4e4d-926a-68605b2c923b
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# ドメイン登録解除要求の処理{#handling-domain-de-registration-requests}

クライアントアプリケーションがドメインを離脱する必要がある場合は、 `DRMManager.removeFromDeviceGroup()`ActionScript APIまたは `leaveLicenseDomain()` iOS APIを呼び出して、ドメインの登録解除プロセスを開始します。 ドメインの登録解除は2段階のプロセスです。 クライアントは、最初に登録解除プレビュー要求を送信します。 ドメインサーバーは要求を調べ、クライアントがドメインを離脱できるかどうかを判断します（コンピューターが現在ドメインに属していない場合は、エラーが返される可能性があります）。 応答が成功すると、クライアントはドメインの資格情報とそのドメインに発行されたライセンスを削除し、登録解除要求を送信します。

* リクエストハンドラークラスは、 `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationHandler`
* リクエストメッセージクラスは `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationRequestMessage`
* クライアントとサーバーの両方がプロトコルバージョン5をサポートしている場合、要求URLは「Domain Server URL in metadata:+ &quot;/flashaccess/dereg/v4&quot; それ以外の場合、要求URLは、メタデータのドメインサーバーURL + &quot;/flashaccess/dereg/v3&quot;です。

ドメインの登録解除要求を処理する場合、サーバーは、クライ `getRequestPhase()` アントがプレビュー段階にあるか登録解除段階にあるかを判断します。 プレビュー段階で、ドメインサーバーは要求を調べ、クライアントがドメインを離脱できるかどうかを判断します(要求は拒否される場合があります（例えば、マシンが現在ドメインに属していない場合など）。 登録解除段階で、サーバーはマシンがドメインを離れたことを記録します。 サーバは、実際の登録解除要求と同じロジックをプレビュー要求で評価し、2番目のフェーズが失敗する可能性を最小限に抑えることを強くお勧めします。
