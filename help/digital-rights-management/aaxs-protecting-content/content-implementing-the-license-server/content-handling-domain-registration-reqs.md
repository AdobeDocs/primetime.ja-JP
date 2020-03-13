---
seo-title: ドメイン登録要求の処理
title: ドメイン登録要求の処理
uuid: e0cef9c4-b2d1-4bec-8dce-50452bc826fb
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# ドメイン登録要求の処理{#handling-domain-registration-requests}

DRMメタデータが、コンテンツを再生するためにドメイン登録が必要であることを示している場合、クライアントアプリケーションは、DRMManager.addToDeviceGroup() ActionScript APIまたはjoinLicenseDomain() iOS APIを呼び出す必要があります。 クライアントがまだ指定したドメインサーバーに登録していない場合（またはアプリケーションが再加入を強制している場合）、ドメイン登録要求が送信されます。 ドメインサーバーは、クライアントがドメインへの参加を許可されるかどうかを判断し、1つ以上のドメイン資格情報をクライアントに発行します。

* リクエストハンドラークラスは、 `com.adobe.flashaccess.sdk.protocol.domain.DomainRegistrationHandler`
* リクエストメッセージクラスは `com.adobe.flashaccess.sdk.protocol.domain.DomainRegistrationRequestMessage`
* クライアントとサーバーの両方がプロトコルバージョン5をサポートしている場合、要求URLは「Domain Server URL in metadata:+ &quot;/flashaccess/domain/v4&quot; それ以外の場合、要求URLは、メタデータのドメインサーバーURL + &quot;/flashaccess/domain/v3&quot;です。

を初期化する際に `DomainRegistrationHandler`は、ドメインサーバーのURLを指定する必要があります。 このURLは、トークンを発行したドメインサーバーを示すために、ハンドラーが発行したドメイントークンに含まれます。 URLは、サーバーへのドメイン登録を必要とするポリシーで指定されたドメインサーバーのURLと一致する必要があります。

クライアントがドメインへの加入を許可されているかどうかを判断するために、サーバーは、要求内のマシンとユーザー情報を調べることができます。 ドメイン [に参加しているマシンを識別](../../aaxs-protecting-content/content-implementing-the-license-server/content-processing-aaxs-requests/content-using-machine-ids.md) 、カウントする方法については、「マシン識別子の使用」を参照してください。 サーバーは、クライアントがどのドメインに参加できるかを判断することもできます。 クライアントは、ドメインサーバーのURLごとに1つのドメインのメンバーになる場合があります。 マシンにこのドメインサーバーURLのドメイントークンが既に存在する場合、ドメイン登録要求には現在のドメイン名( `getRequestDomainName()`)が含まれます。 再加入要求の場合、ドメインサーバーは、このドメインの現在のドメイン資格情報のセットを返すか、エラーを返す必要があります（ドメインサーバーは、別のドメインのドメイン資格情報を返さない場合があります）。

ドメインサーバーがドメインに参加するために認証が必要な場合は、要求に認証トークンが含まれている必要があります。 ライセンス要求と同様に、ドメイン登録にはユーザー名/パスワードまたはカスタム認証が必要になる場合があります。 認証トークン [の処理について詳しくは](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-authentication/content-user-authentication.md) 、「ユーザー認証」を参照してください。

ドメインサーバーは、各ドメインに関連付けられたドメインキーの保存と管理を行います。 ドメイン（ドメインの最初のドメイン登録）に対して新しいキーペアを生成する必要がある場合は、を呼び出しま `generateDomainCredential``(String, int, Principal, Date)`す。 このメソッドは、新しいドメインキーペアとドメイン証明書を生成します。 ドメインサーバーは、このドメインに対する以降の要求を処理する際に、秘密鍵と証明書を格納し、これらのオブジェクトを提供する必要があります。 また、キーをロールオーバーするために、ドメインの新しいキーペアを生成することもできます。 特定のドメインのキーをロールオーバーする場合は、のキーのバージョンも必ず増分し `generateDomainCredential` てください。

その後、マシンが同じドメインに登録されるたびに、同じドメインの秘密鍵と証明書が使用されます。 を呼び出し `addDomainCredential(DomainToken, PrivateKey)` て、既存のドメインの秘密鍵証明書をクライアントに返します。 ドメインキーが変更されたためにドメインに複数のドメイン資格情報が存在する場合は、クライアントが古いドメインキーにバインドされたライセンスを使用できるように、現在のドメインキーと以前のドメインキーのドメイン資格情報を提供する必要があります。 これにより、古いドメイントークンにバインドされたライセンスを新しく登録されたマシンに移動し、引き続き再生可能にすることができます。
