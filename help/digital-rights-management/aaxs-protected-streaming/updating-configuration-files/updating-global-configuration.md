---
title: グローバル設定ファイルの更新
description: グローバル設定ファイルの更新
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '59'
ht-degree: 0%

---


# グローバル構成ファイルの更新{#updating-the-global-configuration-file}

[!DNL flashaccess-global.xml]内のHSMパスワードはいつでも変更でき、この変更は、次にサーバーが設定ファイルをリロードしたときに有効になります。 ただし、「Logging」要素と「Caching」要素に対する変更は再読み込みされません。これらの要素に変更を加えた場合は、サーバーを再起動する必要があります。
