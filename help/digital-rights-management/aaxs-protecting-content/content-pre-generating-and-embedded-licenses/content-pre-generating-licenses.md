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

ライセンスを事前生成するには、を使用 `com.adobe.flashaccess.sdk.license.pregen.LicenseFactory.getInstance()` してのインスタンスを取得し `LicenseFactory`ます。 このファクトリによって生成されたライセンスに署名するには、License Server資格情報を指定する必要があります。 このクラスは、ライセンスチェーンなしでのリーフライセンスの生成をサポートし、 [拡張ライセンスチェーンを使用したリーフライセンスとルートライセンス](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-other-policy-options/content-enhanced-license-chaining.md)。

リーフライセンスを生成する場合、を使用してコンテンツのメタデータを指定する必要があり `initContentInfo()`ます。 メタデータに複数のポリシーが含まれる場合、またはメタデータに含まれていないポリシーを使用する場合は、を使用して、ライセンスの生成に使用するポリシー `setSelectedPolicy()` を指定します。 ポリシーの更新リストを使用してポリシーの更新を追跡する場合、を使用してメタデータを初期化する前に、License Factoryにポリシー更新リストを指定でき `setPolicyUpdateList()`ます。

Rootライセンスを生成する際に、コンテンツのメタデータを上記のとおりに指定できます。 または、メタデータの代わりにポリシー( `setSelectedPolicy()`)とライセンスサーバーURL( `setLicenseServerURL()`)を使用して、Rootライセンスを生成できます。

>[!NOTE]
>
>クライアントがライセンスを要求できるAdobeアクセスライセンスサーバがない場合でも、ライセンスサーバURLが必要です。 この場合、License ServerのURLには、ライセンス発行者を識別するURLを指定する必要があります。

ポリシーで拡張ライセンスチェーンを使用する場合は、ポリシー( `setRootKeyRetrievalInfo()`)のルート暗号化キーを復号化するために、ライセンスサーバーの秘密鍵証明書を指定する必要があります。

ポリシーでドメインバインドライセンスが必要な場合は、を使用して、ライセンスサーバーがドメイントークンを受け入れるドメイン発行者 `setDomainCAs()` を指定します。 ライセンス受信者を検証するには、1つ以上のドメインCA証明書を指定する必要があります。

iOSデバイスに対してポリシーでリモートキーの配信が必要な場合は、Chained Leafが生成されていない限り、を使用してキーサーバー証明書を指定する必要があり `setKeyServerCertificate()`ます。

ライセンスを生成するには、ライセンスの種類（リーフまたはルート） `generateLicense()` と1つ以上の受信者証明書を呼び出して指定します。 受信者証明書は、ポリシーで指定されている要件に応じて、コンピューター証明書またはドメイン証明書になります。 Chained Leafを生成する場合、受信者は不要です。 ライセンスが生成された後は、ポリシーで指定された使用規則を上書きできます。 最後に、を呼び出 `signLicense()` してライセンスに署名し、のインスタンスを取得し `PreGeneratedLicense`ます。 ライセンスをファイルに保存(シリアライズされたライセンスを取得するた `getBytes()` めに使用)したり、暗号化されたコンテンツに埋め込んだりできるようになりました。 詳しくは、ライセンスの [埋め込みを参照してください](../../aaxs-protecting-content/content-pre-generating-and-embedded-licenses/content-embedding-licenses.md)。

事前生成ライセンスを示すサンプルコードについては、『リファレンス導入コマンドラインツール』 `com.adobe.flashaccess.samples.licensegen.GenerateLicense` の「samples」ディレクトリを参照してください。
