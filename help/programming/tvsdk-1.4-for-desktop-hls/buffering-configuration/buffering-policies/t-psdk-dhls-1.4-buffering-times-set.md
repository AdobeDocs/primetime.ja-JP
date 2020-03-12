---
description: MediaPlayerは、初期バッファリング時間と再生バッファリング時間を設定および取得するメソッドを提供します。
seo-description: MediaPlayerは、初期バッファリング時間と再生バッファリング時間を設定および取得するメソッドを提供します。
seo-title: バッファリング時間の設定
title: バッファリング時間の設定
uuid: 25142b01-5381-49c9-b89a-24c858faaf13
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# バッファリング時間の設定{#set-buffering-times}

MediaPlayerは、初期バッファリング時間と再生バッファリング時間を設定および取得するメソッドを提供します。

>[!TIP]
>
>再生を開始する前にバッファー制御パラメーターを設定しなかった場合、メディアプレイヤーは、初期バッファーが2秒、再生中のバッファー時間が30秒にデフォルト設定されます。

1. オブジェクトを設定し `BufferControlParameters` ます。このオブジェクトには、初期バッファー時間と再生バッファー時間の制御パラメーターがカプセル化されています。

       このクラスは、次のファクトリメソッドを提供します。
   
   * 初期バッファー時間を再生バッファー時間と同じに設定するには：

      ```
      createSimple(bufferTime:uint):BufferControlParameters
      ```

   * 初期バッファー時間と再生バッファー時間の両方を設定するには：

      ```
      createDual(initialBufferTime:uint, playbackBufferTime:uint):BufferControlParameters 
      ```

      これらのメソッドは、次のよ `IllegalArgumentException` うな場合に、パラメーターが有効でない場合にスローします。

   * 初期バッファー時間が0未満です。
   * 初期バッファー時間がバッファー時間より長くなっています。

1. バッファパラメータの値を設定するには、次の方法を使用 `MediaPlayer` します。

   ```
   public function set bufferControlParameters(value:BufferControlParameters):void
   ```

1. 現在のバッファーパラメーター値を取得するには、次のメソッドを使用 `MediaPlayer` します。

   ```
   public function get bufferControlParameters():BufferControlParameters
   ```

<!--<a id="example_B5C5004188574D8D8AB8525742767280"></a>-->

例えば、初期バッファーを2秒に設定し、再生バッファー時間を30秒に設定するには、次のように記述します。

```
mediaPlayer.bufferControlParameters = BufferControlParameters.createDual(2000, 30000); 
```

は、この `psdkdemo` 機能を示します。アプリケーションの設定を使用して、バッファー値を設定します。
