---
description: これは、クローズドキャプショントラックを選択するためのボタンの作成方法の例です。
seo-description: これは、クローズドキャプショントラックを選択するためのボタンの作成方法の例です。
seo-title: 例ユーザーがキャプショントラックを変更できるようにする
title: 例ユーザーがキャプショントラックを変更できるようにする
uuid: 4b69d569-0d6e-4388-9fe3-488e2a4d762d
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# 例：キャプショントラックの変更を許可する{#example-allow-users-to-change-the-caption-track}

これは、クローズドキャプショントラックを選択するためのボタンの作成方法の例です。

1. クローズドキャプショントラックを変更する簡単なボタンを作成します。

   ```xml
      <Button 
     android:id="@+id/selectCC" 
     android:layout_width="wrap_content" 
     android:layout_height="wrap_content" 
     android:layout_alignParentBottom="true" 
     android:layout_alignParentRight="true" 
     android:layout_marginRight="10dp" 
     android:onClick="selectClosedCaptioningClick" 
     android:text="CC" /> 
   ```

1. 使用可能なクローズドキャプショントラックのリストを文字列配列に変換します。 アクティビティ（TVSDKがデータを検出したチャネル）を持つクローズドキャプショントラックは、それに応じてマークされます。

   ```java
   /** 
   * Converts the closed captions tracks to a string array. 
   * 
   * @return array of CC tracks 
   */ 
   private String[] getCCsAsArray() { 
       List<String> closedCaptionsTracksAsStrings = new ArrayList<String>(); 
       MediaPlayerItem currentItem = mediaPlayer.getCurrentItem(); 
       if (currentItem != null) { 
           List<ClosedCaptionsTrack> closedCaptionsTracks = 
             currentItem.getClosedCaptionsTracks(); 
           Iterator<ClosedCaptionsTrack> iterator = closedCaptionsTracks.iterator(); 
           while (iterator.hasNext()) { 
               ClosedCaptionsTrack closedCaptionsTrack = iterator.next(); 
               String isActive = closedCaptionsTrack.isActive() ? " (" + getString(R.string.active)+ ")" : ""; 
               closedCaptionsTracksAsStrings.add(closedCaptionsTrack.getName() + isActive); 
           } 
       } 
       return closedCaptionsTracksAsStrings.toArray(new 
       String[closedCaptionsTracksAsStrings.size()]); 
   } 
   ```

1. ユーザーがボタンをクリックすると、すべてのデフォルトのCCトラックを一覧表示するダイアログが表示されます。

   ```java
      public void selectClosedCaptioningClick(View view) { 
       Log.i(LOG_TAG + "#selectClosedCaptions", "Displaying closed captions chooser dialog."); 
       final String items[] = getCCsAsArray(); 
       final AlertDialog.Builder ab = new AlertDialog.Builder(this); 
       ab.setTitle(R.string.PlayerControlCCDialogTitle); 
       ab.setSingleChoiceItems(items, selectedClosedCaptionsIndex, new DialogInterface.OnClickListener() { 
           public void onClick(DialogInterface dialog, int whichButton) { 
               // Select the new closed captioning track. 
               MediaPlayerItem currentItem = mediaPlayer.getCurrentItem(); 
               ClosedCaptionsTrack desiredClosedCaptionsTrack = currentItem.getClosedCaptionsTracks().get(whichButton); 
               boolean result = currentItem.selectClosedCaptionsTrack(desiredClosedCaptionsTrack); 
               if (result) { 
                   selectedClosedCaptionsIndex = whichButton; 
               } 
               // Dismiss dialog. 
               dialog.cancel(); 
           } 
       }).setNegativeButton(R.string.PlayerControlCCDialogCancel, new DialogInterface.OnClickListener() { 
           public void onClick(DialogInterface dialog, int whichButton) { 
           // Just cancel the dialog. 
           } 
       }); 
       ab.show(); 
   } 
   ```

