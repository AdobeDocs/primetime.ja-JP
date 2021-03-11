---
description: MediaResourceは、MediaPlayerインスタンスが読み込もうとしているコンテンツを表します。
title: MediaPlayerおよびMediaResourceクラス
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---


# MediaPlayerおよびMediaResourceクラス{#mediaplayer-and-mediaresource-classes}

MediaResourceは、MediaPlayerインスタンスが読み込もうとしているコンテンツを表します。

<!--<a id="section_431AB7221E0249BF949EC72EEB9B428A"></a>-->

TVSDKは、`MediaPlayer`の`replaceCurrentResource`メソッドを使用して、再生するコンテンツを読み込み、準備する手段を提供します。 このメソッドは、`MediaPlayerResource`のインスタンスと、必要に応じて`MediaPlayerItemConfig`のインスタンスの2つの引数を取ります。これを使用して、アプリケーション定義のカスタムパラメーターを渡すことができます。

* 詳しくは、mediaplayer-reuse-or-removeを参照してください。
* `MediaPlayerResource`の詳細については、media-resource-createを参照してください

