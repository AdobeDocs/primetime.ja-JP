---
description: Password Scrambler ユーティリティは、保護されたストリーミング設定ファイル用のAdobe Primetime DRM サーバーのパスワードを暗号化します。
title: パスワードスクランブラ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---

# パスワードスクランブラ {#password-scrambler}

Password Scrambler ユーティリティは、保護されたストリーミング設定ファイル用のAdobe Primetime DRM サーバーのパスワードを暗号化します。

スクランブラを実行するには、次のように入力します。

```
Scrambler.bat  
<i class="+ topic ph hi-d="" i "="">
  password 
</i class="+ topic>
```

または

```
java -jar libs/flashaccess-scrambler.jar  
<i class="+ topic ph hi-d="" i "="">
  password  
</i class="+ topic>
```

ユーティリティに次のメッセージが表示されます。

```
Encrypted password:  
<i class="+ topic ph hi-d="" i "="">
  scrambled-password 
</i class="+ topic>
```

すべてのパスワードを [!DNL flashaccess-global.xml] および [!DNL flashaccess-tenant.xml] ファイルは暗号化する必要があります。

>[!NOTE]
>
>Primetime DRM Server for Protected Streaming の Password Scrambler ユーティリティは、Reference Implementation License Server に付属の Scrambler と交換できません。
