---
title: サードパーティ製エンコーダーの使用
description: サードパーティ製エンコーダーの使用
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---


# サードパーティ製エンコーダーを使用する{#use-a-third-party-encoder}

一部のお客様は、ハードウェアまたはソフトウェアのビデオエンコーダー(またはAdobe Mediumサーバー)を使用して、既にコンテンツ準備パイプラインを導入している場合があります。 この場合、現在Primetime DRM保護コンテンツを作成できるすべての製品では、Primetime Cloud DRM保護キットと同じ設定を使用して、Primetime Cloud DRM用のコンテンツをパッケージ化できます。 必要な情報は、キットに含まれている既存の設定ファイルのいずれかから取得できます。[!DNL config_hls.xml]または[!DNL config_hds.xml]。

関連する設定項目は次のとおりです。

* ライセンスサーバのURL
* キーサーバーURL
* ライセンスサーバー証明書
* Transport Certificate

