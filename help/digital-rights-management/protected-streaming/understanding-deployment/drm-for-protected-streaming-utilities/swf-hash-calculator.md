---
description: SWF・ハッシュ計算ユーティリティは、ファイル内のSWF・アプリケーションのダイジェストを計算します。
title: SWFハッシュ計算ツール
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '65'
ht-degree: 0%

---

# SWFハッシュ計算ツール{#swf-hash-calculator}

SWF・ハッシュ計算ユーティリティは、ファイル内のSWF・アプリケーションのダイジェストを計算します。

ハッシャーを実行するには、次のように入力します。

```
Hasher.bat 
<i class="+ topic ph hi-d="" i "="">
  filename.swf
</i class="+ topic>
```

または

```
java -jar libs/flashaccess-hasher.jar 
<i class="+ topic ph hi-d="" i "="">
  filename.swf
</i class="+ topic>
```

ユーティリティに次のメッセージが表示されます。

```
SWF Hash: 
<i class="+ topic ph hi-d="" i "="">
  hash-of-swf
</i class="+ topic>
```

この値を使用して、でSWFダイジェストを指定できます。 [!DNL flashaccess-tenant.xml].
