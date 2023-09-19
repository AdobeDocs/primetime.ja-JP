---
title: Java を使用してパスワードを準備する
description: Java を使用してパスワードを準備する
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '22'
ht-degree: 0%

---

# Java を使用してパスワードを準備する{#prepare-passwords-using-java}

を実行します。 `ScrambleUtil.class` Java の場合：

1. に移動します。 `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl/scrambler/ refimpl/scrambler/`
1. コマンドラインで、次のように入力します。

   ```
   java -classpath [DRM SDK DVD]/SDK/adobe-flashaccess-sdk.jar;  
       com.adobe.flashaccess.refimpl.util.ScrambleUtil your_pfx_password
   ```
