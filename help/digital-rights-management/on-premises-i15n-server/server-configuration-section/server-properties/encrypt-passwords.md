---
title: パスワードの暗号化
description: パスワードの暗号化
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '54'
ht-degree: 0%

---


# パスワードを暗号化{#encrypt-passwords}

プロパティファイルには、プレーンテキストとして入力しないパスワード値がいくつか含まれています。 次のコマンドを使用して、これらの値を暗号化します。

`java -jar adobe-flashaccess-i15n-setup.jar password`

このコマンドは、暗号化されたパスワードを出力し、そのパスワードをプロパティファイルで使用します。

>[!NOTE]
>このユーティリティは、License Serverのパスワードを暗号化するために使用されるものではありません。

