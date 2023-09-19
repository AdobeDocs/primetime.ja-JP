---
description: クローズドキャプションの表示を制御できます。 表示がオンの場合は、現在選択されているトラックが表示されます。 現在のトラックを変更した場合、表示設定は変わりません。
title: クローズドキャプションの表示を制御する
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# クローズドキャプションの表示を制御する{#control-closed-caption-visibility}

クローズドキャプションの表示を制御できます。 表示がオンの場合は、現在選択されているトラックが表示されます。 現在のトラックを変更した場合、表示設定は変わりません。

>[!TIP]
>
>プレーヤーがシークモードに入ったときにクローズドキャプションテキストが表示される場合、シークが完了した後にテキストが表示されなくなります。 代わりに、数秒後に、 TVSDK はビデオ内のシーク終了位置の後に、次のクローズドキャプションテキストを表示します。

>[!NOTE]
>
>クローズドキャプションの表示値は、 `ClosedCaptionsVisibility`.
>
>```
>public static const HIDDEN:String = hidden; 
>public static const VISIBLE:String = visible;
>```
>

1. 待機： `MediaPlayer` 少なくとも PREPARED ステータスを持つには ( [有効な状態になるのを待つ](../../t-psdk-dhls-1.4-configure/c-psdk-dhls-1.4-ui-configure/t-psdk-dhls-1.4-ui-state-prepared-wait-for.md)) をクリックします。
1. クローズドキャプションの現在の表示設定を取得するには、 `MediaPlayer`：表示値を返します。

   ```
   public function get ccVisibility():String
   ```

1. クローズドキャプションの表示を変更するには、setter メソッドを使用して、表示値を `ClosedCaptionsVisibility`.

   例：

   ```
   public function set ccVisibility(value:String):void
   ```

1. ドロップダウンリストを定義します。

   ```
   <s:DropDownList id="ccTracksList" width="85" 
                   dataProvider="{_ccTracks}" 
                   change="onCCTrackChange(event)" 
                   prompt="CC"/>
   ```

1. クローズドキャプショントラックのバインド可能な配列を定義します。

   ```
   [Bindable] private var _ccTracks:ArrayCollection =  
     new ArrayCollection(); // active tracks 
   ```

1. リスナーを設定します。

   ```
   player.addEventListener(MediaPlayerItemEvent.ITEM_CREATED, onItemCreated); 
   player.addEventListener(MediaPlayerItemEvent.CAPTIONS_UPDATED, onCaptionUpdated);
   ```

   破壊コードからリスナーを削除するには、次の手順に従います。

   ```
   player.removeEventListener(MediaPlayerItemEvent.ITEM_CREATED, onItemCreated); 
   player.removeEventListener(MediaPlayerItemEvent.CAPTIONS_UPDATED, onCaptionUpdated);
   ```

1. ユーザーがリストから選択を行った場合は、リストを作成および更新します。

   ```
   private function onCCTrackChange(event:IndexChangeEvent):void { 
       var ccTrackIndex:int = event.newIndex; 
       var ccTracks:Vector.<ClosedCaptionsTrack> =  
         _player.currentItem.closedCaptionsTracks; 
       if (ccTrackIndex == 0) { 
           _player.ccVisibility = MediaPlayer.INVISIBLE; 
       } 
       else if (ccTrackIndex <= _ccTracks.length) { 
           var index:Number = findFromActiveIndex(ccTracks, ccTrackIndex - 1); 
           _player.currentItem.selectClosedCaptionsTrack(ccTracks[index]); 
           _player.ccVisibility = MediaPlayer.VISIBLE; 
       } 
   } 
   
   private function findFromActiveIndex(ccTracks:Vector.<ClosedCaptionsTrack>,  
     ccTrackIndex:int):Number { 
       var count:Number = 0; 
       for each (var ccTrack:ClosedCaptionsTrack in ccTracks) { 
           if (count < ccTrackIndex) 
               count = count + 1; 
           else 
               return count; 
       } 
       return -1; 
   } 
   
   private function onItemCreated(event:MediaPlayerItemEvent):void { 
       ... (you are likely to need more code here for other reasons) 
       updateCCTracks(_player.currentItem.closedCaptionsTracks); 
   } 
   
   private function onCaptionUpdated(event:MediaPlayerItemEvent):void { 
       ... (you are likely to need more code here for other reasons) 
       updateCCTracks(_player.currentItem.closedCaptionsTracks,  
                     (_player.ccVisibility == MediaPlayer.VISIBLE) ?  
                      _player.currentItem.selectedClosedCaptionsTrack : null); 
   } 
   
   private function updateCCTracks(tracks:Vector.<ClosedCaptionsTrack>,  
     selectedTrack:ClosedCaptionsTrack = null):void { 
       _ccTracks.removeAll(); 
   
       _ccTracks.addItem( 
           { 
               "label": "CC off", 
               "data": "cc-off" 
           } 
       ); 
   
       var selectedIndex:int = 0; 
       for each (var ccTrack:ClosedCaptionsTrack in tracks) { 
           _ccTracks.addItem( 
               { 
                   "label": ccTrack.name, 
                   "data": ccTrack.name 
               } 
           ); 
           if (selectedTrack && ccTrack.name == selectedTrack.name && 
           ccTrack.language == selectedTrack.language && 
           ccTrack.serviceType == selectedTrack.serviceType) { 
               selectedIndex = _ccTracks.length - 1; 
           } 
       } 
   
       var hasCC:Boolean = _ccTracks.length > 0; 
       ccTracksList.enabled = hasCC; 
       ccTracksList.mouseEnabled = hasCC; 
       ccTracksList.selectedIndex = selectedIndex; 
   } 
   ```
