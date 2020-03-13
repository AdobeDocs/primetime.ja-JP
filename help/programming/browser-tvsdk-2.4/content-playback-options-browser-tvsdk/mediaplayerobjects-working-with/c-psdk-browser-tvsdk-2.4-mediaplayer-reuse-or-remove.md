---
description: 不要になったMediaPlayerインスタンスは、リセット、再利用または解放できます。
seo-description: 不要になったMediaPlayerインスタンスは、リセット、再利用または解放できます。
seo-title: MediaPlayerインスタンスの再利用または削除
title: MediaPlayerインスタンスの再利用または削除
uuid: 0b9a06b0-ece7-4e18-9221-a4528bcbc141
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# MediaPlayerインスタンスの再利用または削除{#reuse-or-remove-a-mediaplayer-instance}

不要になったMediaPlayerインスタンスは、リセット、再利用または解放できます。

## MediaPlayerインスタンスのリセットまたは再利用 {#section_C183E6164C184C3CBC5321FC6A2528EA}

インスタンスをリセッ `MediaPlayer` トして、で定義されている、初期化されていないIDLE状態に戻すことができま `MediaPlayerStatus`す。 また、現在のメディア項目を置き換えたり、以前に読み込んだメディアリソースを使用して新しいメディア項目を設定したりすることもできます。

この操作は、次の場合に役立ちます。

* インスタンスを再利用したいが、 `MediaPlayer` 新しい（ビデオコンテンツ）を読み込ん `MediaResource` で、前のインスタンスを置き換える必要がある。

   リセットすると、リソースの解放、再 `MediaPlayer` 作成およびリソースの再割り当てを行うオーバーヘッドなしで、インスタ `MediaPlayer`ンスを再利用できます。 これらの `replaceCurrentItem` 手順は、メソッドによって自動的に実行されます。

* がERROR状態 `MediaPlayer` で、クリアする必要がある場合。

   >[!IMPORTANT]
   >
   >これは、ERROR状態から回復する唯一の方法です。

1. インスタ `MediaPlayer.reset()` ンスを初期化されて `MediaPlayer` いない状態に戻すための呼び出し：

   ```js
   reset(); // returns AdobePSDK.PSDKErrorCode.SUCCESS 
            // on successful reset
   ```

1. 別の `MediaPlayer.replaceCurrentItem()``MediaResource`

   >[!TIP]
   >
   >エラーをクリアするには、同じエラーを読み込みま `MediaResource`す。

1. メソッドを呼び `prepareToPlay()` 出します。

   >[!NOTE]
   >
   >PREPARED状態のイベント `MediaPlaybackStatusChangeEvent.STATUS_CHANGED` を受け取ったら、再生を開始できます。

## MediaPlayerインスタンスとリソースの解放 {#section_2D159975C82245098E7078FE0B1578CE}

MediaResourceが不要になった場合は、イ `MediaPlayer` ンスタンスとリソースを解放する必要があります。

以下に、をリリースする理由を示しま `MediaPlayer`す。

* 不要なリソースを保持すると、パフォーマンスに影響を与える可能性があります。
* 不要な物体を残す `MediaPlayer` と、モバイルデバイスのバッテリー消費が継続的に発生する可能性があります。
* 同じビデオコーデックの複数のインスタンスがデバイスでサポートされていない場合、他のアプリケーションで再生エラーが発生する可能性があります。

* を解放しま `MediaPlayer`す。

   ```js
   void release()
   ```

   >[!NOTE]
   >
   >インスタンス `MediaPlayer` を解放した後は、使用できなくなります。 インターフェイスのメソッド `MediaPlayer` が解放された後に呼び出された場合、がスロ `IllegalStateException` ーされます。

