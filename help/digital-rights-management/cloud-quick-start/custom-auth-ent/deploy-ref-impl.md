---
title: BEES リファレンス実装のデプロイ
description: BEES リファレンス実装のデプロイ
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '53'
ht-degree: 0%

---

# BEES リファレンス実装のデプロイ {#deploy-the-bees-reference-implementation}

1. Tomcat アプリケーションサーバーを設定します。 （ Tomcat のドキュメントを参照）。
1. をコピーします。 `[!DNL bees.war]` Tomcat の [!DNL webapps/] フォルダー。
1. にリクエストを送信 `https://localhost:8080/bees`.

   「BEES is operational」というメッセージが表示された場合は、デプロイメントが正常に完了しています。
1. サーバーで SSL を有効にします。
