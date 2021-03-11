---
title: ドメイン登録解除要求の処理
description: ドメイン登録解除要求の処理
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---


# ドメイン登録解除要求の処理{#handling-domain-de-registration-requests}

クライアントアプリケーションがドメインを離れる必要がある場合は、`DRMManager.removeFromDeviceGroup()`ActionScriptAPIまたは`leaveLicenseDomain()` iOS APIを呼び出してドメインの登録解除プロセスを開始します。 ドメインの登録解除は2段階のプロセスです。 クライアントは、最初に登録解除プレビュー要求を送信します。 ドメインサーバーは要求を調べ、クライアントがドメインからの離脱を許可されているかどうかを判断します（コンピューターが現在ドメインに属していない場合は、エラーが返される場合があります）。 応答が成功すると、クライアントはそのドメインの資格情報とそのドメインに発行されたライセンスを削除し、登録解除要求を送信します。

* リクエストハンドラークラスは`com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationHandler`です
* 要求メッセージクラスは`com.adobe.flashaccess.sdk.protocol.domain.DomainDeRegistrationRequestMessage`です
* クライアントとサーバーの両方がプロトコルバージョン5をサポートしている場合、要求URLは「メタデータのドメインサーバーURL:+ &quot;/flashaccess/dereg/v4&quot; それ以外の場合、リクエストURLは、メタデータのドメインサーバーURL + &quot;/flashaccess/dereg/v3&quot;です

ドメイン登録解除要求を処理する場合、サーバーは`getRequestPhase()`を使用して、クライアントがプレビュー段階にあるか登録解除段階にあるかを判断します。 プレビュー段階で、ドメインサーバーは要求を調べ、クライアントがドメインを離脱することを許可されるかどうかを判断します(要求は拒否される場合があります（マシンが現在ドメインに属していない場合など）。 登録解除段階で、サーバーは、マシンがドメインから離れたことを記録します。 2番目のフェーズが失敗する可能性を最小限に抑えるために、サーバは、実際の登録解除要求と同じロジックをプレビュー要求で評価することを強くお勧めします。
