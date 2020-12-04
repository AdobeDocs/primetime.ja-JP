---
description: 不要になったMediaPlayerインスタンスは、リセット、再利用または解放できます。
seo-description: 不要になったMediaPlayerインスタンスは、リセット、再利用または解放できます。
seo-title: MediaPlayerインスタンスの再利用または削除
title: MediaPlayerインスタンスの再利用または削除
uuid: 0b9a06b0-ece7-4e18-9221-a4528bcbc141
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---


# MediaPlayerインスタンス{#reuse-or-remove-a-mediaplayer-instance}の再利用または削除

不要になったMediaPlayerインスタンスは、リセット、再利用または解放できます。

## MediaPlayerインスタンス{#section_C183E6164C184C3CBC5321FC6A2528EA}のリセットまたは再利用

`MediaPlayer`インスタンスをリセットして、`MediaPlayerStatus`で定義されているとおり、初期化されていないIDLE状態に戻すことができます。 また、現在のメディア項目を置き換えたり、以前に読み込まれたメディアリソースを使用して新しいメディア項目を設定したりすることもできます。

この操作は、次の場合に役立ちます。

* `MediaPlayer`インスタンスを再利用したいが、新しい`MediaResource`（ビデオコンテンツ）を読み込んで、前のインスタンスを置き換える必要がある。

   リセットすると、リソースの解放、`MediaPlayer`の再作成、リソースの再割り当てを行わなくても、`MediaPlayer`インスタンスを再利用できます。 `replaceCurrentItem`メソッドは自動的にこれらの手順を実行します。

* `MediaPlayer`がERROR状態で、クリアする必要がある場合。

   >[!IMPORTANT]
   >
   >ERROR状態から回復するには、この方法しかありません。

1. `MediaPlayer.reset()`を呼び出して、`MediaPlayer`インスタンスを初期化されていない状態に戻します。

   ```js
   reset(); // returns AdobePSDK.PSDKErrorCode.SUCCESS 
            // on successful reset
   ```

1. `MediaPlayer.replaceCurrentItem()`を呼び出して別の`MediaResource`を読み込みます

   >[!TIP]
   >
   >エラーをクリアするには、同じ`MediaResource`を読み込みます。

1. `prepareToPlay()`メソッドを呼び出します。

   >[!NOTE]
   >
   >PREPARED状態の`MediaPlaybackStatusChangeEvent.STATUS_CHANGED`イベントを受け取ったら、再生を開始できます。

## MediaPlayerインスタンスとリソース{#section_2D159975C82245098E7078FE0B1578CE}の解放

MediaResourceが不要になったら、`MediaPlayer`インスタンスとリソースを解放する必要があります。

以下に、`MediaPlayer`をリリースする理由を示します。

* 不要なリソースを保持すると、パフォーマンスに影響を与える可能性があります。
* 不要な`MediaPlayer`オブジェクトを残すと、モバイルデバイスのバッテリ消費が継続的に発生する可能性があります。
* 同じビデオコーデックの複数のインスタンスがデバイスでサポートされていない場合、他のアプリケーションで再生エラーが発生する可能性があります。

* `MediaPlayer`を解放します。

   ```js
   void release()
   ```

   >[!NOTE]
   >
   >`MediaPlayer`インスタンスを解放すると、そのインスタンスは使用できなくなります。 `MediaPlayer`インターフェイスのメソッドが解放された後に呼び出されると、`IllegalStateException`がスローされます。

