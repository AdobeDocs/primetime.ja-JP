---
title: Javaを使用したパスワードの準備
description: Javaを使用したパスワードの準備
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '22'
ht-degree: 0%

---


# Java{#prepare-passwords-using-java}を使用してパスワードを準備する

Javaで`ScrambleUtil.class`を実行：

1. `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl/scrambler/ refimpl/scrambler/`に移動
1. コマンドラインで次のように入力します。

   ```
   java -classpath [DRM SDK DVD]/SDK/adobe-flashaccess-sdk.jar;  
       com.adobe.flashaccess.refimpl.util.ScrambleUtil your_pfx_password
   ```

