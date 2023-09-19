---
description: プレーヤーの UI ロジックは、広告クリックを管理するプロセスとは別にする必要があります。 これをおこなう 1 つの方法は、1 つのアクティビティに複数のフラグメントを実装することです。
title: クリック可能な広告プロセスの分離
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---

# クリック可能な広告プロセスの分離{#separate-the-clickable-ad-process}

プレーヤーの UI ロジックは、広告クリックを管理するプロセスとは別にする必要があります。 これをおこなう 1 つの方法は、1 つのアクティビティに複数のフラグメントを実装することです。

1. フラグメントを 1 つ実装して、 `MediaPlayer` とは、ビデオの再生を担当します。

   このフラグメントはを呼び出す必要があります `notifyClick`.

   ```java
   public class PlayerFragment extends SherlockFragment { 
       ... 
       public void notifyAdClick () { 
           _mediaPlayer.notifyClick(); 
       } 
       ... 
   } 
   ```

1. 別のフラグメントを実装して、広告がクリック可能であることを示す UI 要素を表示し、その UI 要素を監視し、 `MediaPlayer`.

   このフラグメントは、フラグメント通信用のインターフェイスを宣言する必要があります。 フラグメントは、onAttach ライフサイクルメソッドの間にインターフェイス実装をキャプチャし、インターフェイスメソッドを呼び出してアクティビティと通信できます。

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
