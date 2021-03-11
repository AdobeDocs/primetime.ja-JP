---
title: ドメイン登録要求の処理
description: ドメイン登録要求の処理
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 0%

---


# ドメイン登録要求の処理{#handling-domain-registration-requests}

DRMメタデータが、コンテンツの再生にドメイン登録が必要であることを示している場合、クライアントアプリケーションは、DRMManager.addToDeviceGroup()ActionScriptAPIまたはjoinLicenseDomain() iOS APIを呼び出す必要があります。 クライアントが指定したドメインサーバーにまだ登録していない場合（またはアプリケーションが再加入を強制している場合）は、ドメイン登録要求が送信されます。 ドメインサーバーは、クライアントがドメインに参加することを許可されているかどうかを判断し、クライアントに1つ以上のドメイン資格情報を発行します。

* リクエストハンドラークラスは`com.adobe.flashaccess.sdk.protocol.domain.DomainRegistrationHandler`です
* 要求メッセージクラスは`com.adobe.flashaccess.sdk.protocol.domain.DomainRegistrationRequestMessage`です
* クライアントとサーバーの両方がプロトコルバージョン5をサポートしている場合、要求URLは「メタデータのドメインサーバーURL:+ 「/flashaccess/domain/v4」)。 それ以外の場合、リクエストURLは、メタデータのドメインサーバーURL + &quot;/flashaccess/domain/v3&quot;です

`DomainRegistrationHandler`を初期化する場合は、ドメインサーバーのURLを指定する必要があります。 このURLは、トークンを発行したドメインサーバーを示すために、ハンドラーが発行するドメイントークンに含まれます。 URLは、サーバーとのドメイン登録を必要とするポリシーで指定されたドメインサーバーのURLと一致する必要があります。

クライアントがドメインに参加することを許可されているかどうかを判断するために、サーバは、要求内のマシンとユーザ情報を調べることができます。 ドメインに参加するマシンの識別方法とカウント方法については、[マシン識別子の使用](../../aaxs-protecting-content/content-implementing-the-license-server/content-processing-aaxs-requests/content-using-machine-ids.md)を参照してください。 サーバーは、クライアントが参加を許可されているドメインも決定できます。 クライアントは、ドメインサーバーのURLごとに1つのドメインのメンバーにすることのみ可能です。 コンピューターにこのドメインサーバーURLのドメイントークンが既に存在する場合、ドメイン登録要求には現在のドメイン名(`getRequestDomainName()`)が含まれます。 再参加要求の場合、ドメインサーバーは、このドメインの現在のドメイン資格情報のセットを返すか、エラーを返す必要があります（ドメインサーバーは、別のドメインのドメイン資格情報を返さない場合があります）。

ドメインサーバーがドメインに参加するために認証が必要な場合、要求には認証トークンが含まれている必要があります。 ライセンス要求と同様に、ドメイン登録にはユーザ名/パスワードまたはカスタム認証が必要になる場合があります。 認証トークンの処理の詳細については、[ユーザー認証](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-authentication/content-user-authentication.md)を参照してください。

ドメインサーバーは、各ドメインに関連付けられたドメインキーの保存と管理を行います。 ドメインに対して新しいキーペアを生成する必要がある場合（ドメインの最初のドメイン登録）、`generateDomainCredential` `(String, int, Principal, Date)`を呼び出します。 このメソッドは、新しいドメインキーペアとドメイン証明書を生成します。 ドメインサーバーは、秘密鍵と証明書を格納し、このドメインに対する以降の要求を処理する際に、これらのオブジェクトを提供する必要があります。 また、ドメインの新しいキーペアを生成して、キーをロールオーバーすることもできます。 特定のドメインのキーをロールオーバーする場合は、`generateDomainCredential`のキーのバージョンも増やす必要があります。

その後、マシンが同じドメインに登録するたびに、同じドメインの秘密鍵と証明書を使用する必要があります。 `addDomainCredential(DomainToken, PrivateKey)`を呼び出して、既存のドメインの秘密鍵証明書をクライアントに返します。 ドメインキーが変更されたために、ドメインに対する複数のドメイン資格情報が存在する場合は、クライアントが古いドメインキーにバインドされたライセンスを使用できるように、現在のドメインキーと以前のすべてのドメインキーに対するドメイン資格情報を提供する必要があります。 これにより、古いドメイントークンにバインドされたライセンスを新たに登録されたマシンに移動して、引き続き再生可能にする。
