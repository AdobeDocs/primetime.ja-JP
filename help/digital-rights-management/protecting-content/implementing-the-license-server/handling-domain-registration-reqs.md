---
title: ドメイン登録要求の処理
description: ドメイン登録要求の処理
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 0%

---

# ドメイン登録要求の処理 {#handle-domain-registration-requests}

DRM メタデータがコンテンツの再生にドメインの登録が必要であることを示している場合、クライアントアプリケーションは `DRMManager.addToDeviceGroup()` ActionScriptAPI または `joinLicenseDomain()` iOS API クライアントが指定されたドメインサーバーにまだ登録していない場合（またはアプリケーションが再加入を強制する場合）は、ドメイン登録要求が送信されます。 ドメインサーバは、クライアントがドメインに参加することを許可するかどうかを判断し、1 つ以上のドメイン資格情報をクライアントに発行します。

* リクエストハンドラークラスは、 `com.adobe.flashaccess.sdk.protocol.domain.DomainRegistrationHandler`
* リクエストメッセージクラスは、 `com.adobe.flashaccess.sdk.protocol.domain.DomainRegistrationRequestMessage`
* クライアントとサーバーの両方がプロトコルバージョン 5 をサポートしている場合、要求 URL は「Domain Server URL in metadata: + 」です。 [!DNL /flashaccess/domain/v4]&quot;. それ以外の場合、要求 URL は、「メタデータのドメインサーバー URL」+「 [!DNL /flashaccess/domain/v3]&quot;

を初期化する際に、 `DomainRegistrationHandler`の場合は、ドメインサーバー URL を指定する必要があります。 次に、この URL は、トークンが発行されたことをドメインサーバーに示すために、ハンドラーが発行したドメイントークンに含まれます。 URL は、サーバーとのドメイン登録を必要とする DRM ポリシーで指定されたドメインサーバー URL と一致する必要があります。

クライアントがドメインに参加するのを許可されているかどうかを判断するために、サーバはリクエスト内のマシンとユーザ情報を調べることができます。 また、サーバは、クライアントがどのドメインに参加するかを決定する場合もあります。

>[!NOTE]
>
>クライアントは、ドメインサーバー URL ごとに 1 つのドメインのメンバーにすることができます。 コンピューターにこのドメインサーバー URL のドメイントークンが既に存在する場合、ドメイン登録要求には現在のドメイン名 ( `getRequestDomainName()`) をクリックします。

再参加要求の場合、ドメインサーバーは、このドメインの現在のドメイン資格情報のセットを返すか、エラーを返す必要があります。 ドメインサーバーは、別のドメインのドメイン資格情報を返さない場合があります。

詳しくは、 [マシン識別子の使用](../../protecting-content/implementing-the-license-server/processing-drm-requests.md#use-machine-identifiers) ドメインに参加しているマシンを識別してカウントする方法については、を参照してください。

ドメインサーバーがドメインに参加するために認証が必要な場合は、リクエストに認証トークンを含める必要があります。 ライセンスリクエストと同様に、ドメイン登録には、ユーザー名/パスワードまたはカスタム認証が必要な場合があります。

詳しくは、 [ユーザー認証](../../protecting-content/implementing-the-license-server/processing-drm-requests.md#user-authentication) 認証トークンの管理方法の詳細については、を参照してください。

ドメインサーバーは、各ドメインに関連付けられたドメインキーの保存と管理を担当します。 ドメインに対して新しいキーペアを生成する必要がある場合（ドメインの最初のドメイン登録）、を呼び出す必要があります。 `generateDomainCredential(String, int, Principal, Date)`. このメソッドは、新しいドメインキーペアとドメイン証明書を生成します。 ドメインサーバーは、このドメインに対する以降の要求を処理する際に、秘密鍵と証明書を保存し、これらのオブジェクトを提供する必要があります。 また、ドメインの新しいキーペアを生成して、キーをロールオーバーすることもできます。 特定のドメインのキーをロールオーバーする際には、必ずでキーのバージョンを増やしてください。 `generateDomainCredential`.

その後、コンピュータが同じドメインに登録するたびに、同じドメイン秘密鍵と証明書を使用する必要があります。 起動 `addDomainCredential(DomainToken, PrivateKey)` 既存のドメイン資格情報をクライアントに返す。 ドメインキーが変更されたためにドメインに複数のドメイン資格情報がある場合、サーバーは現在のドメインキーと以前のドメインキーのドメイン資格情報を提供し、古いドメインキーにバインドされたライセンスをクライアントが使用できるようにします。 これにより、古いドメイントークンにバインドされたライセンスを新しく登録されたマシンに移動し、再生可能なままにすることができます。
