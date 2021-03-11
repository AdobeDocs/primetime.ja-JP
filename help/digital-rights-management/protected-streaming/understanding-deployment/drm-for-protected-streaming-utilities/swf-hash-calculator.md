---
description: SWF Hash Calculatorユーティリティは、ファイル内のSWFアプリケーションのダイジェストを計算します。
title: SWFハッシュ計算ツール
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '65'
ht-degree: 0%

---


# SWFハッシュ計算{#swf-hash-calculator}

SWF Hash Calculatorユーティリティは、ファイル内のSWFアプリケーションのダイジェストを計算します。

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

次のメッセージが表示されます。

```
SWF Hash: 
<i class="+ topic ph hi-d="" i "="">
  hash-of-swf
</i class="+ topic>
```

この値を使用して、[!DNL flashaccess-tenant.xml]でSWFダイジェストを指定できます。
