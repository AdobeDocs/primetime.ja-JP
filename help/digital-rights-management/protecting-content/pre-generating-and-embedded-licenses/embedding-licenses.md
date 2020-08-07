---
seo-title: ライセンスの埋め込み
title: ライセンスの埋め込み
uuid: e3d55376-07de-479c-9a53-04bc8071ced4
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---


# ライセンスの埋め込み {#embedding-licenses}

コンテンツが暗号化され、ライセンスが事前に生成されたら、そのライセンスを暗号化されたコンテンツに埋め込むことができます。

ライセンスを埋め込む場合は、のインスタンスを取得する必要があり `com.adobe.flashaccess.sdk.media.drm.contentupdate.MediaKeyMetaDataUpdater`ます。 暗号化されたコンテンツの種類がわかっている場合は、または `FLVKeyMetaDataUpdater``F4VKeyMetaDataUpdater`；のコンストラクタを使用してください。それ以外の場合は、を使用 `MediaProcessorFactory.getMediaProcessor()` して、検出されたファイルタイプに基づくインスタンスを返します。 次に、を構築して呼び出す必要 `KeyMetaDataCallback` があり `modifyKeyMetaData()`ます。 次に、DRMメタデータが暗号化されたコンテンツ内に配置されると、コールバック実装が呼び出されます。 見つかったメタデータに基づいて、埋め込むライセンスを選択し、を使用してライセンスを設定でき `EmbedLicenseKeyMetaData.setEmbeddedLicenses()`ます。

埋め込みライセンス `com.adobe.flashaccess.samples.licenseembedder.EmbedLicense` を示すサンプルコードについては、リファレンス実装のコマンドラインツール [!DNL Samples] ディレクトリのを参照してください。

>[!NOTE]
>
>Adobe PrimetimeDRM 2.0クライアントは、コンテンツに埋め込まれたライセンスを無視し、メタデータで指定されたライセンスサーバーからライセンスを取得しようとします。 ただし、使用可能なライセンスサーバーがないことがメタデータに示されている場合は、コンテンツを表示する前にPrimetime DRM 2.0クライアントをアップグレードする必要があります。

