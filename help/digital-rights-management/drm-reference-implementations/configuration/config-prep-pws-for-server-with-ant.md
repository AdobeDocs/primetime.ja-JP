---
title: Ant を使用してパスワードを準備する
description: Ant を使用してパスワードを準備する
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '40'
ht-degree: 0%

---

# Ant を使用してパスワードを準備する{#prepare-passwords-using-ant}

Ant を使用してパスワードを暗号化します。

1. に移動します。 `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl/`
1. を設定します。 `sdkdir` プロパティ： [!DNL build-refimpl.xml] をクリックして、Primetime DRM Java SDK が含まれるディレクトリを指します。
1. 次のコマンドを実行します。

   ```
   ant -f build-refimpl.xml
   ```
