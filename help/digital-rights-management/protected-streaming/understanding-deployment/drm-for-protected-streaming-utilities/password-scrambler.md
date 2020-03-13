---
description: Password Scramblerユーティリティは、保護されたストリーミング設定ファイル用のAdobe Primetime DRMサーバーのパスワードを暗号化します。
seo-description: Password Scramblerユーティリティは、保護されたストリーミング設定ファイル用のAdobe Primetime DRMサーバーのパスワードを暗号化します。
seo-title: パスワードスクランブラ
title: パスワードスクランブラ
uuid: 56df0f49-f3fd-464d-b4ba-25e1b497158a
translation-type: tm+mt
source-git-commit: 105dedcfe47a5f454a067e66a95827e638290742

---


# パスワードスクランブラ {#password-scrambler}

Password Scramblerユーティリティは、保護されたストリーミング設定ファイル用のAdobe Primetime DRMサーバーのパスワードを暗号化します。

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

とファイルで指定したすべてのパスワード [!DNL flashaccess-global.xml] は暗号 [!DNL flashaccess-tenant.xml] 化する必要があります。

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>Primetime DRM ServerのPassword Scramblerユーティリティ（Protected Streaming用）は、リファレンス実装ライセンスサーバに付属のスクランブラと交換できません。