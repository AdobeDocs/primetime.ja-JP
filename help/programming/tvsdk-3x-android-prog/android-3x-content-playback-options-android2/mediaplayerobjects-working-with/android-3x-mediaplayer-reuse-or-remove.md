---
description: 不要になった MediaPlayer インスタンスをリセット、再利用、またはリリースできます。
title: MediaPlayer インスタンスの再利用または削除
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---

# MediaPlayer インスタンスの再利用または削除 {#reuse-or-remove-a-mediaplayer-instance}

不要になった MediaPlayer インスタンスをリセット、再利用、またはリリースできます。

## MediaPlayer インスタンスのリセットまたは再利用 {#section_E6A2446A2D0B4ACD9EA980685B2E57D9}

をリセットしたとき `MediaPlayer` インスタンスの場合、 `MediaPlayerStatus`.

この操作は、次の場合に役立ちます。

* 次の項目を再利用します： `MediaPlayer` インスタンスを使用するが、新しい `MediaResource` （ビデオコンテンツ）をクリックし、前のインスタンスを置き換えます。

  リセットを使用すると、 `MediaPlayer` リソースを解放するオーバーヘッドがなく、 `MediaPlayer`、およびリソースの再割り当て。

* 次の場合に `MediaPlayer` は ERROR ステータスで、クリアする必要があります。

  >[!IMPORTANT]
  >
  >これは、ERROR ステータスから回復する唯一の方法です。

   1. 通話 `reset` 返す `MediaPlayer` インスタンスを初期化されていない状態に変更します。

      ```java
      void reset() throws MediaPlayerException; 
      ```

   1. 用途 `MediaPlayer.replaceCurrentResource()` 別の物を積み込む `MediaResource`.

      >[!NOTE]
      >
      >エラーをクリアするには、同じ `MediaResource`.

   1. 次を受け取ったとき： `STATUS_CHANGED` を使用したイベントコールバック `PREPARED` ステータス、再生を開始します。

## MediaPlayer インスタンスとリソースの解放 {#section_13A0914AFF784943ABC343F7EB249C4E}

以下の場合、 `MediaPlayer` 不要になったインスタンスとリソース `MediaResource`.

をリリースする際に、 `MediaPlayer` オブジェクト、このオブジェクトに関連付けられている基になるハードウェアリソース `MediaPlayer` オブジェクトの割り当てが解除されます。

以下は、 `MediaPlayer`:

* 不要なリソースを保持すると、パフォーマンスに影響を与える可能性があります。
* 不要な `MediaPlayer` オブジェクトがインスタンス化されると、モバイルデバイスで継続的にバッテリーが消費される可能性があります。
* 1 つのデバイスで同じビデオコーデックの複数のインスタンスがサポートされていない場合、他のアプリケーションで再生エラーが発生する可能性があります。

* をリリースします。 `MediaPlayer`.

  ```java
  void release() throws MediaPlayerException;
  ```

  >[!NOTE]
  >
  >次の期間の後に `MediaPlayer` インスタンスがリリースされているので、使用できなくなっています。 いずれかの方法で `MediaPlayer` インターフェイスは、リリース後に呼び出されます。 `MediaPlayerException` がスローされます。
