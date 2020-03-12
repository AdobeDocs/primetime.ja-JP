---
seo-title: 認証UIの作成
title: 認証UIの作成
uuid: 4744bac0-c36e-4b0a-b3fb-d81c7f2e7617
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# 認証UIの作成 {#create-an-authentication-ui}

1. ユーザーの認証資格情報を取得するユーザーインターフェイスを作成します。

   次に、ユーザ資格情報を取得するためのシンプルなユーザインターフェイスのFlexの例を示します。 このオブジェクトは、2つのオブジェクトを含むパネルオ `TextInput` ブジェクトで構成され、各ユーザー名とパスワードの秘密鍵証明書に対して1つずつ割り当てられます。 このパネルには、メソッドを起動するボタンも含まれ `credentials()` ています。

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

1. ユーザーが `credentials()` 提供する認証値を処理する方法を記述します。

   このメ `credentials()` ソッドは、ユーザー名とパスワードの値をメソッドに渡すユーザー定義のメソッ `setDRMAuthenticationCredentials()` ドです。 値が渡されると、メソッドはオ `credentials()` ブジェクトの値をリセットし `TextInput` ます。

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

   このタイプのシンプルインターフェイスを実装する1つの方法は、パネルを新しい状態の一部として含めることです。 新しい状態は、オブジェクトがスローされたときのベース状 `DRMAuthenticateEvent` 態に基づきます。 次の例には、保護されたビデ `VideoDisplay` オファイルを指すsource属性を持つオブジェクトが含まれています。 この場合、メソッドは、 `credentials()` アプリケーションもベース状態に戻すように変更されます。 このメソッドは、ユーザーの資格情報を渡し、TextInputオブジェクトの値をリセットした後に実行されます。

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

