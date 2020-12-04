---
description: クローズドキャプションテキストのフォント、サイズ、色、端、不透明度などの形式を設定できます。
seo-description: クローズドキャプションテキストのフォント、サイズ、色、端、不透明度などの形式を設定できます。
seo-title: クローズドキャプションのスタイルの設定
title: クローズドキャプションのスタイルの設定
uuid: 906ed22c-e673-4211-a14b-d95d176aad21
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---


# クローズドキャプションのスタイルを設定{#set-closed-caption-styles}

クローズドキャプションテキストのフォント、サイズ、色、端、不透明度などの形式を設定できます。

1. `MediaPlayer`がPREPARED状態になるまで待ちます。

   状態について詳しくは、[有効な状態を待つ](../../../content-playback-options-browser-tvsdk/ui-configure/t-psdk-browser-tvsdk-2.4-ui-state-prepared-wait-for.md)を参照してください。
1. `TextFormat`インスタンスを作成します。

   すべてのクローズドキャプションのスタイル設定パラメーターを指定するか、後で設定することができます。

   ```js
   new TextFormat( 
       font,   
       fontColor,  
       edgeColor,   
       fontEdge,  
       backgroundColor,   
       fillColor,  
       size,   
       fontOpacity,   
       backgroundOpacity,  
       fillOpacity, 
       bottomInset 
       safeArea) → {AdobePSDK.TextFormat}
   ```

1. （オプション）`MediaPlayer.ccStyle`を使用して、現在のクローズドキャプションスタイル設定を取得します。

   戻り値は`TextFormat`インターフェイスのインスタンスです。

   以前にスタイルが設定されていない場合は、各属性のデフォルト値を持つTextFormatオブジェクトを返します。

   ```js
   ccStyle :AdobePSDK.TextFormat
   ```

1. スタイル設定を変更するには、`MediaPlayer.ccStyle`を使用して、`TextFormat`インターフェイスのインスタンスを渡します。

   現在のメディアストリームにクローズドキャプションがない場合でも、このメソッドを使用できます。

   ```js
   ccStyle :AdobePSDK.TextFormat 
   ```

   >[!TIP]
   >
   >クローズドキャプションのスタイルの設定は非同期的なので、変更が画面に表示されるまでに数秒かかる場合があります。

