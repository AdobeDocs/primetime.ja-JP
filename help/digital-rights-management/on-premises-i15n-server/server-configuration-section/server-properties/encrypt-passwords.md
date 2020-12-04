---
seo-title: パスワードの暗号化
title: パスワードの暗号化
uuid: 94dc7fe9-fe40-4779-912a-d84b58e4ee36
translation-type: tm+mt
source-git-commit: 1547eb3dd220fafc08df923f40504736c16a866c
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

