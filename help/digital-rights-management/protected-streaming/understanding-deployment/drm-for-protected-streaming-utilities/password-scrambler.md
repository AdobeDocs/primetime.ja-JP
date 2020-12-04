---
description: Password Scramblerユーティリティは、保護されたストリーミング設定ファイル用のAdobe PrimetimeDRMサーバのパスワードを暗号化します。
seo-description: Password Scramblerユーティリティは、保護されたストリーミング設定ファイル用のAdobe PrimetimeDRMサーバのパスワードを暗号化します。
seo-title: パスワードスクランブラ
title: パスワードスクランブラ
uuid: 56df0f49-f3fd-464d-b4ba-25e1b497158a
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '112'
ht-degree: 0%

---


# パスワードスクランブラ{#password-scrambler}

Password Scramblerユーティリティは、保護されたストリーミング設定ファイル用のAdobe PrimetimeDRMサーバのパスワードを暗号化します。

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

次のメッセージが表示されます。

```
Encrypted password:  
<i class="+ topic ph hi-d="" i "="">
  scrambled-password 
</i class="+ topic>
```

[!DNL flashaccess-global.xml]ファイルと[!DNL flashaccess-tenant.xml]ファイルに指定したパスワードはすべて暗号化する必要があります。

>[!NOTE]
>
>Primetime DRM Server for Protected StreamingのPassword Scramblerユーティリティは、リファレンス実装ライセンスサーバーに付属のスクランブラと交換できません。