---
seo-title: ライセンスの埋め込み
title: ライセンスの埋め込み
uuid: e3d55376-07de-479c-9a53-04bc8071ced4
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# ライセンスの埋め込み {#embedding-licenses}

コンテンツが暗号化され、ライセンスが事前に生成されたら、ライセンスは暗号化されたコンテンツに埋め込まれます。

ライセンスを埋め込む場合は、のインスタンスを取得する必要がありま `com.adobe.flashaccess.sdk.media.drm.contentupdate.MediaKeyMetaDataUpdater`す。 暗号化されたコンテンツのタイプがわかっている場合は、またはのコンストラクタを使 `FLVKeyMetaDataUpdater` 用しま `F4VKeyMetaDataUpdater`す。それ以外の場合は、を `MediaProcessorFactory.getMediaProcessor()` 使用して、検出されたファイルタイプに基づいてインスタンスを返します。 その後、を構築して呼び出す `KeyMetaDataCallback` 必要がありま `modifyKeyMetaData()`す。 その後、DRMメタデータが暗号化されたコンテンツ内に配置されると、コールバック実装が呼び出されます。 見つかったメタデータに基づいて、埋め込むライセンスを選択し、を使用してライセンスを設定できま `EmbedLicenseKeyMetaData.setEmbeddedLicenses()`す。

埋め込みラ `com.adobe.flashaccess.samples.licenseembedder.EmbedLicense` イセンスを示すサンプルコードについては、Reference Implementation Command Line Tools [!DNL Samples] ディレクトリのを参照してください。

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>Adobe Primetime DRM 2.0クライアントは、コンテンツに埋め込まれたライセンスを無視し、メタデータで指定されたライセンスサーバーからライセンスを取得しようとします。 ただし、使用可能なライセンスサーバーがないことがメタデータに示されている場合は、コンテンツを表示する前にPrimetime DRM 2.0クライアントをアップグレードする必要があります。

