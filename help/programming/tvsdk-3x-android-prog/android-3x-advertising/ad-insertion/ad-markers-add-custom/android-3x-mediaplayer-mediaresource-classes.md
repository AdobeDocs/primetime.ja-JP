---
description: MediaResourceは、MediaPlayerインスタンスが読み込もうとしているコンテンツを表します。
seo-description: MediaResourceは、MediaPlayerインスタンスが読み込もうとしているコンテンツを表します。
seo-title: MediaPlayerおよびMediaResourceクラス
title: MediaPlayerおよびMediaResourceクラス
uuid: e198f599-22ca-4ea4-bbbb-e239c79174ae
translation-type: tm+mt
source-git-commit: ed910a60440ae7c0d19d9be56c80c8bdbc62bcf1
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 0%

---


# MediaPlayerおよびMediaResourceクラス{#mediaplayer-and-mediaresource-classes}

MediaResourceは、MediaPlayerインスタンスが読み込もうとしているコンテンツを表します。

<!--<a id="section_431AB7221E0249BF949EC72EEB9B428A"></a>-->

TVSDKは、`MediaPlayer`の`replaceCurrentResource`メソッドを使用して、再生するコンテンツを読み込み、準備する手段を提供します。 このメソッドは、`MediaPlayerResource`のインスタンスと、必要に応じて`MediaPlayerItemConfig`のインスタンスの2つの引数を取ります。これを使用して、アプリケーション定義のカスタムパラメーターを渡すことができます。

* 詳しくは、[MediaPlayerインスタンスの再利用または削除](../../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayerobjects-working-with/android-3x-mediaplayer-reuse-or-remove.md)を参照してください。
* `MediaPlayerResource`の詳細については、[メディアリソースの作成](../../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-create.md)を参照してください。