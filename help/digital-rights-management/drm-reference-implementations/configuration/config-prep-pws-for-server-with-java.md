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


# Javaを使用したパスワードの準備{#prepare-passwords-using-java}

Javaでの実行 `ScrambleUtil.class` :

1. 移動先 `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl/scrambler/ refimpl/scrambler/`
1. コマンドラインで次のように入力します。

   ```
   java -classpath [DRM SDK DVD]/SDK/adobe-flashaccess-sdk.jar;  
       com.adobe.flashaccess.refimpl.util.ScrambleUtil your_pfx_password
   ```

