---
description: カスタムスキンを使用するには、default-video-controls.cssと同様のカスタマイズを作成し、この新しいカスタマイズをプレーヤーで参照する必要があります。
seo-description: カスタムスキンを使用するには、default-video-controls.cssと同様のカスタマイズを作成し、この新しいカスタマイズをプレーヤーで参照する必要があります。
seo-title: カスタムスキン
title: カスタムスキン
uuid: bc71926e-0dec-4628-8248-911224a7a6c2
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# カスタムスキン{#custom-skins}

カスタムスキンを使用するには、default-video-controls.cssと同様のカスタマイズを作成し、この新しいカスタマイズをプレーヤーで参照する必要があります。

例えば、次のいずれかのオプションを使用できます。

* `<link rel="stylesheet" href="css/common_style.css">`
* `<link rel="stylesheet" href="css/custom-video-controls1.css">`

次のタイプの変更を行うことができます。

* ボタンとテキストの前景色

   フォアグラウンドを持つすべてのコントロールは、このクラスを使用 `vid-skin-fgcolor` します。 すべてのコントロールの前景を変更するには、クラスを持つすべての要素を繰り返し処理し、 `vid-skin-fgcolor` 必要な色を指定します。
* ボタンとテキストの背景色

   フォアグラウンドを持つすべてのコントロールが、このクラスを使用し `vid-skin-bgcolor` ています。 すべてのコントロールの前景を変更するには、クラスを持つすべての要素を繰り返し処理し、 `vid-skin-bgcolor` 必要な色を指定します。
* 再生ヘッドの形状

   再生ヘッドは、正方形または円形にすることができます。 再生ヘッドを変更するには、要素に `square` クラス `round` を追加し `playhead` ます。
* バッファリングスピナーのスタイル

   参照プレーヤーは、プレーヤーがコンテンツをバッファリングする際に、次のスタイルのスピナーを表示できます。

   * オーバーレイテキスト( `overlay-text`)
   * [矩形]スピナー( `spinner`)
   * シグナル( `signal`)
   * 縦棒グラフ( `vertical`)

      >[!TIP]
      >
      >バッファリングスピナーを使用するには、buffering-overlay要素にクラスを追加する必要があります。 例えば、を使用するに `overlay-text`は、次の行をファイルに追加し `BufferOverlay.js` ます。      >
      >
      >
      ```js      >
      >var overlay = document.getElementById("buffering-overlay"); 
      >overlay.classList.add ("spinner");
      >```      >
      >



