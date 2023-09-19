---
description: MediaPlayer には、初期バッファリング時間と再生バッファリング時間を設定および取得するメソッドが用意されています。
title: バッファリング時間の設定
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# バッファリング時間の設定{#set-buffering-times}

MediaPlayer には、初期バッファリング時間と再生バッファリング時間を設定および取得するメソッドが用意されています。

>[!TIP]
>
>再生を開始する前にバッファー制御パラメーターを設定しない場合、メディアプレーヤーでは、初期バッファーが 2 秒、進行中の再生バッファー時間が 30 秒にデフォルト設定されます。

1. を設定します。 `BufferControlParameters` 初期バッファー時間と再生バッファー時間の制御パラメーターをカプセル化するオブジェクト。

       このクラスは、次のファクトリメソッドを提供します。
   
   * 初期バッファ時間を再生バッファ時間と等しく設定するには：

     ```
     createSimple(bufferTime:uint):BufferControlParameters
     ```

   * 初期バッファ時間と再生バッファ時間の両方を設定するには：

     ```
     createDual(initialBufferTime:uint, playbackBufferTime:uint):BufferControlParameters 
     ```

     これらのメソッドでは、 `IllegalArgumentException` の場合は、次のように指定します。

   * 初期バッファ時間が 0 未満です。
   * 初期バッファ時間がバッファ時間より長い。

1. バッファパラメータの値を設定するには、次を使用します。 `MediaPlayer` メソッド：

   ```
   public function set bufferControlParameters(value:BufferControlParameters):void
   ```

1. 現在のバッファパラメータの値を取得するには、次を使用します。 `MediaPlayer` メソッド：

   ```
   public function get bufferControlParameters():BufferControlParameters
   ```

<!--<a id="example_B5C5004188574D8D8AB8525742767280"></a>-->

例えば、最初のバッファーを 2 秒に、再生バッファー時間を 30 秒に設定するには、次のように記述します。

```
mediaPlayer.bufferControlParameters = BufferControlParameters.createDual(2000, 30000); 
```

The `psdkdemo` この機能を示します。アプリケーションの設定を使用して、バッファ値を設定します。
