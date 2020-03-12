---
seo-title: パスワードスクランブラ
title: パスワードスクランブラ
uuid: e488babc-cd50-41b9-acb8-490e8e42e8bc
translation-type: tm+mt
source-git-commit: 47b2ed65ff0ea4f54a210cf7627ed535782296b9

---


# パスワードスクランブラ {#password-scrambler}

Password Scramblerユーティリティは、パスワードを暗号化して、Adobe Access Serverで保護されたストリーミング設定ファイルに使用できるようにします。 スクランブラを実行するには、次のコマンドを実行します。

```
Scrambler.bat password 
```

または次のコマンドを実行します。

```
java -jar libs/flashaccess-scrambler.jar password  
```

ユーティリティは次のメッセージを出力します。

```
Encrypted password: scrambled-password 
```

flashaccess-global.xmlおよびflashaccess-tenant.xmlで指定されているすべてのパスワードは、暗号化する必要があります。

>[!NOTE]
>
>Adobe Access Server for Protected StreamingのPassword Scramblerユーティリティは、リファレンス実装ライセンスサーバーに付属のスクランブラと交換できません。

