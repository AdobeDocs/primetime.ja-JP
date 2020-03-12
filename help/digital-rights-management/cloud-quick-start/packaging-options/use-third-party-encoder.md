---
seo-title: サードパーティ製エンコーダの使用
title: サードパーティ製エンコーダの使用
uuid: 8649303c-b8e6-4c02-a8ad-5734af850bfe
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# サードパーティ製エンコーダの使用{#use-a-third-party-encoder}

一部のお客様は、ハードウェアまたはソフトウェアのビデオエンコーダー（またはAdobe Media Server）を使用して、既にコンテンツ準備パイプラインを導入している場合があります。 この場合、現在Primetime DRM保護コンテンツを作成できるすべての製品で、Primetime Cloud DRM保護キットと同じ設定を使用して、Primetime Cloud DRM用のコンテンツをパッケージ化できます。 必要な情報は、キットに含まれている既存の設定ファイルのいずれかから取得できます。ま [!DNL config_hls.xml] た [!DNL config_hds.xml]は

関連する設定項目は次のとおりです。

* ライセンスサーバのURL
* キーサーバーURL
* ライセンスサーバー証明書
* Transport Certificate

