---
seo-title: SWF Hash Calculator
title: SWF Hash Calculator
uuid: c1823208-92d9-47c5-b550-f9cc370b543d
translation-type: tm+mt
source-git-commit: 47b2ed65ff0ea4f54a210cf7627ed535782296b9

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

この値は、でSWFダイジェストを指定するために使用できま [!DNL flashaccess-tenant.xml]す。
