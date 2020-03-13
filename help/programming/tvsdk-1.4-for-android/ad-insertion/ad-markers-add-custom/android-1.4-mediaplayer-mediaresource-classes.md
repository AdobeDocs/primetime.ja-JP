---
description: MediaResourceは、MediaPlayerインスタンスが読み込むコンテンツを表します。
seo-description: MediaResourceは、MediaPlayerインスタンスが読み込むコンテンツを表します。
seo-title: MediaPlayerおよびMediaResourceクラス
title: MediaPlayerおよびMediaResourceクラス
uuid: 7393c320-7dbb-4580-9425-a735f9d03ef5
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# MediaPlayerおよびMediaResourceクラス{#mediaplayer-and-mediaresource-classes}

MediaResourceは、MediaPlayerインスタンスが読み込むコンテンツを表します。

<!--<a id="section_B09A012C97454AF58CE2269B800D8027"></a>-->

TVSDKライブラリは、MediaPlayerインターフェイスのメソッドを使用して、再生用のコンテンツを読み込み、準 `replaceCurrentItem` 備する簡単な方法を提供します。 このメソッドは、MediaResourceクラスのインスタンスを唯一の入力引数として受け取ります。 MediaResourceクラスは、次の情報で構成されます。

* 読み込まれるコンテンツの場所を表すURL。
* 読み込まれるコンテンツのタイプです。

   これは、MediaPlayerによって読み込み `MediaResource` 可能なコンテンツのタイプを定義するクラス内の単純な列挙です。 使用可能な値はHLSとHDSです。 各値は、HLSおよびHDSで一般的に使用されるファイル拡張子を表す文字 `m3u8` 列に関連付け `f4m` られます。
* 一部のメタデータ(クラスのインスタンス `Metadata` )。

   このディクショナリのような構造には、読み込まれるコンテンツに関する追加情報（メインコンテンツに配置する必要のある代替/広告コンテンツに関する情報など）が含まれる場合があります。

メタデータは、代替コンテンツに関連する情報がTVSDKに渡される媒体です。 インタ `Metadata` ーフェイスは、キーと値の両方がプレーン文字列である汎用のキーと値のストアのAPIを定義します。
