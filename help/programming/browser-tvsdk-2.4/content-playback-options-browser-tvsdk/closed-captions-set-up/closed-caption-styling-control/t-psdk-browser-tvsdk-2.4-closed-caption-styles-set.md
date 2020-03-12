---
description: クローズドキャプションテキストのフォント、サイズ、色、端、不透明度などの形式を設定できます。
seo-description: クローズドキャプションテキストのフォント、サイズ、色、端、不透明度などの形式を設定できます。
seo-title: クローズドキャプションのスタイルの設定
title: クローズドキャプションのスタイルの設定
uuid: 906ed22c-e673-4211-a14b-d95d176aad21
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# クローズドキャプションのスタイルの設定{#set-closed-caption-styles}

クローズドキャプションテキストのフォント、サイズ、色、端、不透明度などの形式を設定できます。

1. がPREPARED状態 `MediaPlayer` になるまで待ちます。

   状態について詳しくは、「有効な状態を [待機する」を参照してください](../../../content-playback-options-browser-tvsdk/ui-configure/t-psdk-browser-tvsdk-2.4-ui-state-prepared-wait-for.md)。
1. インスタンスを作 `TextFormat` 成します。

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

1. （オプション）で現在のクローズドキャプションスタイル設定を取得しま `MediaPlayer.ccStyle`す。

   戻り値はインターフェイスのインスタンス `TextFormat` です。

   以前にスタイルが設定されていない場合、各属性のデフォルト値を持つTextFormatオブジェクトを返します。

   ```js
   ccStyle :AdobePSDK.TextFormat
   ```

1. スタイル設定を変更するには、を使用して、イ `MediaPlayer.ccStyle`ンターフェイスのインスタンスを渡 `TextFormat` します。

   現在のメディアストリームにクローズドキャプションがない場合でも、このメソッドを使用できます。

   ```js
   ccStyle :AdobePSDK.TextFormat 
   ```

   >[!TIP]
   >
   >クローズドキャプションのスタイルの設定は非同期的なので、変更が画面に表示されるまで数秒かかる場合があります。

