---
seo-title: ドメイン登録要求の処理
title: ドメイン登録要求の処理
uuid: d92db6c2-5a16-41ea-a1aa-541c59780678
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# ドメイン登録要求の処理 {#handle-domain-registration-requests}

DRMメタデータが、コンテンツを再生するためにドメイン登録が必要であることを示している場合は、クライアントアプリケーションから `DRMManager.addToDeviceGroup()` ActionScript APIまたは `joinLicenseDomain()` iOS APIを呼び出す必要があります。 クライアントがまだ指定したドメインサーバーに登録していない場合（またはアプリケーションが再加入を強制している場合）、ドメイン登録要求が送信されます。 ドメインサーバーは、クライアントがドメインへの参加を許可されるかどうかを判断し、1つ以上のドメイン資格情報をクライアントに発行します。

* リクエストハンドラークラスは、 `com.adobe.flashaccess.sdk.protocol.domain.DomainRegistrationHandler`
* リクエストメッセージクラスは `com.adobe.flashaccess.sdk.protocol.domain.DomainRegistrationRequestMessage`
* クライアントとサーバーの両方がプロトコルバージョン5をサポートしている場合、要求URLは「Domain Server URL in metadata:+ &quot; [!DNL /flashaccess/domain/v4]&quot; それ以外の場合、要求URLは、メタデータ&quot; + &quot; [!DNL /flashaccess/domain/v3]&quot;のドメインサーバーURLです

を初期化する際は、ドメ `DomainRegistrationHandler`インサーバーのURLを指定する必要があります。 次に、このURLは、トークンが発行されたことをドメインサーバーに示すために、ハンドラーが発行したドメイントークンに含まれます。 URLは、サーバーへのドメイン登録を必要とするDRMポリシーで指定されたドメインサーバーのURLと一致する必要があります。

クライアントがドメインへの加入を許可されているかどうかを判断するために、サーバーは、要求内のマシンとユーザー情報を調べることができます。 サーバーは、クライアントがどのドメインに参加できるかを判断することもできます。

>[!NOTE]
>
>クライアントは、ドメインサーバーのURLごとに1つのドメインのメンバーにすることができます。 マシンにこのドメインサーバーURLのドメイントークンが既に存在する場合、ドメイン登録要求には現在のドメイン名( `getRequestDomainName()`)が含まれます。

再加入要求の場合、ドメインサーバーは、このドメインの現在のドメイン資格情報のセットを返すか、エラーを返す必要があります。 ドメインサーバーは、別のドメインのドメイン資格情報を返さない場合があります。

ドメイン [に参加しているマシンを識別](../../protecting-content/implementing-the-license-server/processing-drm-requests.md#use-machine-identifiers) 、カウントする方法については、「マシン識別子の使用」を参照してください。

ドメインサーバーがドメインに参加するために認証が必要な場合は、要求に認証トークンが含まれている必要があります。 ライセンス要求と同様に、ドメイン登録にはユーザー名/パスワードまたはカスタム認証が必要になる場合があります。

認証トー [クンの管理方法について詳しくは](../../protecting-content/implementing-the-license-server/processing-drm-requests.md#user-authentication) 、「ユーザー認証」を参照してください。

ドメインサーバーは、各ドメインに関連付けられたドメインキーの保存と管理を行います。 ドメイン（ドメインの最初のドメイン登録）に対して新しいキーペアを生成する必要がある場合は、を呼び出す必要がありま `generateDomainCredential(String, int, Principal, Date)`す。 このメソッドは、新しいドメインキーペアとドメイン証明書を生成します。 ドメインサーバーは、このドメインに対する以降の要求を処理する際に、秘密鍵と証明書を格納し、これらのオブジェクトを提供する必要があります。 また、キーをロールオーバーするために、ドメインの新しいキーペアを生成することもできます。 特定のドメインのキーをロールオーバーする場合は、でキーのバージョンを増やしてくださ `generateDomainCredential`い。

その後、マシンが同じドメインに登録されるたびに、同じドメインの秘密鍵と証明書が使用されます。 を呼び出し `addDomainCredential(DomainToken, PrivateKey)` て、既存のドメインの秘密鍵証明書をクライアントに返します。 ドメインキーが変更されたためにドメインに複数のドメイン資格情報が存在する場合は、クライアントが古いドメインキーにバインドされたライセンスを使用できるように、現在のドメインキーと以前のドメインキーのドメイン資格情報を提供する必要があります。 これにより、古いドメイントークンにバインドされたライセンスを新しく登録されたマシンに移動し、引き続き再生可能にすることができます。
