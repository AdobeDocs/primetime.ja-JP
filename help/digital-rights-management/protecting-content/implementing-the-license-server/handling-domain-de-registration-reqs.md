---
seo-title: ドメイン登録解除要求の処理
title: ドメイン登録解除要求の処理
uuid: 80dbbb60-9005-4a3d-86bf-26cdbed86452
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# ドメイン登録解除要求の処理 {#handle-domain-de-registration-requests}

クライアントアプリケーションがドメインを離脱する必要がある場合は、 `DRMManager.removeFromDeviceGroup()`ActionScript APIまたは `leaveLicenseDomain()` iOS APIを呼び出して、ドメインの登録解除プロセスを開始します。 ドメインの登録解除は2段階のプロセスです。 クライアントは、最初に登録解除プレビュー要求を送信します。 ドメインサーバーは要求を調べ、クライアントがドメインを離脱できるかどうかを判断します。 マシンが現在ドメインに属していない場合は、エラーが返される可能性があります。 応答が成功すると、クライアントはそのドメインの資格情報と、そのドメインに発行されたライセンスを削除します。 次に、登録解除要求を送信します。

* リクエストハンドラークラスは、 `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationHandler`
* リクエストメッセージクラスは `com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationRequestMessage`
* クライアントとサーバーの両方がプロトコルバージョン5をサポートしている場合、要求URLは「Domain Server URL in metadata:+ &quot; [!DNL /flashaccess/dereg/v4]&quot; それ以外の場合、要求URLは、メタデータ&quot; + &quot; [!DNL /flashaccess/dereg/v3]&quot;のドメインサーバーURLです

ドメインの登録解除要求を処理する場合、サーバーは、クライ `getRequestPhase()` アントがプレビュー段階にあるか登録解除段階にあるかを判断します。 プレビュー段階で、ドメインサーバーは要求を調べ、要求が拒否される可能性があるので、クライアントがドメインを離脱できるかどうかを判断します。例えば、マシンが現在ドメインに属していない場合、要求が拒否される可能性があります。 登録解除段階で、サーバーはマシンがドメインを離れたことを記録します。 サーバは、実際の登録解除要求と同じロジックをプレビュー要求で評価し、2番目のフェーズが失敗する可能性を最小限に抑えることを強くお勧めします。
