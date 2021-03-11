---
description: よりスムーズな表示エクスペリエンスを提供するために、TVSDKはビデオストリームをバッファリングすることがあります。 プレイヤーのバッファリング方法を設定できます。
title: バッファリング時間の設定
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 0%

---


# バッファリング{#buffering}

よりスムーズな表示エクスペリエンスを提供するために、TVSDKはビデオストリームをバッファリングすることがあります。 プレイヤーのバッファリング方法を設定できます。

TVSDKは、再生バッファーの長さを30秒以上にし、それ以内の初期バッファー時間をメディア開始が再生するまでの2秒以上に定義します。 アプリケーションが`play`を呼び出した後、再生が開始される前に、TVSDKはメディアを初期時間までバッファリングし、実際に再生中の開始がスムーズに開始されるようにします。

新しいバッファリングポリシーを定義してバッファー時間を変更したり、インスタントオンを使用して最初のバッファリングが発生するタイミングを変更したりできます。

## バッファリング時間の設定{#set-buffering-times}

`MediaPlayer`は、初期バッファリング時間と再生バッファリング時間を設定および取得するメソッドを提供します。

>[!TIP]
>
>再生を開始する前にバッファー制御パラメーターを設定しなかった場合、メディアプレイヤーはデフォルトで、初期バッファーが2秒、継続中の再生バッファー時間が30秒に設定されます。

1. `BufferControlParameters`オブジェクトを設定します。このオブジェクトには、初期バッファー時間と再生バッファー時間の制御パラメーターがカプセル化されています。

       このクラスは、次の2つのファクトリメソッドを提供します。
   
   * 初期バッファー時間を再生バッファー時間と等しく設定するには：

      ```java
      public static BufferControlParameters createSimple( 
          long bufferTime)
      ```

   * 初期バッファー時間と再生バッファー時間の両方を設定するには：

      ```java
      public static BufferControlParameters createDual( 
          long initialBuffer,   
          long bufferTime)
      ```

      これらのメソッドは、次のような場合に、パラメーターが有効でない場合は`IllegalArgumentException`をスローします。

   * 初期バッファー時間が0未満です。
   * 初期バッファー時間がバッファー時間より長くなっています。

1. バッファパラメータの値を設定するには、次の`MediaPlayer`メソッドを使用します。

   ```java
   void setBufferControlParameters(BufferControlParameters params)
   ```

1. 現在のバッファーパラメーター値を取得するには、次の`MediaPlayer`メソッドを使用します。

   ```java
      BufferControlParameters getBufferControlParameters()  
   ```

   AVEが指定された値を設定できない場合、メディアプレイヤーは`SET_BUFFER_PARAMETERS_ERROR`というエラーコードを持つ`ERROR`状態に入ります。

<!--<a id="example_B5C5004188574D8D8AB8525742767280"></a>-->

例えば、初期バッファーを2秒に設定し、再生バッファー時間を30秒に設定するには、次のように記述します。

```java
mediaPlayer.setBufferControlParameters(BufferControlParameters.createDual(2000, 30000));
```

Primetimeリファレンスの実装では、この機能の例を示しています。アプリケーションの設定を使用して、バッファー値を設定します。