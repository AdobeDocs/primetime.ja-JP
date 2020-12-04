---
description: MediaResourceは、MediaPlayerインスタンスが読み込もうとしているコンテンツを表します。
seo-description: MediaResourceは、MediaPlayerインスタンスが読み込もうとしているコンテンツを表します。
seo-title: MediaPlayerおよびMediaResourceクラス
title: MediaPlayerおよびMediaResourceクラス
uuid: dcc747d2-8340-45e3-8cdb-a79d4f9360dc
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 0%

---


# MediaPlayerおよびMediaResourceクラス{#mediaplayer-and-mediaresource-classes}

MediaResourceは、MediaPlayerインスタンスが読み込もうとしているコンテンツを表します。

<!--<a id="section_431AB7221E0249BF949EC72EEB9B428A"></a>-->

TVSDKは、`MediaPlayer`の`replaceCurrentResource`メソッドを使用して、再生するコンテンツを読み込み、準備する手段を提供します。 このメソッドは、`MediaPlayerResource`のインスタンスと、必要に応じて`MediaPlayerItemConfig`のインスタンスの2つの引数を取ります。これを使用して、アプリケーション定義のカスタムパラメーターを渡すことができます。

* 詳しくは、mediaplayer-reuse-or-removeを参照してください。
* `MediaPlayerResource`の詳細については、media-resource-createを参照してください

