---
description: クローズドキャプションテキストのフォント、サイズ、色、端、不透明度などの形式を設定できます。
title: クローズドキャプションのスタイルの設定
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# クローズドキャプションのスタイルの設定{#set-closed-caption-styles}

クローズドキャプションテキストのフォント、サイズ、色、端、不透明度などの形式を設定できます。

1. 待機： `MediaPlayer` 少なくとも PREPARED 状態である。

   状態について詳しくは、 [有効な状態になるのを待つ](../../../content-playback-options-browser-tvsdk/ui-configure/t-psdk-browser-tvsdk-2.4-ui-state-prepared-wait-for.md).
1. の作成 `TextFormat` インスタンス。

   すべてのクローズドキャプションスタイル設定パラメーターを今すぐ指定することも、後で設定することもできます。

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

1. （オプション）現在のクローズドキャプションスタイル設定を取得する `MediaPlayer.ccStyle`.

   戻り値は、 `TextFormat` インターフェイス。

   以前にスタイルが設定されていない場合は、各属性のデフォルト値を持つ TextFormat オブジェクトが返されます。

   ```js
   ccStyle :AdobePSDK.TextFormat
   ```

1. スタイル設定を変更するには、 `MediaPlayer.ccStyle`を渡す場合、 `TextFormat` インターフェイス。

   現在のメディアストリームにクローズドキャプションがない場合でも、このメソッドを使用できます。

   ```js
   ccStyle :AdobePSDK.TextFormat 
   ```

   >[!TIP]
   >
   >クローズドキャプションスタイルの設定は非同期なので、変更が画面に表示されるまで数秒かかる場合があります。
