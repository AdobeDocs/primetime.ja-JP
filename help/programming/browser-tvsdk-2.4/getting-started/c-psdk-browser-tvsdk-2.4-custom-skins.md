---
description: カスタムスキンを使用するには、 default-video-controls.css と同様のカスタマイズを記述し、この新しいカスタマイズをプレーヤーで参照する必要があります。
title: カスタムスキン
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---

# カスタムスキン{#custom-skins}

カスタムスキンを使用するには、 default-video-controls.css と同様のカスタマイズを記述し、この新しいカスタマイズをプレーヤーで参照する必要があります。

例えば、次のいずれかのオプションを使用できます。

* `<link rel="stylesheet" href="css/common_style.css">`
* `<link rel="stylesheet" href="css/custom-video-controls1.css">`

次のタイプの変更を行うことができます。

* ボタンとテキストの前景色

  前景を持つすべてのコントロールは、 `vid-skin-fgcolor` クラス。 すべてのコントロールの前景を変更するには、 `vid-skin-fgcolor` クラスを選択し、目的の色を指定します。
* ボタンとテキストの背景色

  前景を持つすべてのコントロールは、 `vid-skin-bgcolor` クラス。 すべてのコントロールの前景を変更するには、 `vid-skin-bgcolor` クラスを選択し、目的の色を指定します。
* 再生ヘッドの形状

  再生ヘッドは、四角形または丸型にすることができます。 再生ヘッドを変更するには、 `square` または `round` ～へのクラス `playhead` 要素を選択します。
* バッファリングスピナーのスタイル

  リファレンスプレーヤは、プレーヤがコンテンツをバッファリングする際に、次のスタイルのスピナーを表示できます。

   * オーバーレイテキスト ( `overlay-text`)
   * 長方形スピナー ( `spinner`)
   * シグナル ( `signal`)
   * 縦棒グラフ ( `vertical`)

     >[!TIP]
     >
     >バッファリングスピナーを使用するには、 buffering-overlay 要素にクラスを追加する必要があります。 例えば、 `overlay-text`をクリックし、 `BufferOverlay.js` ファイル：
     >
     >```js
     >var overlay = document.getElementById("buffering-overlay"); 
     >overlay.classList.add ("spinner");
     >```
     >
