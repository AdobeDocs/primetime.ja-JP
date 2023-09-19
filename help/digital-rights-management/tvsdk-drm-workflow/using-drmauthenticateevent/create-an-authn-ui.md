---
title: 認証 UI の作成
description: 認証 UI の作成
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# 認証 UI の作成 {#create-an-authentication-ui}

1. ユーザーの認証資格情報を取得するためのユーザーインターフェイスを作成します。

   次に、Flexのユーザー資格情報を取得するためのシンプルなユーザーインターフェイスの例を示します。 これは、2 つの `TextInput` オブジェクト。ユーザー名とパスワードの資格情報ごとに 1 つずつ。 パネルには、 `credentials()` メソッド。

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

1. を書き込む `credentials()` メソッドを使用して、ユーザー指定の認証値を処理できます。

   The `credentials()` メソッドは、ユーザー名とパスワードの値を `setDRMAuthenticationCredentials()` メソッド。 値が渡されると、 `credentials()` メソッドは、 `TextInput` オブジェクト。

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

   このタイプのシンプルなインターフェイスを実装する 1 つの方法は、パネルを新しい状態の一部として含めることです。 新しい状態は、 `DRMAuthenticateEvent` オブジェクトがスローされます。 次の例には、 `VideoDisplay` 保護されたビデオファイルを指す source 属性を持つオブジェクト。 この場合、 `credentials()` メソッドを変更して、アプリケーションもベース状態に戻すようにします。 このメソッドは、ユーザーの資格情報を渡し、TextInput オブジェクトの値をリセットした後に実行します。

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
