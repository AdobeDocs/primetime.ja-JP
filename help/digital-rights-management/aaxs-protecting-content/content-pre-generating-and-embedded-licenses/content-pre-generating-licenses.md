---
title: ライセンスの事前生成
description: ライセンスの事前生成
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# ライセンスの事前生成{#pre-generating-licenses}

ライセンスを事前に生成するには、 `com.adobe.flashaccess.sdk.license.pregen.LicenseFactory.getInstance()` 例を得る `LicenseFactory`. このファクトリで生成されたライセンスに署名するには、ライセンスサーバー資格情報を指定する必要があります。 このクラスは、ライセンスチェーニングを行わずに Leaf ライセンスを生成し、 [強化されたライセンスチェーニング](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-other-policy-options/content-enhanced-license-chaining.md).

Leaf ライセンスを生成する場合、コンテンツのメタデータは `initContentInfo()`. メタデータに複数のポリシーが含まれる場合、またはメタデータに含まれていないポリシーを使用する場合は、 `setSelectedPolicy()` をクリックして、ライセンスの生成に使用するポリシーを指定します。 ポリシー更新リストを使用してポリシーの更新を追跡する場合、を使用してメタデータを初期化する前に、ポリシー更新リストを License Factory に提供できます。 `setPolicyUpdateList()`.

ルートライセンスを生成する際には、前述のようにコンテンツのメタデータを指定できます。 または、ポリシー ( `setSelectedPolicy()`) およびライセンスサーバ URL ( `setLicenseServerURL()`) を使用する必要があります。

>[!NOTE]
>
>ライセンスを要求できるAdobeアクセスライセンスサーバがない場合でも、ライセンスサーバ URL が必要です。 この場合、ライセンスサーバ URL は、ライセンス発行者を識別する URL を指定する必要があります。

ポリシーで拡張ライセンスチェーンを使用する場合は、ポリシーのルート暗号化キーを復号化するために、ライセンスサーバーの資格情報を指定する必要があります ( `setRootKeyRetrievalInfo()`) をクリックします。

ポリシーでドメインバインドライセンスが必要な場合は、 `setDomainCAs()` をクリックして、ライセンスサーバーがドメイントークンを受け取るドメイン発行者を指定します。 ライセンス受信者を検証するには、1 つ以上のドメイン CA 証明書を提供する必要があります。

ポリシーでiOSデバイスのリモートキー配信が必要な場合は、を使用してキーサーバー証明書を指定する必要があります。 `setKeyServerCertificate()`チェーンされたリーフが生成されていない場合は除きます。

ライセンスを生成するには、を呼び出します。 `generateLicense()` ライセンスの種類（リーフまたはルート）と 1 つ以上の受信者証明書を指定します。 受信者証明書は、ポリシーで指定されている要件に応じて、コンピューター証明書またはドメイン証明書になります。 チェーンされたリーフを生成する場合は、受信者は不要です。 ライセンスが生成された後は、ポリシーで指定された使用規則を上書きできます。 最後に、を呼び出します。 `signLicense()` ライセンスに署名してインスタンスを取得するには `PreGeneratedLicense`. これで、ライセンスをファイルに保存できます ( `getBytes()` ：シリアル化されたライセンスの取得 )、または暗号化されたコンテンツに埋め込まれます。 詳しくは、 [ライセンスの埋め込み](../../aaxs-protecting-content/content-pre-generating-and-embedded-licenses/content-embedding-licenses.md).

事前生成ライセンスを示すサンプルコードについては、 `com.adobe.flashaccess.samples.licensegen.GenerateLicense` 「リファレンス実装」コマンドラインツールの「samples」ディレクトリ。
