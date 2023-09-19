---
title: パスワードの暗号化
description: パスワードの暗号化
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '54'
ht-degree: 0%

---

# パスワードの暗号化{#encrypt-passwords}

プロパティファイルには、プレーンテキストとして入力しないいくつかのパスワード値が含まれています。 次のコマンドを使用して、これらの値を暗号化します。

`java -jar adobe-flashaccess-i15n-setup.jar password`

このコマンドは、暗号化されたパスワードを出力し、プロパティファイルで使用します。

>[!NOTE]
>これは、ライセンスサーバのパスワードを暗号化するために使用されるユーティリティではありません。
