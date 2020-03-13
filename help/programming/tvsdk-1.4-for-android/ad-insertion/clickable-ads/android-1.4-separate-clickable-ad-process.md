---
description: プレイヤーのUIロジックは、広告クリックを管理するプロセスとは別にする必要があります。 これを行う1つの方法は、1つのアクティビティに複数のフラグメントを実装することです。
seo-description: プレイヤーのUIロジックは、広告クリックを管理するプロセスとは別にする必要があります。 これを行う1つの方法は、1つのアクティビティに複数のフラグメントを実装することです。
seo-title: クリック可能な広告プロセスの分離
title: クリック可能な広告プロセスの分離
uuid: 00537191-8997-418d-add2-8e86d818c76e
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# クリック可能な広告プロセスの分離{#separate-the-clickable-ad-process}

プレイヤーのUIロジックは、広告クリックを管理するプロセスとは別にする必要があります。 これを行う1つの方法は、1つのアクティビティに複数のフラグメントを実装することです。

1. 1つのフラグメントを実装して、ビデオを含め `MediaPlayer` 、ビデオの再生を担当するフラグメントを含めます。

   このフラグメントは呼び出す必要があり `notifyClick`ます。

   ```java
   public class PlayerFragment extends SherlockFragment { 
       ... 
       public void notifyAdClick () { 
           _mediaPlayer.notifyClick(); 
       } 
       ... 
   } 
   ```

1. 別のフラグメントを実装して、クリック可能な広告を示すUI要素を表示し、そのUI要素を監視し、広告を含むフラグメントにユーザーのクリックを通知しま `MediaPlayer`す。

   このフラグメントは、フラグメント通信用のインターフェイスを宣言する必要があります。 このフラグメントは、onAttachライフサイクルメソッドの間にインターフェイス実装をキャプチャし、インターフェイスメソッドを呼び出してアクティビティと通信できます。

   ```java
   public class PlayerClickableAdFragment extends SherlockFragment { 
       private ViewGroup viewGroup; 
       private Button button; 
       OnAdUserInteraction callback; 
   
       @Override 
       public View onCreateView(LayoutInflater inflater,  
                                ViewGroup container, Bundle 
                                savedInstanceState) { 
   
           // the custom fragment is defined by a custom button 
           viewGroup =  
             (ViewGroup) inflater.inflate(R.layout.fragment_player_clickable_ad, container, false); 
           button = (Button) viewGroup.findViewById(R.id.clickButton); 
   
           // register a click listener to detect user interaction 
           button.setOnClickListener(new View.OnClickListener() { 
               @Override 
               public void onClick(View v) { 
                   // send the event back to the activity 
                   callback.onAdClick(); 
               } 
           }); 
   
           viewGroup.setVisibility(View.INVISIBLE); 
           return viewGroup; 
       } 
   
       public void hide() { 
           viewGroup.setVisibility(View.INVISIBLE); 
       } 
   
       public void show() { 
           viewGroup.setVisibility(View.VISIBLE);  
       } 
   
       @Override 
       public void onAttach(Activity activity) { 
           super.onAttach(activity); 
           // attaches the interface implementation 
           // if the container activity does not implement the methods  
           // from the interface an exception will be thrown 
           try { 
               callback = (OnAdUserInteraction) activity; 
           } catch (ClassCastException e) { 
               throw new ClassCastException(activity.toString() 
               + " must implement OnAdUserInteraction"); 
           }  
       } 
   
       // user defined interface that allows fragment communication 
       // must be implemented by the container activity 
       public interface OnAdUserInteraction { 
           public void onAdClick(); 
       } 
   } 
   ```

