---
title: SWF Hash Calculator
description: SWF Hash Calculator
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '52'
ht-degree: 0%

---


# SWF Hash Calculator{#swf-hash-calculator}

SWF Hash Calculatorユーティリティは、ファイル内のSWFアプリケーションのダイジェストを計算しました。 ハッシャーを実行するには、次のコマンドを実行します。

```
Hasher.bat filename.swf
```

または次のコマンドを実行します。

```
java -jar libs/flashaccess-hasher.jar filename.swf
```

ユーティリティは次のメッセージを出力します。

```
SWF Hash: hash-of-swf
```

この値は、[!DNL flashaccess-tenant.xml]でSWFダイジェストを指定するために使用できます。
