---
description: MediaResource は、MediaPlayer インスタンスによって読み込まれるコンテンツを表します。
title: MediaPlayer および MediaResource クラス
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# MediaPlayer および MediaResource クラス{#mediaplayer-and-mediaresource-classes}

MediaResource は、MediaPlayer インスタンスによって読み込まれるコンテンツを表します。

<!--<a id="section_B09A012C97454AF58CE2269B800D8027"></a>-->

TVSDK ライブラリを使用すると、 `replaceCurrentItem` メソッドを使用して、MediaPlayer インターフェイスに表示されます。 このメソッドは、唯一の入力引数として MediaResource クラスのインスタンスを受け取ります。 MediaResource クラスは、次の情報で構成されます。

* 読み込まれるコンテンツの場所を表す URL。
* タイプ。読み込まれるコンテンツのタイプです。

  これは、 `MediaResource` MediaPlayer で読み込み可能なコンテンツのタイプを定義するクラス。 指定できる値は HLS と HDS です。 各値は、一般的に使用されるファイル拡張子を表す文字列に関連付けられます。 `m3u8` （HLS およびの場合） `f4m` （HDS 用）
* 一部のメタデータ ( `Metadata` クラス。

  この辞書に似た構造には、読み込まれるコンテンツに関する追加情報（メインコンテンツに配置する代替/広告コンテンツに関する情報など）が含まれている場合があります。

メタデータは、代替コンテンツに関連する情報を TVSDK に渡すメディアです。 The `Metadata` インターフェイスは、汎用のキーと値のストアの API を定義します。キーと値の両方がプレーン文字列です。
