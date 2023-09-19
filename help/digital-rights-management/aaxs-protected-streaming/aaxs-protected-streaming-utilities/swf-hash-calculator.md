---
title: SWFハッシュ計算ツール
description: SWFハッシュ計算ツール
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '52'
ht-degree: 0%

---

# SWFハッシュ計算ツール{#swf-hash-calculator}

SWFHash Calculator ユーティリティは、ファイル内のSWFアプリケーションのダイジェストを計算しました。 ハッシャーを実行するには、次のコマンドを実行します。

```
Hasher.bat filename.swf
```

または次のコマンドを使用します。

```
java -jar libs/flashaccess-hasher.jar filename.swf
```

ユーティリティは次のメッセージを出力します。

```
SWF Hash: hash-of-swf
```

この値は、でSWFダイジェストを指定するために使用できます [!DNL flashaccess-tenant.xml].
