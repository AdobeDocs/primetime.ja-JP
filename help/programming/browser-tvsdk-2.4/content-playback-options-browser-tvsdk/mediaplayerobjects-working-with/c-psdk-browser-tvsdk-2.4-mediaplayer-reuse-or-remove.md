---
description: 不要になった MediaPlayer インスタンスをリセット、再利用、またはリリースできます。
title: MediaPlayer インスタンスの再利用または削除
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# MediaPlayer インスタンスの再利用または削除{#reuse-or-remove-a-mediaplayer-instance}

不要になった MediaPlayer インスタンスをリセット、再利用、またはリリースできます。

## MediaPlayer インスタンスのリセットまたは再利用 {#section_C183E6164C184C3CBC5321FC6A2528EA}

以下を実行すると、 `MediaPlayer` インスタンスを使用して、 `MediaPlayerStatus`. また、現在のメディア項目を置き換えたり、以前に読み込んだメディアリソースを使用して新しいメディア項目を設定したりすることもできます。

この操作は、次の場合に役立ちます。

* 次の項目を再利用します： `MediaPlayer` インスタンスを使用するが、新しい `MediaResource` （ビデオコンテンツ）をクリックし、前のインスタンスを置き換えます。

  リセットを使用すると、 `MediaPlayer` リソースを解放するオーバーヘッドがなく、 `MediaPlayer`、およびリソースの再割り当て。 The `replaceCurrentItem` メソッドは、これらの手順を自動的に実行します。

* 次の場合に `MediaPlayer` は ERROR 状態であり、クリアする必要があります。

  >[!IMPORTANT]
  >
  >これは、ERROR 状態から回復する唯一の方法です。

1. 通話 `MediaPlayer.reset()` 返す `MediaPlayer` インスタンスを初期化されていない状態に変更します。

   ```js
   reset(); // returns AdobePSDK.PSDKErrorCode.SUCCESS 
            // on successful reset
   ```

1. 通話 `MediaPlayer.replaceCurrentItem()` 別の物を積み込む `MediaResource`

   >[!TIP]
   >
   >エラーをクリアするには、同じ `MediaResource`.

1. を呼び出します。 `prepareToPlay()` メソッド。

   >[!NOTE]
   >
   >次を受け取ったとき： `MediaPlaybackStatusChangeEvent.STATUS_CHANGED` イベントに PREPARED ステートが含まれる場合は、再生を開始できます。

## MediaPlayer インスタンスとリソースの解放 {#section_2D159975C82245098E7078FE0B1578CE}

以下の場合、 `MediaPlayer` インスタンスとリソースを使用します（MediaResource が不要になった場合）。

以下は、 `MediaPlayer`:

* 不要なリソースを保持すると、パフォーマンスに影響を与える可能性があります。
* 不要な `MediaPlayer` オブジェクトは、モバイルデバイスのバッテリ消費を継続的に引き起こす可能性があります。
* 1 つのデバイスで同じビデオコーデックの複数のインスタンスがサポートされていない場合、他のアプリケーションで再生エラーが発生する可能性があります。

* をリリースします。 `MediaPlayer`.

  ```js
  void release()
  ```

  >[!NOTE]
  >
  >次の期間の後に `MediaPlayer` インスタンスがリリースされているので、使用できなくなっています。 いずれかの方法で `MediaPlayer` インターフェイスは、リリース後に呼び出されます。 `IllegalStateException` がスローされます。
