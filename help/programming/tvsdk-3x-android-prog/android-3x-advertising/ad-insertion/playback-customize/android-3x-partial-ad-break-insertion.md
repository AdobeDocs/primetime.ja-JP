---
title: 部分的な広告ブレーク挿入
description: 部分的な広告ブレーク挿入
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# 部分的な広告ブレーク挿入 {#partial-ad-break-insertion}

ライブストリーム内の広告の途中で TV と同じようにエクスペリエンスを結合できます。 部分的な広告ブレーク機能を使用すると、テレビのようなエクスペリエンスを模倣できます。クライアントがミッドロール内でライブストリームを開始すると、そのミッドロール内で開始します。 TV チャンネルに切り替えるのと似ており、CM はシームレスに動きます。

例えば、ユーザーが 90 秒の広告ブレーク（3 つの 30 秒の広告）の途中、2 番目の広告に 10 秒（つまり、40 秒で広告ブレークに）加わった場合、次のことが起こります。

* 2 番目の広告は、残りの時間（20 秒）に続いて 3 番目の広告で再生されます。
* 部分的に再生された広告（2 番目の広告）の広告トラッカーは実行されません。 3 番目の広告のトラッカーのみが実行されます。

この動作は、デフォルトでは有効になっていません。 アプリでこの機能を有効にするには、以下の手順を実行します。

部分的な広告ブレーク挿入の環境設定をオンにします。 新しいメソッドを使用 `setPartialAdBreakPref` MediaPlayer インターフェイスでこの機能をオンに切り替えます。 用途 `getPartialAdBreakPref` メソッドを使用して、この環境設定の現在の状態を検索します。

```
    MediaPlayer mediaPlayer = new MediaPlayer(getActivity(). getApplicationContext()); 
    mediaPlayer.setPartialAdBreakPref(true);
```

プリロール広告がある場合は、その広告が再生され、ライブポイントからコンテンツが再生されて、ライブテレビのエクスペリエンスがエミュレートされます。
