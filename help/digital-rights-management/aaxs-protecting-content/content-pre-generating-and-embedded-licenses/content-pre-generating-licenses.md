---
seo-title: 事前生成ライセンス
title: 事前生成ライセンス
uuid: 31430753-11f1-4ce5-b402-cf4279119a05
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---


# 事前生成ライセンス{#pre-generating-licenses}

ライセンスを事前生成するには、`com.adobe.flashaccess.sdk.license.pregen.LicenseFactory.getInstance()`を使用して`LicenseFactory`のインスタンスを取得します。 このファクトリによって生成されたライセンスに署名するには、License Server資格情報を指定する必要があります。 このクラスは、ライセンスチェーンなしでリーフライセンスを生成し、[拡張ライセンスチェーン](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-other-policy-options/content-enhanced-license-chaining.md)を使用してリーフライセンスとルートライセンスを生成できます。

リーフライセンスを生成する場合、コンテンツのメタデータは`initContentInfo()`を使用して指定する必要があります。 メタデータに複数のポリシーが含まれる場合、またはメタデータに含まれていないポリシーを使用する場合は、`setSelectedPolicy()`を使用して、ライセンスの生成に使用するポリシーを指定します。 ポリシーの更新リストを使用してポリシーの更新を追跡する場合、`setPolicyUpdateList()`を使用してメタデータを初期化する前に、License Factoryにポリシー更新リストを提供できます。

Rootライセンスを生成する際に、コンテンツのメタデータを上記のとおりに指定できます。 また、Rootライセンスは、メタデータの代わりにポリシー(`setSelectedPolicy()`)とライセンスサーバーURL(`setLicenseServerURL()`)を使用して生成できます。

>[!NOTE]
>
>クライアントがライセンスを要求できるAdobeアクセスライセンスサーバがない場合でも、ライセンスサーバURLが必要です。 この場合、License ServerのURLには、ライセンス発行者を識別するURLを指定する必要があります。

ポリシーで拡張ライセンスチェーンを使用する場合は、ポリシー(`setRootKeyRetrievalInfo()`)のルート暗号化キーを復号化するために、ライセンスサーバーの秘密鍵証明書を指定する必要があります。

ポリシーにドメインバインドライセンスが必要な場合は、`setDomainCAs()`を使用して、ライセンスサーバーがドメイントークンを受け入れるドメイン発行者を指定します。 ライセンス受信者を検証するには、1つ以上のドメインCA証明書を指定する必要があります。

iOSデバイスに対してリモートキー配信がポリシーで必要な場合、Chained Leafが生成されていない限り、`setKeyServerCertificate()`を使用してキーサーバー証明書を指定する必要があります。

ライセンスを生成するには、`generateLicense()`を呼び出し、ライセンスの種類（リーフまたはルート）と1つ以上の受信者証明書を指定します。 受信者証明書は、ポリシーで指定されている要件に応じて、コンピューター証明書またはドメイン証明書になります。 Chained Leafを生成する場合、受信者は不要です。 ライセンスが生成された後は、ポリシーで指定された使用規則を上書きできます。 最後に、`signLicense()`を呼び出してライセンスに署名し、`PreGeneratedLicense`のインスタンスを取得します。 ライセンスをファイルに保存（`getBytes()`を使用してシリアライズされたライセンスを取得）したり、暗号化されたコンテンツに埋め込んだりできるようになりました。 「[ライセンスの埋め込み](../../aaxs-protecting-content/content-pre-generating-and-embedded-licenses/content-embedding-licenses.md)」を参照してください。

事前生成ライセンスをデモするサンプルコードについては、リファレンス実装のコマンドラインツールの「samples」ディレクトリの`com.adobe.flashaccess.samples.licensegen.GenerateLicense`を参照してください。
