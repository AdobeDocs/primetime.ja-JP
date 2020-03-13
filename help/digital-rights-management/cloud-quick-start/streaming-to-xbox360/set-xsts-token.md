---
description: 'null'
seo-description: 'null'
seo-title: プレイヤーにXSTSトークンを設定する
title: プレイヤーにXSTSトークンを設定する
uuid: 8995e029-deee-4e23-9cda-a50de8c4f2c0
translation-type: tm+mt
source-git-commit: b7f52b71bde1d7bf59ef51d4f6f90dfaa07e347b

---


# プレイヤーにXSTSトークンを設定する{#set-the-xsts-token-in-your-player}

Xbox360では、イベントに応じてトークンを非同期で設定し `MediaPlayer.RequestKeyAttribute` ます。

XSTSトークンを設定します。

ソフトウェアにバンドルされているサンプルアプリでは、XSTSトークンをプレーヤーに設定する方法を示しています。 以下に、サンプルプレーヤーからの関連コードスニペットを示します。

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

