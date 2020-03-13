---
description: SWF Hash Calculatorユーティリティは、ファイル内のSWFアプリケーションのダイジェストを計算します。
seo-description: SWF Hash Calculatorユーティリティは、ファイル内のSWFアプリケーションのダイジェストを計算します。
seo-title: SWFハッシュ計算ツール
title: SWFハッシュ計算ツール
uuid: 0cf972c1-4717-4d78-a594-b27178ece512
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# SWFハッシュ計算ツール{#swf-hash-calculator}

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

この値を使用して、でSWFダイジェストを指定できま [!DNL flashaccess-tenant.xml]す。
