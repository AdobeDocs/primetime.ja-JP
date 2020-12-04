---
seo-title: パスワードスクランブラ
title: パスワードスクランブラ
uuid: e488babc-cd50-41b9-acb8-490e8e42e8bc
translation-type: tm+mt
source-git-commit: 47b2ed65ff0ea4f54a210cf7627ed535782296b9
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 0%

---


# パスワードスクランブラ{#password-scrambler}

Password Scramblerユーティリティは、パスワードを暗号化して、保護ストリーミング設定ファイル用のAdobe Access Serverで使用できるようにします。 スクランブラを実行するには、次のコマンドを実行します。

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
>保護ストリーミング用Adobe Access ServerのPassword Scramblerユーティリティは、リファレンス実装ライセンスサーバに付属のスクランブラと交換できません。

