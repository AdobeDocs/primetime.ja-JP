---
title: 認証UIの作成
description: 認証UIの作成
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---


# 認証UIの作成{#create-an-authentication-ui}

1. ユーザーの認証資格情報を取得するユーザーインターフェイスを作成します。

   以下は、Flexのユーザー資格情報を取得するためのシンプルなユーザーインターフェイスの例です。 これは2つの`TextInput`オブジェクトを含むパネルオブジェクトで構成され、各ユーザー名とパスワードの秘密鍵証明書に対して1つずつ割り当てられます。 このパネルには、`credentials()`メソッドを起動するボタンも含まれています。

   ```xml
   <mx:Panel x="236.5"  
             y="113"  
             width="325"  
             height="204"  
             layout="absolute"  
             title="Login">  
       <mx:TextInput x="110"  
                     y="46"  
                     id="uName"/>  
       <mx:TextInput x="110"  
                     y="76"  
                     id="pWord"  
                     displayAsPassword="true"/>  
       <mx:Text x="35"  
                y="48"  
                text="Username:"/>  
       <mx:Text x="35"  
                y="78"  
                text="Password:"/>  
       <mx:Button x="120"  
                  y="115"  
                  label="Login"  
                  click="credentials()"/>  
   </mx:Panel>  
   ```

1. `credentials()`メソッドを記述して、ユーザーが提供する認証値を処理します。

   `credentials()`メソッドは、ユーザー名とパスワードの値を`setDRMAuthenticationCredentials()`メソッドに渡すユーザー定義のメソッドです。 値が渡されると、`credentials()`メソッドは`TextInput`オブジェクトの値をリセットします。

   ```
   <mx:Script> 
       <![CDATA[ 
         public function credentials():void { 
             videoStream.setDRMAuthenticationCredentials(uName, pWord, "drm"); 
             uName.text = ""; 
             pWord.text = ""; 
   } ]]> 
   </mx:Script> 
   ```

   このタイプのシンプルインターフェイスを実装する1つの方法は、パネルを新しい状態の一部として含めることです。 新しい状態は、`DRMAuthenticateEvent`オブジェクトがスローされたときの基本状態に基づきます。 次の例には、保護されたビデオファイルを指すsource属性を持つ`VideoDisplay`オブジェクトが含まれています。 この場合、`credentials()`メソッドも変更され、アプリケーションもベース状態に戻ります。 このメソッドは、ユーザー資格情報を渡し、TextInputオブジェクトの値をリセットした後に実行します。

   ```xml
   <?xml version="1.0" encoding="utf-8"?> 
   <mx:WindowedApplication xmlns:mx="https://www.adobe.com/2006/mxml" 
       layout="absolute" 
       width="800" 
       height="500" 
       title="DRM FLV Player" 
       creationComplete="initApp()" > 
       <mx:states> 
           <mx:State name="LOGIN"> 
               <mx:AddChild position="lastChild"> 
                       <mx:Panel x="236.5"  
                                 y="113"  
                                 width="325"  
                                 height="204"  
                                 layout="absolute"  
                                 title="Login"> 
                       <mx:TextInput x="110"  
                                     y="46"  
                                     id="uName"/> 
                       <mx:TextInput x="110"  
                                     y="76"  
                                     id="pWord"  
                                     displayAsPassword="true"/> 
                       <mx:Text x="35"  
                                y="48"  
                                text="Username:"/> 
                       <mx:Text x="35"  
                                y="78"  
                                text="Password:"/> 
                       <mx:Button x="120"  
                                  y="115"  
                                  label="Login"  
                                  click="credentials()"/> 
                       <mx:Button x="193"  
                                  y="115"  
                                  label="Reset"  
                                  click="uName.text=''; 
               </mx:Panel> 
           </mx:AddChild> 
       </mx:State> 
   </mx:states> 
   pWord.text='';"/> 
   
   <mx:Script> 
       <![CDATA[ 
           import flash.events.DRMAuthenticateEvent; 
           private function initApp():void { 
               videoStream.addEventListener(DRMAuthenticateEvent.DRM_AUTHENTICATE, 
                                            drmAuthenticateEventHandler); 
           } 
           public function credentials():void { 
               videoStream.setDRMAuthenticationCredentials(uName, pWord, "drm"); 
               uName.text = ""; 
               pWord.text = ""; 
               currentState=''; 
           } 
           private function drmAuthenticateEventHandler(event:DRMAuthenticateEvent):void { 
               currentState='LOGIN'; 
           } 
       ]]> 
   </mx:Script> 
   <mx:VideoDisplay id="video"  
                    x="50"  
                    y="25"  
                    width="700"  
                    height="350" 
                    autoPlay="true" 
                    bufferTime="10.0" 
                    source="https://www.example.com/flv/Video.flv" /> 
   </mx:WindowedApplication> 
   ```

