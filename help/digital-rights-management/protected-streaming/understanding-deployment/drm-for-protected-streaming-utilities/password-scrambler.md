---
description: Password Scramblerユーティリティは、保護されたストリーミング設定ファイル用のAdobe PrimetimeDRMサーバのパスワードを暗号化します。
title: パスワードスクランブラ
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '92'
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