---
description: 不要になったMediaPlayerインスタンスは、リセット、再利用または解放できます。
seo-description: 不要になったMediaPlayerインスタンスは、リセット、再利用または解放できます。
seo-title: MediaPlayerインスタンスの再利用または削除
title: MediaPlayerインスタンスの再利用または削除
uuid: 74a46689-1708-4d26-9a4e-a4cdb0e55451
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# MediaPlayerインスタンスの再利用または削除 {#reuse-or-remove-a-mediaplayer-instance}

不要になったMediaPlayerインスタンスは、リセット、再利用または解放できます。

## MediaPlayerインスタンスのリセットまたは再利用 {#section_E6A2446A2D0B4ACD9EA980685B2E57D9}

インスタンスをリセッ `MediaPlayer` トすると、で定義されている、初期化されていないIDLEステータスに戻りま `MediaPlayerStatus`す。

この操作は、次の場合に役立ちます。

* インスタンスを再利用したいが、 `MediaPlayer` 新しい（ビデオコンテンツ）を読み込ん `MediaResource` で、前のインスタンスを置き換える必要がある。

   リセットすると、リソースの解放、再 `MediaPlayer` 作成およびリソースの再割り当てを行うオーバーヘッドなしで、インスタ `MediaPlayer`ンスを再利用できます。

* がERRORステー `MediaPlayer` タスで、クリアする必要がある場合。

   >[!IMPORTANT]
   >
   >これは、ERRORステータスから回復する唯一の方法です。

   1. インスタ `reset` ンスを初期化されて `MediaPlayer` いない状態に戻すための呼び出し：

      ```java
      void reset() throws MediaPlayerException; 
      ```

   1. を使用し `MediaPlayer.replaceCurrentResource()` て、別のを読み込みま `MediaResource`す。

      >[!NOTE]
      >
      >エラーをクリアするには、同じエラーを読み込みま `MediaResource`す。

   1. ステータスのイベントコー `STATUS_CHANGED` ルバックを受け `PREPARED` 取ったら、再生を開始します。

## MediaPlayerインスタンスとリソースの解放 {#section_13A0914AFF784943ABC343F7EB249C4E}

不要になった場合は、 `MediaPlayer` インスタンスとリソースを解放する必要がありま `MediaResource`す。

オブジェクトを解放す `MediaPlayer` ると、このオブジェクトに関連付けられている基になるハードウェアリソ `MediaPlayer` ースの割り当てが解除されます。

以下に、をリリースする理由を示しま `MediaPlayer`す。

* 不要なリソースを保持すると、パフォーマンスに影響を与える可能性があります。
* 不要なオブジェクトをイ `MediaPlayer` ンスタンス化したままにすると、モバイルデバイスのバッテリ消費が継続的に発生する可能性があります。
* 同じビデオコーデックの複数のインスタンスがデバイスでサポートされていない場合、他のアプリケーションで再生エラーが発生する可能性があります。

* を解放しま `MediaPlayer`す。

   ```java
   void release() throws MediaPlayerException;
   ```

   >[!NOTE]
   >
   >インスタンス `MediaPlayer` を解放した後は、使用できなくなります。 インターフェイスのメソッド `MediaPlayer` が解放された後に呼び出された場合、がスロ `MediaPlayerException` ーされます。