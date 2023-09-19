---
title: サードパーティ製のエンコーダーを使用する
description: サードパーティ製のエンコーダーを使用する
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---

# サードパーティ製のエンコーダーを使用する{#use-a-third-party-encoder}

ハードウェアまたはソフトウェアのビデオエンコーダー ( またはAdobe Media Server) を使用して、コンテンツ準備パイプラインを既に導入しているお客様もいます。 その場合、現在 Primetime DRM で保護されたコンテンツを作成できる製品では、Primetime Cloud DRM 保護キットと同じ設定を使用して、Primetime Cloud DRM 用のコンテンツをパッケージ化できます。 必要な情報は、キットに含まれている既存の設定ファイルのいずれかから取得できます。 [!DNL config_hls.xml] または [!DNL config_hds.xml].

関連する設定項目は次のとおりです。

* ライセンスサーバー URL
* キーサーバー URL
* ライセンスサーバー証明書
* トランスポート証明書
