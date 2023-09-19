---
title: グローバル設定ファイルの更新
description: グローバル設定ファイルの更新
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '59'
ht-degree: 0%

---

# グローバル設定ファイルの更新{#updating-the-global-configuration-file}

の HSM パスワード [!DNL flashaccess-global.xml] はいつでも変更でき、サーバーが次回設定ファイルをリロードしたときに変更が有効になります。 ただし、「Logging」要素と「Caching」要素に対する変更は再読み込みされません。これらの要素に対する変更には、サーバーの再起動が必要です。
