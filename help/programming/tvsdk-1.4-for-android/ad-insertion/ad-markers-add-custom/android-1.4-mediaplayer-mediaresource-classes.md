---
description: MediaResourceは、MediaPlayerインスタンスが読み込もうとしているコンテンツを表します。
title: MediaPlayerおよびMediaResourceクラス
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---


# MediaPlayerおよびMediaResourceクラス{#mediaplayer-and-mediaresource-classes}

MediaResourceは、MediaPlayerインスタンスが読み込もうとしているコンテンツを表します。

<!--<a id="section_B09A012C97454AF58CE2269B800D8027"></a>-->

TVSDKライブラリは、MediaPlayerインターフェイスの`replaceCurrentItem`メソッドを使用して、再生するコンテンツを読み込み、準備する簡単な方法を提供します。 このメソッドは、MediaResourceクラスのインスタンスを唯一の入力引数として受け取ります。 MediaResourceクラスは、次の情報で構成されます。

* 読み込まれるコンテンツの場所を表すURL。
* タイプ。読み込まれるコンテンツのタイプです。

   これは、MediaPlayerで読み込み可能なコンテンツのタイプを定義する`MediaResource`クラスの単純な定義済みリストです。 使用可能な値はHLSとHDSです。 各値には、一般的に使用されるファイル拡張子を表す文字列が関連付けられています（HLSの場合は`m3u8`、HDSの場合は`f4m`）。
* `Metadata`クラスのインスタンスである、一部のメタデータ。

   このディクショナリのような構造体は、読み込まれるコンテンツに関する追加情報（メインコンテンツに配置する必要がある代替/広告コンテンツに関する情報など）を含む場合があります。

メタデータは、代替コンテンツに関連する情報をTVSDKに渡すメディアです。 `Metadata`インターフェイスは、キーと値の両方がプレーン文字列である汎用のキー値ストアのAPIを定義します。
