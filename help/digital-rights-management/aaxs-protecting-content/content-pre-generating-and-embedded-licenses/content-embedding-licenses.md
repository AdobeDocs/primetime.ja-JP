---
title: ライセンスの埋め込み
description: ライセンスの埋め込み
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# ライセンスの埋め込み {#embedding-licenses}

コンテンツが暗号化され、ライセンスが事前に生成されたら、ライセンスを暗号化されたコンテンツに埋め込むことができます。

ライセンスを埋め込むには、次のインスタンスを取得します。 `com.adobe.flashaccess.sdk.media.drm.contentupdate.MediaKeyMetaDataUpdater`. 暗号化されたコンテンツのタイプがわかっている場合は、 `FLVKeyMetaDataUpdater` または `F4VKeyMetaDataUpdater`；それ以外の場合は、 `MediaProcessorFactory.getMediaProcessor()` を指定すると、検出されたファイルタイプに基づいてインスタンスが返されます。 次の項目を作成： `KeyMetaDataCallback` を呼び出します。 `modifyKeyMetaData()`. DRM メタデータが暗号化されたコンテンツ内に配置されると、コールバック実装が呼び出されます。 検索されたメタデータに基づいて、埋め込むライセンスを選択し、 `EmbedLicenseKeyMetaData.setEmbeddedLicenses()`.

埋め込みライセンスを示すサンプルコードについては、 `com.adobe.flashaccess.samples.licenseembedder.EmbedLicense` 」をクリックします。

>[!NOTE]
>
>AdobeAccess 2.0 クライアントは、コンテンツに埋め込まれたライセンスを無視し、メタデータで指定されたライセンスサーバーからライセンスを取得しようとします。 ただし、使用可能なライセンスサーバが存在しないとメタデータが示す場合は、AdobeAccess 2.0 クライアントをアップグレードしてコンテンツを表示する必要があります。

詳しくは、 [帯域外ライセンス](../../aaxs-protecting-content/content-introduction/packaging-options/content-out-of-band-licenses.md).
