---
description: 'null'
seo-description: 'null'
seo-title: Antを使用したパスワードの準備
title: Antを使用したパスワードの準備
uuid: 9419ab0d-b448-4881-9d26-35c00f0b13bc
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '42'
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

