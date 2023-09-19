---
title: パスワードスクランブラ
description: パスワードスクランブラ
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 0%

---

# パスワードスクランブラ {#password-scrambler}

Password Scrambler ユーティリティは、保護されたストリーミング設定ファイル用のAdobe Access Serverで使用できるように、パスワードを暗号化します。 スクランブラを実行するには、次のコマンドを実行します。

```
Scrambler.bat password 
```

または次のコマンドを使用します。

```
java -jar libs/flashaccess-scrambler.jar password  
```

ユーティリティは次のメッセージを出力します。

```
Encrypted password: scrambled-password 
```

flashaccess-global.xml および flashaccess-tenant.xml で指定するすべてのパスワードは、暗号化する必要があります。

>[!NOTE]
>
>Adobe Access Server for Protected Streaming の Password Scrambler ユーティリティは、Reference Implementation License Server に付属するスクランブラと交換できません。
