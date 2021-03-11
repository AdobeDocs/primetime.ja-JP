---
description: ブラウザーTVSDKは、他のPrimetimeコンポーネントと統合できる高度なビデオプレイヤーアプリケーション（Primetimeプレイヤー）を作成するためのツールを提供します。
title: Flashのフェイルオーバー
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---


# Flashフェイルオーバー{#flash-failover}

ブラウザーTVSDKは、他のPrimetimeコンポーネントと統合できる高度なビデオプレイヤーアプリケーション（Primetimeプレイヤー）を作成するためのツールを提供します。

プラットフォームのツールを使用してプレイヤーを作成し、それをブラウザーTVSDKのメディアプレイヤー表示に接続します。このメソッドは、ビデオの再生と管理を行うメソッドを備えています。 例えば、Browser TVSDKは、再生メソッドと一時停止メソッドを提供します。 プラットフォーム上にユーザーインターフェイスボタンを作成し、これらのブラウザーTVSDKメソッドを呼び出すボタンを設定できます。

## Flashフォールバック{#section_92D3884A13A6431F9A9CC5C79715D888}

ブラウザーTVSDKでは、アプリケーションは`Primetime.js` APIとのみ対話します。 基盤となるBrowser TVSDKの実装は、再生するメディアの現在のプラットフォームとリソースタイプに基づいて、使用するプレイヤーテクノロジーを決定します。

プレイヤーテクノロジの決定は、`MediaPlayer.replaceCurrentResource`を呼び出して特定のリソースを再生するまで行われません。

例：

```js
var player = new AdobePSDK.MediaPlayer(), 
              mediaResource = new AdobePSDK.MediaResource(url, 
              AdobePSDK.MediaResource.Type.TYPE_HLS); 
              ... 
              player.replaceCurrentResource(mediaResource);
```

## {#section_D844E386AF5848688D204DEE258ECEE6}

以下の手順の例は、プレーヤーの技術を決定するプロセスを示しています。

>[!TIP]
>
>処理は、URLや環境によって異なる場合があります。

1. Media Source Extensionsがサポートされている場合は、既知の制限なしで使用します。
1. サポートされている場合は、MSEを使用せずに直接`<video>`タグを使用します。
1. 少なくともAdobeFlash Playerバージョン23.0を使用していることを確認してください。
1. 適切な再生技術が見つからない場合、`replaceCurrentResource`はエラーを返します。

同じ`MediaPlayer`インスタンスに対する後続の`replaceCurrentResource`呼び出しは、同じプロセスに従います。 これにより、`MediaPlayerView`インスタンスの作成時に指定したのと同じ親`<DIV>`タグで、同じ`MediaPlayer`インスタンスを使用して、様々なリソースタイプを再生できます。

>[!TIP]
>
>SWFオブジェクトと`<video>`タグは、親の`<DIV>`タグ内にネストされます。

