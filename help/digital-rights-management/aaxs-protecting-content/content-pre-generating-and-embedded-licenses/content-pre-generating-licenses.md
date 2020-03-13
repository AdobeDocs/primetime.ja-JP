---
seo-title: 事前生成ライセンス
title: 事前生成ライセンス
uuid: 31430753-11f1-4ce5-b402-cf4279119a05
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# 事前生成ライセンス{#pre-generating-licenses}

ライセンスを事前生成するには、を使用し `com.adobe.flashaccess.sdk.license.pregen.LicenseFactory.getInstance()` てのインスタンスを取得しま `LicenseFactory`す。 このファクトリで生成されたライセンスに署名するには、ライセンスサーバーの資格情報を指定する必要があります。 このクラスは、ライセンスチェーンなしでのLeafライセンスの生成と、拡張ライセンスチェーンを使用したLeafライセンスとRootライセンスの生成 [をサポートしていま](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-other-policy-options/content-enhanced-license-chaining.md)す。

リーフライセンスを生成する場合、を使用してコンテンツのメタデータを指定する必要がありま `initContentInfo()`す。 メタデータに複数のポリシーが含まれる場合、またはメタデータに含まれていないポリシーを使用する場合は、を使用して、ライセンスの生成に使 `setSelectedPolicy()` 用するポリシーを指定します。 ポリシー更新リストを使用してポリシーの更新を追跡する場合、を使用してメタデータを初期化する前に、ポリシー更新リストをライセンスファクトリに提供できま `setPolicyUpdateList()`す。

Rootライセンスを生成する際に、コンテンツのメタデータを上記のように指定できます。 また、Rootライセンスは、メタデータの代わりにポリシー( `setSelectedPolicy()`)とライセンスサーバーURL( `setLicenseServerURL()`)を使用して生成できます。

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>クライアントがライセンスを要求できるAdobe Access License Serverがない場合でも、ライセンスサーバーのURLが必要です。 この場合、ライセンスサーバのURLには、ライセンスの発行者を識別するURLを指定する必要があります。

ポリシーで拡張ライセンスチェーンを使用する場合、ポリシー( `setRootKeyRetrievalInfo()`)のルート暗号化キーを復号化するには、ライセンスサーバーの秘密鍵証明書を指定する必要があります。

ポリシーでドメインバインドライセンスが必要な場合は、を使用し `setDomainCAs()` て、ライセンスサーバーがドメイントークンを受け入れるドメイン発行者を指定します。 ライセンスの受信者を検証するには、1つ以上のドメインCA証明書を指定する必要があります。

iOSデバイスに対してポリシーでリモートキーの配信が必要な場合は、チェーンリーフが生成されていない限り、を使用してキ `setKeyServerCertificate()`ーサーバー証明書を提供する必要があります。

ライセンスを生成するには、ライセンス `generateLicense()` の種類（リーフまたはルート）と1つ以上の受信者証明書を呼び出して指定します。 受信者証明書は、ポリシーで指定された要件に応じて、コンピューター証明書またはドメイン証明書になります。 連結されたリーフを生成する場合、受信者は不要です。 ライセンスが生成された後、ポリシーで指定された使用規則を上書きできます。 最後に、を呼び出し `signLicense()` てライセンスに署名し、のインスタンスを取得しま `PreGeneratedLicense`す。 ライセンスをファイルに保存（シリアライズされたライセンスの取得に使用）したり、 `getBytes()` 暗号化されたコンテンツに埋め込んだりできるようになりました。 詳しくは、ライセンス [の埋め込みを参照してくださ](../../aaxs-protecting-content/content-pre-generating-and-embedded-licenses/content-embedding-licenses.md)い。

事前生成ライセンスを示すサンプルコードについては、『リファレンス `com.adobe.flashaccess.samples.licensegen.GenerateLicense` 実装コマンドラインツール』の「samples」ディレクトリを参照してください。
