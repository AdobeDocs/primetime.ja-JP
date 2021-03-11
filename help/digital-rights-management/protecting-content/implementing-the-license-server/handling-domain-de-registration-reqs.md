---
title: ドメイン登録解除要求の処理
description: ドメイン登録解除要求の処理
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---


# ドメイン登録解除要求を処理する{#handle-domain-de-registration-requests}

クライアントアプリケーションがドメインを離れる必要がある場合は、`DRMManager.removeFromDeviceGroup()`ActionScriptAPIまたは`leaveLicenseDomain()` iOS APIを呼び出してドメインの登録解除プロセスを開始します。 ドメインの登録解除は2段階のプロセスです。 クライアントは、最初に登録解除プレビュー要求を送信します。 ドメインサーバは、要求を調べ、クライアントがドメインからの離脱を許可されているかどうかを判断する。 マシンが現在ドメインに属していない場合は、エラーが返される場合があります。 応答が成功すると、クライアントはそのドメインの資格情報と、そのドメインに発行されたすべてのライセンスを削除します。 その後、登録解除リクエストが送信されます。

* リクエストハンドラークラスは`com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationHandler`です
* 要求メッセージクラスは`com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationRequestMessage`です
* クライアントとサーバーの両方がプロトコルバージョン5をサポートしている場合、要求URLは「メタデータのドメインサーバーURL:+ &quot; [!DNL /flashaccess/dereg/v4]&quot;。 それ以外の場合、要求URLは、メタデータ&quot; + &quot; [!DNL /flashaccess/dereg/v3]&quot;のドメインサーバーURLです

ドメイン登録解除要求を処理する場合、サーバーは`getRequestPhase()`を使用して、クライアントがプレビュー段階にあるか登録解除段階にあるかを判断します。 プレビュー段階では、ドメインサーバーは要求を調べ、要求が拒否される可能性があるので、クライアントがドメインを離脱できるかどうかを判断します。例えば、マシンが現在ドメインに属していない場合は、要求が拒否される可能性があります。 登録解除段階で、サーバーは、マシンがドメインから離れたことを記録します。 2番目のフェーズが失敗する可能性を最小限に抑えるために、サーバは、実際の登録解除要求と同じロジックをプレビュー要求で評価することを強くお勧めします。
