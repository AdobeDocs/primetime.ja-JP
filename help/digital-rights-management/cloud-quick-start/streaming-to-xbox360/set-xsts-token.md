---
title: プレイヤーにXSTSトークンを設定する
description: プレイヤーにXSTSトークンを設定する
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '64'
ht-degree: 0%

---


# プレイヤーにXSTSトークンを設定{#set-the-xsts-token-in-your-player}

Xbox360では、`MediaPlayer.RequestKeyAttribute`イベントに応じてトークンを非同期に設定します。

XSTSトークンを設定します。

ソフトウェアにバンドルされているサンプルアプリでは、プレイヤーにXSTSトークンを設定する方法を示しています。 サンプルプレーヤーからの関連コードスニペットを次に示します。

```
   MediaPlayer mMediaPlayer;  
 
mMediaPlayer.RequestKeyAttribute += Player_RequestKeyAttribute;  
 
private void Player_RequestKeyAttribute(object sender, RequestKeyAttributeEventArgs args) {  
    string token = "";  
    // XBOX XSTS Token...  
    KeyAttribute keyAttribute = new KeyAttribute(System.Text.Encoding.UTF8.GetBytes(token), null);  
    mMediaPlayer.SetKeyAttribute(args.RequestIdentifier, keyAttribute);  
} 
```

