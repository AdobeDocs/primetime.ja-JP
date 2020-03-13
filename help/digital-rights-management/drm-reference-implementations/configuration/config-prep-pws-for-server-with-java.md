---
description: 'null'
seo-description: 'null'
seo-title: Javaを使用したパスワードの準備
title: Javaを使用したパスワードの準備
uuid: 8a708d22-764f-4229-95ca-109482563432
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Javaを使用したパスワードの準備{#prepare-passwords-using-java}

Javaを使用し `ScrambleUtil.class` て実行：

1. 移動先 `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl/scrambler/ refimpl/scrambler/`
1. コマンドラインで、次のように入力します。

   ```
   java -classpath < 
   
<i>[DRM SDK DVD]/SDK/adobe-flashaccess-sdk.jar</i>>;\
com.adobe.flashaccess.refimpl.util.ScrambleUtil your_pfx_password

```


