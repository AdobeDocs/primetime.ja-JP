---
description: よりスムーズな表示エクスペリエンスを提供するために、TVSDKはビデオストリームをバッファリングすることがあります。 プレイヤーのバッファリング方法を設定できます。
seo-description: よりスムーズな表示エクスペリエンスを提供するために、TVSDKはビデオストリームをバッファリングすることがあります。 プレイヤーのバッファリング方法を設定できます。
seo-title: バッファリング時間の設定
title: バッファリング時間の設定
uuid: 5a3945a4-1935-4797-b19d-84989850a487
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# バッファ {#buffering}

よりスムーズな表示エクスペリエンスを提供するために、TVSDKはビデオストリームをバッファリングすることがあります。 プレイヤーのバッファリング方法を設定できます。

TVSDKは、30秒以上の再生バッファー長と、メディアの再生開始前の30秒以上の初期バッファー時間を、2秒以上で定義します。 アプリケーションが呼び出 `play` した後、再生が開始される前に、TVSDKはメディアを初期時間までバッファリングし、実際に再生が開始されたときにスムーズに開始されるようにします。

新しいバッファリングポリシーを定義することでバッファー時間を変更でき、また、インスタントオンを使用して最初のバッファリングが発生するタイミングを変更できます。

## バッファリング時間の設定 {#set-buffering-times}

は、初期 `MediaPlayer` バッファリング時間と再生バッファリング時間を設定および取得するメソッドを提供します。

>[!TIP]
>
>再生を開始する前にバッファー制御パラメーターを設定しなかった場合、メディアプレイヤーは、初期バッファーが2秒、再生中のバッファー時間が30秒にデフォルト設定されます。

1. オブジェクトを設定し `BufferControlParameters` ます。このオブジェクトには、初期バッファー時間と再生バッファー時間の制御パラメーターがカプセル化されています。

       このクラスは、次の2つのファクトリメソッドを提供します。
   
   * 初期バッファー時間を再生バッファー時間と同じに設定するには：

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

      これらのメソッドは、次のよ `IllegalArgumentException` うな場合に、パラメーターが有効でない場合にスローします。

   * 初期バッファー時間が0未満です。
   * 初期バッファー時間がバッファー時間より長くなっています。

1. バッファパラメータの値を設定するには、次の方法を使用 `MediaPlayer` します。

   ```java
   void setBufferControlParameters(BufferControlParameters params)
   ```

1. 現在のバッファーパラメーター値を取得するには、次のメソッドを使用 `MediaPlayer` します。

   ```java
      BufferControlParameters getBufferControlParameters()  
   ```

   AVEが指定した値を設定できない場合、メディアプレイヤーはエラーコ `ERROR` ードを使用して状態に入りま `SET_BUFFER_PARAMETERS_ERROR`す。

<!--<a id="example_B5C5004188574D8D8AB8525742767280"></a>-->

例えば、初期バッファーを2秒に設定し、再生バッファー時間を30秒に設定するには、次のように記述します。

```java
mediaPlayer.setBufferControlParameters(BufferControlParameters.createDual(2000, 30000));
```

Primetimeリファレンスの実装では、この機能を示しています。アプリケーションの設定を使用して、バッファー値を設定します。