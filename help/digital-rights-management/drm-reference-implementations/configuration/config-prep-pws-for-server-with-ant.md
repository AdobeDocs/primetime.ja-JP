---
title: Antを使用したパスワードの準備
description: Antを使用したパスワードの準備
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '40'
ht-degree: 0%

---


# Ant{#prepare-passwords-using-ant}を使用してパスワードを準備する

Antを使用してパスワードを暗号化します。

1. `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl/`に移動
1. [!DNL build-refimpl.xml]の`sdkdir`プロパティを設定して、Primetime DRM Java SDKを含むディレクトリを指すようにします。
1. 次のコマンドを実行します。

   ```
   ant -f build-refimpl.xml
   ```

