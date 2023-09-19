---
description: ブラウザー TVSDK は、他の Primetime コンポーネントと統合できる高度なビデオプレーヤーアプリケーション（Primetime プレーヤー）を作成するためのツールを提供します。
title: Flashのフェイルオーバー
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Flashのフェイルオーバー {#flash-failover}

ブラウザー TVSDK は、他の Primetime コンポーネントと統合できる高度なビデオプレーヤーアプリケーション（Primetime プレーヤー）を作成するためのツールを提供します。

プラットフォームのツールを使用して、プレーヤーを作成し、Browser TVSDK のメディアプレーヤービューに接続します。このビューには、ビデオを再生および管理するメソッドがあります。 例えば、Browser TVSDK は、再生および一時停止のメソッドを提供します。 プラットフォーム上にユーザーインターフェイスボタンを作成し、これらの Browser TVSDK メソッドを呼び出すためのボタンを設定できます。

## Flashの代替 {#section_92D3884A13A6431F9A9CC5C79715D888}

ブラウザー TVSDK では、アプリケーションは `Primetime.js` API. 基になる Browser TVSDK の実装は、現在のプラットフォームと再生するメディアのリソースタイプに基づいて、使用するプレーヤーテクノロジーを決定します。

プレーヤーテクノロジーの決定は、 `MediaPlayer.replaceCurrentResource` 特定のリソースを再生する場合。

例：

```js
var player = new AdobePSDK.MediaPlayer(), 
              mediaResource = new AdobePSDK.MediaResource(url, 
              AdobePSDK.MediaResource.Type.TYPE_HLS); 
              ... 
              player.replaceCurrentResource(mediaResource);
```

## 使用するメディアプレーヤーを決定します。 {#section_D844E386AF5848688D204DEE258ECEE6}

以下の手順の例は、プレーヤーテクノロジーを決定するプロセスを示しています。

>[!TIP]
>
>プロセスは、URL と環境によって異なる場合があります。

1. Media Source Extensions がサポートされている場合は、既知の制限なしで使用します。
1. サポートされている場合は、 `<video>` タグが直接 MSE なしで使用されます。
1. バージョン 23.0 以降のAdobeFlash Playerを使用している。
1. 適切な再生技術が見つからない場合は、 `replaceCurrentResource` はエラーを返します。

後続の `replaceCurrentResource` 同じ電話をする `MediaPlayer` インスタンスも同じプロセスに従います。 これにより、同じ `MediaPlayer` 同じ親のインスタンス `<DIV>` タグを指定します。 `MediaPlayerView` インスタンスが作成されました。

>[!TIP]
>
>SWFオブジェクトと `<video>` タグが親にネストされている `<DIV>` タグを使用します。
