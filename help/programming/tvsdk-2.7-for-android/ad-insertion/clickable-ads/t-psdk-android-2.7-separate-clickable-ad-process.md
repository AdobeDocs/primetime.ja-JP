---
description: プレイヤーのUIロジックは、広告クリックを管理するプロセスと分離する必要があります。 これを行う1つの方法は、1つのアクティビティに対して複数のフラグメントを実装することです。
title: クリック可能な広告プロセスの分離
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---


# クリック可能な広告プロセス{#separate-the-clickable-ad-process}を分離

プレイヤーのUIロジックは、広告クリックを管理するプロセスと分離する必要があります。 これを行う1つの方法は、1つのアクティビティに対して複数のフラグメントを実装することです。

1. 1つのフラグメントを実装して`MediaPlayer`を含めます。

   このフラグメントは`notifyClick()`を呼び出す必要があり、ビデオ再生を担当します。

   ```java
   public class PlayerFragment extends SherlockFragment { 
       ... 
       public void notifyAdClick () { 
           _mediaPlayer.notifyClick(); 
       } 
       ... 
   } 
   ```

1. 別のフラグメントを実装して、クリック可能な広告を示すUI要素を表示し、そのUI要素を監視し、`MediaPlayer`を含むフラグメントにユーザーのクリックを伝えます。

   このフラグメントは、フラグメント通信用のインターフェイスを宣言する必要があります。 このフラグメントは、`onAttach()`ライフサイクルメソッドの間にインターフェイス実装をキャプチャし、インターフェイスメソッドを呼び出してアクティビティと通信できます。

   ```java
   public class PlayerClickableAdFragment extends SherlockFragment { 
       private ViewGroup viewGroup; 
       private Button button; 
       OnAdUserInteraction callback; 
       @Override 
       public View onCreateView(LayoutInflater inflater,  
                                ViewGroup container,  
                                Bundle savedInstanceState) { 
           // the custom fragment is defined by a custom button 
           viewGroup = (ViewGroup) inflater.inflate(R.layout.fragment_player_clickable_ad,  
                                                    container, false); 
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

