---
description: ブラウザーTVSDKは、他のPrimetimeコンポーネントと統合できる高度なビデオプレーヤーアプリケーション（Primetimeプレイヤー）を作成するためのツールを提供します。
seo-description: ブラウザーTVSDKは、他のPrimetimeコンポーネントと統合できる高度なビデオプレーヤーアプリケーション（Primetimeプレイヤー）を作成するためのツールを提供します。
seo-title: 'null'
title: 'null'
uuid: 57b35a5f-87f8-41a2-ad85-300b999dc30b
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# フラッシュフェイルオーバー {#flash-failover}

ブラウザーTVSDKは、他のPrimetimeコンポーネントと統合できる高度なビデオプレーヤーアプリケーション（Primetimeプレイヤー）を作成するためのツールを提供します。

プラットフォームのツールを使用して、プレイヤーを作成し、ブラウザーTVSDKのメディアプレイヤービューに接続します。このビューには、ビデオの再生および管理のメソッドがあります。 例えば、ブラウザーTVSDKは、再生および一時停止のメソッドを提供します。 プラットフォーム上にユーザーインターフェイスボタンを作成し、これらのボタンを設定して、これらのブラウザーTVSDKメソッドを呼び出すことができます。

## Flashフォールバック {#section_92D3884A13A6431F9A9CC5C79715D888}

ブラウザーTVSDKでは、アプリケーションはAPIとのみ対話し `Primetime.js` ます。 基盤となるブラウザーTVSDKの実装は、現在のプラットフォームと、再生するメディアのリソースタイプに基づいて、使用するプレーヤーテクノロジーを決定します。

プレイヤー技術の決定は、特定のリソースを再生するように呼び出す `MediaPlayer.replaceCurrentResource` まで行われません。

例：

```js
var player = new AdobePSDK.MediaPlayer(), 
              mediaResource = new AdobePSDK.MediaResource(url, 
              AdobePSDK.MediaResource.Type.TYPE_HLS); 
              ... 
              player.replaceCurrentResource(mediaResource);
```

## 使用するメディアプレイヤーの決定 {#section_D844E386AF5848688D204DEE258ECEE6}

次のサンプル手順は、プレーヤーの技術を決定するプロセスを示しています。

>[!TIP]
>
>プロセスは、URLと環境によって異なる場合があります。

1. Media Source Extensionsがサポートされている場合は、既知の制限なしで使用します。
1. サポートされている場合は、MSEを使用せず `<video>` にタグを直接使用します。
1. Adobe Flash Playerバージョン23.0以上を使用していることを確認します。
1. 適切な再生技術が見つからない場合は、 `replaceCurrentResource` エラーを返します。

同じインスタンス `replaceCurrentResource` に対する後続の呼び出 `MediaPlayer` しは、同じプロセスに従います。 これにより、インスタンスの作成時に指定したのと同じ親タグで同じイ `MediaPlayer` ンスタンスを使用し、様々なリ `<DIV>` ソースタイプを再 `MediaPlayerView` 生することができます。

>[!TIP]
>
>SWFオブジェクトとタグ `<video>` は、親タグ内にネストさ `<DIV>` れます。

