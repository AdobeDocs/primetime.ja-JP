---
seo-title: ライセンスの埋め込み
title: ライセンスの埋め込み
uuid: b8d8ee9b-7430-4899-9caf-47d6b64021b8
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---


# ライセンスの埋め込み{#embedding-licenses}

コンテンツが暗号化され、ライセンスが事前に生成されたら、そのライセンスを暗号化されたコンテンツに埋め込むことができます。

ライセンスを埋め込むには、`com.adobe.flashaccess.sdk.media.drm.contentupdate.MediaKeyMetaDataUpdater`のインスタンスを取得します。 暗号化されたコンテンツの種類がわかっている場合は、`FLVKeyMetaDataUpdater`または`F4VKeyMetaDataUpdater`；のコンストラクタを使用してください。それ以外の場合は、`MediaProcessorFactory.getMediaProcessor()`を使用して、検出されたファイルタイプに基づくインスタンスを返します。 `KeyMetaDataCallback`を作成し、`modifyKeyMetaData()`を呼び出します。 DRMメタデータが暗号化されたコンテンツ内に配置されると、コールバック実装が呼び出されます。 見つかったメタデータに基づいて、埋め込むライセンスを選択し、`EmbedLicenseKeyMetaData.setEmbeddedLicenses()`を使用してライセンスを設定できます。

埋め込みライセンスをデモするサンプルコードについては、リファレンス実装のコマンドラインツールの「Samples」ディレクトリの`com.adobe.flashaccess.samples.licenseembedder.EmbedLicense`を参照してください。

>[!NOTE]
>
>Adobeアクセス2.0クライアントは、コンテンツに埋め込まれたライセンスを無視し、メタデータで指定されたライセンスサーバーからライセンスの取得を試みます。 ただし、使用可能なライセンスサーバがないことがメタデータに示されている場合は、AdobeAccess 2.0クライアントはコンテンツを表示にアップグレードする必要があります。

[帯域外ライセンス](../../aaxs-protecting-content/content-introduction/packaging-options/content-out-of-band-licenses.md)を参照してください。
