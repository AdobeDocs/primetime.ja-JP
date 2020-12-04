---
description: 'null'
seo-description: 'null'
seo-title: Javaを使用したパスワードの準備
title: Javaを使用したパスワードの準備
uuid: 8a708d22-764f-4229-95ca-109482563432
translation-type: tm+mt
source-git-commit: 055989cbe3a187516f18816492aaea709cc80c81
workflow-type: tm+mt
source-wordcount: '24'
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

