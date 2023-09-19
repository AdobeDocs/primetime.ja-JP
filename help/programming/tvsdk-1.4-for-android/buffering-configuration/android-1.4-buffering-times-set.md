---
description: よりスムーズな表示を実現するために、 TVSDK はビデオストリームをバッファリングする場合があります。 プレーヤーでのバッファリング方法を設定できます。
title: バッファリング時間の設定
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 0%

---

# バッファリング {#buffering}

よりスムーズな表示を実現するために、 TVSDK はビデオストリームをバッファリングする場合があります。 プレーヤーでのバッファリング方法を設定できます。

TVSDK は、30 秒以上の再生バッファーの長さと、その中でのメディアの再生開始前の初期バッファー時間を、2 秒以上で定義します。 アプリケーションの呼び出し後 `play` ただし、再生が開始される前に、 TVSDK はメディアを初期時間までバッファリングして、実際に再生が開始されたときにスムーズに開始できるようにします。

新しいバッファリングポリシーを定義することで、バッファー時間を変更できます。また、インスタントオンを使用して、最初のバッファリングが発生するタイミングを変更できます。

## バッファリング時間の設定 {#set-buffering-times}

The `MediaPlayer` には、初期バッファリング時間と再生バッファリング時間を設定および取得するメソッドが用意されています。

>[!TIP]
>
>再生を開始する前にバッファー制御パラメーターを設定しない場合、メディアプレーヤーでは、初期バッファーが 2 秒、進行中の再生バッファー時間が 30 秒にデフォルト設定されます。

1. を設定します。 `BufferControlParameters` 初期バッファー時間と再生バッファー時間の制御パラメーターをカプセル化するオブジェクト。

       このクラスは、次の 2 つのファクトリメソッドを提供します。
   
   * 初期バッファ時間を再生バッファ時間と等しく設定するには：

     ```java
     public static BufferControlParameters createSimple( 
         long bufferTime)
     ```

   * 初期バッファ時間と再生バッファ時間の両方を設定するには：

     ```java
     public static BufferControlParameters createDual( 
         long initialBuffer,   
         long bufferTime)
     ```

     これらのメソッドでは、 `IllegalArgumentException` の場合は、次のように指定します。

   * 初期バッファ時間が 0 未満です。
   * 初期バッファ時間がバッファ時間より長い。

1. バッファパラメータの値を設定するには、次を使用します。 `MediaPlayer` メソッド：

   ```java
   void setBufferControlParameters(BufferControlParameters params)
   ```

1. 現在のバッファパラメータの値を取得するには、次を使用します。 `MediaPlayer` メソッド：

   ```java
      BufferControlParameters getBufferControlParameters()  
   ```

   AVE が指定した値を設定できない場合、メディアプレーヤーが `ERROR` エラーコード付きの状態 `SET_BUFFER_PARAMETERS_ERROR`.

<!--<a id="example_B5C5004188574D8D8AB8525742767280"></a>-->

例えば、最初のバッファーを 2 秒に、再生バッファー時間を 30 秒に設定するには、次のように記述します。

```java
mediaPlayer.setBufferControlParameters(BufferControlParameters.createDual(2000, 30000));
```

Primetime リファレンス実装では、この機能の例を示しています。アプリケーションの設定を使用して、バッファー値を設定します。
