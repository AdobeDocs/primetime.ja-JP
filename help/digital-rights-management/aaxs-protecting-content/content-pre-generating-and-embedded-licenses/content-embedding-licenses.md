---
seo-title: ライセンスの埋め込み
title: ライセンスの埋め込み
uuid: b8d8ee9b-7430-4899-9caf-47d6b64021b8
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# ライセンスの埋め込み {#embedding-licenses}

コンテンツが暗号化され、ライセンスが事前に生成されたら、ライセンスは暗号化されたコンテンツに埋め込まれます。

ライセンスを埋め込むには、のインスタンスを取得しま `com.adobe.flashaccess.sdk.media.drm.contentupdate.MediaKeyMetaDataUpdater`す。 暗号化されたコンテンツのタイプがわかっている場合は、またはのコンストラクタを使 `FLVKeyMetaDataUpdater` 用しま `F4VKeyMetaDataUpdater`す。それ以外の場合は、を `MediaProcessorFactory.getMediaProcessor()` 使用して、検出されたファイルタイプに基づいてインスタンスを返します。 を作成し、を呼 `KeyMetaDataCallback` び出しま `modifyKeyMetaData()`す。 DRMメタデータが暗号化されたコンテンツ内に配置されると、コールバック実装が呼び出されます。 見つかったメタデータに基づいて、埋め込むライセンスを選択し、を使用してライセンスを設定できま `EmbedLicenseKeyMetaData.setEmbeddedLicenses()`す。

埋め込みライセンスを示すサンプルコードについては、『リファレ `com.adobe.flashaccess.samples.licenseembedder.EmbedLicense` ンス実装コマンドラインツール』の「サンプル」ディレクトリを参照してください。

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>Adobe Access 2.0クライアントは、コンテンツに埋め込まれたライセンスを無視し、メタデータで指定されたライセンスサーバーからライセンスの取得を試みます。 ただし、使用可能なライセンスサーバーがないことがメタデータに示されている場合は、コンテンツを表示するにはAdobe Access 2.0クライアントをアップグレードする必要があります。

「帯域外 [ライセンス」を参照してください](../../aaxs-protecting-content/content-introduction/packaging-options/content-out-of-band-licenses.md)。
