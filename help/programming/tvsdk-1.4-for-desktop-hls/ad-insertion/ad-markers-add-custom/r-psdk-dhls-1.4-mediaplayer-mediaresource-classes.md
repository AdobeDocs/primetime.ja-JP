---
description: MediaResource は、MediaPlayer インスタンスによって読み込まれるコンテンツを表します。
title: MediaPlayer および MediaResource クラス
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# MediaPlayer および MediaResource クラス{#mediaplayer-and-mediaresource-classes}

MediaResource は、MediaPlayer インスタンスによって読み込まれるコンテンツを表します。

<!--<a id="section_B09A012C97454AF58CE2269B800D8027"></a>-->

TVSDK ライブラリを使用すると、 `replaceCurrentResource` メソッドを `MediaPlayer` インターフェイス。 このメソッドは、 `MediaResource` クラスを唯一の入力引数として使用します。 The `MediaResource` クラスは、次の情報で構成されます。

* 読み込まれるコンテンツの場所を表す URL。
* タイプ。読み込まれるコンテンツのタイプです。

  これは、 `MediaPlayer`. 指定できる値は HLS と HDS です。 各値は、一般的に使用されるファイル拡張子を表す文字列に関連付けられます。HLS の場合は「m3u8」、HDS の場合は「f4m」です。
* 一部のメタデータ ( `Metadata` クラス。

  この辞書に似た構造には、読み込まれるコンテンツに関する追加情報（メインコンテンツに配置する代替/広告コンテンツに関する情報など）が含まれている場合があります。

メタデータは、代替コンテンツに関連する情報を TVSDK に渡すメディアです。 The `Metadata` インターフェイスは、汎用のキーと値のストアの API を定義します。キーと値の両方がプレーン文字列です。
