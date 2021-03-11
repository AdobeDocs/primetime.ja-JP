---
title: ライセンスの埋め込み
description: ライセンスの埋め込み
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
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
