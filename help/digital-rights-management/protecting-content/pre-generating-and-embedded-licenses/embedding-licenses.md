---
title: ライセンスの埋め込み
description: ライセンスの埋め込み
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---


# ライセンスの埋め込み{#embedding-licenses}

コンテンツが暗号化され、ライセンスが事前に生成されたら、そのライセンスを暗号化されたコンテンツに埋め込むことができます。

ライセンスを埋め込む場合は、`com.adobe.flashaccess.sdk.media.drm.contentupdate.MediaKeyMetaDataUpdater`のインスタンスを取得する必要があります。 暗号化されたコンテンツの種類がわかっている場合は、`FLVKeyMetaDataUpdater`または`F4VKeyMetaDataUpdater`；のコンストラクタを使用してください。それ以外の場合は、`MediaProcessorFactory.getMediaProcessor()`を使用して、検出されたファイルタイプに基づくインスタンスを返します。 次に、`KeyMetaDataCallback`を構築して`modifyKeyMetaData()`を呼び出す必要があります。 次に、DRMメタデータが暗号化されたコンテンツ内に配置されると、コールバック実装が呼び出されます。 見つかったメタデータに基づいて、埋め込むライセンスを選択し、`EmbedLicenseKeyMetaData.setEmbeddedLicenses()`を使用してライセンスを設定できます。

埋め込みライセンスの例を示すサンプルコードについては、リファレンス実装のコマンドラインツール[!DNL Samples]ディレクトリの`com.adobe.flashaccess.samples.licenseembedder.EmbedLicense`を参照してください。

>[!NOTE]
>
>Adobe PrimetimeDRM 2.0クライアントは、コンテンツに埋め込まれたライセンスを無視し、メタデータで指定されたライセンスサーバーからライセンスを取得しようとします。 ただし、使用可能なライセンスサーバーがないことがメタデータに示されている場合は、コンテンツを表示する前にPrimetime DRM 2.0クライアントをアップグレードする必要があります。

