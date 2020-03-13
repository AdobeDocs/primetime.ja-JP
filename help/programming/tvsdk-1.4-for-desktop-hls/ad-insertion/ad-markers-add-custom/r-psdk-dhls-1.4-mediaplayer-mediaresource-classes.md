---
description: MediaResourceは、MediaPlayerインスタンスが読み込むコンテンツを表します。
seo-description: MediaResourceは、MediaPlayerインスタンスが読み込むコンテンツを表します。
seo-title: MediaPlayerおよびMediaResourceクラス
title: MediaPlayerおよびMediaResourceクラス
uuid: 36ef75f3-08f7-4fc5-88a7-9bab9198b917
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# MediaPlayerおよびMediaResourceクラス{#mediaplayer-and-mediaresource-classes}

MediaResourceは、MediaPlayerインスタンスが読み込むコンテンツを表します。

<!--<a id="section_B09A012C97454AF58CE2269B800D8027"></a>-->

TVSDKライブラリは、インターフェイスのメソッドを使用して、再生用のコンテンツを読み込んで準備する `replaceCurrentResource` 簡単な手段を提供 `MediaPlayer` します。 このメソッドは、クラスのインスタンスを `MediaResource` 唯一の入力引数として受け取ります。 このク `MediaResource` ラスは、次の情報で構成されます。

* 読み込まれるコンテンツの場所を表すURL。
* 読み込まれるコンテンツのタイプです。

   これは、によって読み込み可能なコンテンツのタイプを定義する文字列で `MediaPlayer`す。 使用可能な値はHLSとHDSです。 各値は、一般的に使用されるファイル拡張子を表す文字列に関連付けられます。HLSの場合は「m3u8」、HDSの場合は「f4m」です。
* 一部のメタデータ(クラスのインスタンス `Metadata` )。

   このディクショナリのような構造には、読み込まれるコンテンツに関する追加情報（メインコンテンツに配置する必要のある代替/広告コンテンツに関する情報など）が含まれる場合があります。

メタデータは、代替コンテンツに関連する情報がTVSDKに渡される媒体です。 インタ `Metadata` ーフェイスは、キーと値の両方がプレーン文字列である汎用のキーと値のストアのAPIを定義します。
