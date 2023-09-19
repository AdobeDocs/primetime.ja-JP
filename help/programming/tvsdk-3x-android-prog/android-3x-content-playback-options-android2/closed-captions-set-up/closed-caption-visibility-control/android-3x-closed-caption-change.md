---
description: この手順は、クローズドキャプショントラックを選択するためのボタンの作成方法の例です。
title: ユーザーがキャプショントラックを変更することを許可
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 0%

---

# ユーザーがキャプショントラックを変更することを許可 {#allow-users-to-change-the-caption-track}

この手順は、クローズドキャプショントラックを選択するためのボタンの作成方法の例です。

1. クローズドキャプショントラックを変更するためのボタンを作成します。

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

1. 使用可能なクローズドキャプショントラックのリストを文字列配列に変換します。

   TVSDK がデータを検出したチャネルであるアクティビティを持つクローズドキャプショントラックは、それに応じてマークされます。

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
               String isActive = closedCaptionsTrack.isActive() ? " (" +  
                 getString(R.string.active)+ ")" : ""; 
               closedCaptionsTracksAsStrings.add(closedCaptionsTrack.getName() +  
                 isActive); 
           } 
       } 
       return closedCaptionsTracksAsStrings. 
         toArray(new String[closedCaptionsTracksAsStrings.size()]); 
   } 
   ```

1. ユーザーがボタンをクリックすると、デフォルトのクローズドキャプショントラックをすべてリストするダイアログが表示されます。

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
               ClosedCaptionsTrack desiredClosedCaptionsTrack =  
                 currentItem.getClosedCaptionsTracks().get(whichButton); 
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
