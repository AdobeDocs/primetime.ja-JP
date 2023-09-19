---
description: 即時オンでは、1 つ以上のチャネルでメディアの一部がプリロードされます。 ユーザーがチャネルを選択または切り替えた後、一部のバッファリングが既に完了しているので、コンテンツは早く開始します。
title: 即時オン
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# 即時オン{#instant-on}

即時オンでは、1 つ以上のチャネルでメディアの一部がプリロードされます。 ユーザーがチャネルを選択または切り替えた後、一部のバッファリングが既に完了しているので、コンテンツは早く開始します。

プレーヤーが `PTMediaPlayerStatusReady` ステータス、呼び出し `prepareToPlay` 後で再生するためにコンテンツの一部をプリロードして処理する場合。

>[!TIP]
>
>を呼び出さない場合 `prepareToPlay`，呼び出し `play` 自動呼び出し `prepareToPlay` 1 つ目は。 この時点で、プリロードと処理が完了します。

TVSDK は、次のタスクの一部またはすべてを完了します。 `prepareToPlay`:

* メタデータキーが `kSyncCookiesWithAVAsset` が設定されている場合、 TVSDK は元の M3U8 ファイルに対して 1 回のリクエストを実行し、Cookie を同期します。
* DRM のメタデータキーを読み込みます。
* コンテンツの再生に必要な構造、要素またはアセットを作成して準備します。

>[!TIP]
>
>The `PTMediaPlayer` および `PTMediaPlayerItem` `prepareToPlay` メソッドは等しいです。 別の `PTMediaPlayer` 各アセットのインスタンスには、 `PTMediaPlayerItem` メソッド。

即時オンを使用すると、複数のメディアプレーヤーインスタンス（メディアプレーヤーアイテムローダーインスタンス）をバックグラウンドで同時に起動し、これらすべてのインスタンスでビデオストリームをバッファーできます。 ユーザーがチャネルを変更し、ストリームが正しくバッファーされた場合、 `play` 新しいチャネルでは、早く再生を開始します。
