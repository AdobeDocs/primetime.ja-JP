---
description: カスタムスキンを使用するには、default-video-controls.cssと同様のカスタマイズを作成し、この新しいカスタマイズをプレーヤーで参照する必要があります。
title: カスタムスキン
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---


# カスタムスキン{#custom-skins}

カスタムスキンを使用するには、default-video-controls.cssと同様のカスタマイズを作成し、この新しいカスタマイズをプレーヤーで参照する必要があります。

例えば、次のいずれかのオプションを使用できます。

* `<link rel="stylesheet" href="css/common_style.css">`
* `<link rel="stylesheet" href="css/custom-video-controls1.css">`

次のタイプの変更を行うことができます。

* ボタンとテキストの前景色

   フォアグラウンドを持つすべてのコントロールは`vid-skin-fgcolor`クラスを使用します。 すべてのコントロールの前景を変更するには、`vid-skin-fgcolor`クラスを持つすべての要素を繰り返し処理し、必要な色を指定します。
* ボタンとテキストの背景色

   フォアグラウンドを持つコントロールはすべて`vid-skin-bgcolor`クラスを使用します。 すべてのコントロールの前景を変更するには、`vid-skin-bgcolor`クラスを持つすべての要素を繰り返し処理し、必要な色を指定します。
* 再生ヘッドの形状

   再生ヘッドは、正方形または円形にできます。 再生ヘッドを変更するには、`square`または`round`クラスを`playhead`要素に追加します。
* バッファリングスピナーのスタイル

   参照プレーヤーは、プレイヤーがコンテンツをバッファリングする際に、次のスタイルのスピナーを表示できます。

   * オーバーレイテキスト(`overlay-text`)
   * 矩形のスピナー(`spinner`)
   * シグナル(`signal`)
   * 縦棒グラフ(`vertical`)

      >[!TIP]
      >
      >バッファリングスピナーのいずれかを使用するには、buffering-overlay要素にクラスを追加する必要があります。 例えば、`overlay-text`を使用するには、`BufferOverlay.js`ファイルに次の行を追加します。
      >
      >
      ```js
      >var overlay = document.getElementById("buffering-overlay"); 
      >overlay.classList.add ("spinner");
      >```

