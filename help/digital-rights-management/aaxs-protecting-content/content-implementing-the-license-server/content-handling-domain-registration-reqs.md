---
title: ドメイン登録要求の処理
description: ドメイン登録要求の処理
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 0%

---

# ドメイン登録要求の処理{#handling-domain-registration-requests}

DRM メタデータがコンテンツの再生にドメインの登録が必要であることを示している場合、クライアントアプリケーションは DRMManager.addToDeviceGroup()ActionScriptAPI または joinLicenseDomain() iOS API を呼び出す必要があります。 クライアントが指定されたドメインサーバーにまだ登録していない場合（またはアプリケーションが再加入を強制する場合）は、ドメイン登録要求が送信されます。 ドメインサーバは、クライアントがドメインに参加することを許可するかどうかを判断し、1 つ以上のドメイン資格情報をクライアントに発行します。

* リクエストハンドラークラスは、 `com.adobe.flashaccess.sdk.protocol.domain.DomainRegistrationHandler`
* リクエストメッセージクラスは、 `com.adobe.flashaccess.sdk.protocol.domain.DomainRegistrationRequestMessage`
* クライアントとサーバーの両方がプロトコルバージョン 5 をサポートしている場合、要求 URL は「Domain Server URL in metadata: + &quot;/flashaccess/domain/v4」になります。 それ以外の場合、要求 URL は、メタデータのドメインサーバー URL です。&quot; + &quot;/flashaccess/domain/v3&quot;

を初期化する際に `DomainRegistrationHandler`の場合は、ドメインサーバー URL を指定する必要があります。 この URL は、トークンを発行したドメインサーバーを示すために、ハンドラーが発行したドメイントークンに含まれます。 この URL は、サーバーとのドメイン登録を必要とするポリシーで指定されたドメインサーバー URL と一致する必要があります。

クライアントがドメインに参加するのを許可されているかどうかを判断するために、サーバはリクエスト内のマシンとユーザ情報を調べることができます。 詳しくは、 [マシン識別子の使用](../../aaxs-protecting-content/content-implementing-the-license-server/content-processing-aaxs-requests/content-using-machine-ids.md) ドメインに参加しているマシンを識別してカウントする方法については、を参照してください。 また、サーバは、クライアントがどのドメインに参加するかを決定する場合もあります。 クライアントは、ドメインサーバー URL ごとに 1 つのドメインのメンバーにすることができます。 コンピューターにこのドメインサーバー URL のドメイントークンが既に存在する場合、ドメイン登録要求には現在のドメイン名 ( `getRequestDomainName()`) をクリックします。 再参加要求の場合、ドメインサーバーは、このドメインの現在のドメイン資格情報のセットを返すか、エラーを返す必要があります（ドメインサーバーは、別のドメインのドメイン資格情報を返さない場合があります）。

ドメインサーバーがドメインに参加するために認証が必要な場合は、リクエストに認証トークンを含める必要があります。 ライセンスリクエストと同様に、ドメイン登録には、ユーザー名/パスワードまたはカスタム認証が必要な場合があります。 詳しくは、 [ユーザー認証](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-authentication/content-user-authentication.md) 認証トークンの処理の詳細については、を参照してください。

ドメインサーバーは、各ドメインに関連付けられたドメインキーの保存と管理を担当します。 ドメインに対して新しいキーペアを生成する必要がある場合（ドメインの最初のドメイン登録）、を呼び出します。 `generateDomainCredential` `(String, int, Principal, Date)`. このメソッドは、新しいドメインキーペアとドメイン証明書を生成します。 ドメインサーバーは、このドメインに対する以降の要求を処理する際に、秘密鍵と証明書を保存し、これらのオブジェクトを提供する必要があります。 また、ドメインの新しいキーペアを生成して、キーをロールオーバーすることもできます。 特定のドメインのキーをロールオーバーする際には、でキーのバージョンを増やしてください。 `generateDomainCredential` 同様に。

その後、1 台のマシンが同じドメインに登録されるたびに、同じドメイン秘密鍵と証明書を使用する必要があります。 起動 `addDomainCredential(DomainToken, PrivateKey)` 既存のドメイン資格情報をクライアントに返す。 ドメインキーが変更されたためにドメインに複数のドメイン資格情報がある場合、サーバーは現在のドメインキーと以前のドメインキーのドメイン資格情報を提供し、古いドメインキーにバインドされたライセンスをクライアントが使用できるようにします。 これにより、古いドメイントークンにバインドされたライセンスを新しく登録されたマシンに移動し、再生可能なままにすることができます。
