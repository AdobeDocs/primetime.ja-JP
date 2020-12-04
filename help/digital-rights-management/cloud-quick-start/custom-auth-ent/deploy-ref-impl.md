---
seo-title: BEESリファレンスの実装のデプロイ
title: BEESリファレンスの実装のデプロイ
uuid: 5ee7b066-8ae8-48ba-a3f0-8cc14b19d5c5
translation-type: tm+mt
source-git-commit: 4f196bbd079edeb1a423afee6b4b7e249d380f40
workflow-type: tm+mt
source-wordcount: '53'
ht-degree: 0%

---


# BEESリファレンス実装を導入{#deploy-the-bees-reference-implementation}

1. Tomcatアプリケーションサーバーを設定します。 （Tomcatのマニュアルを参照）。
1. `[!DNL bees.war]`ファイルをTomcatの[!DNL webapps/]フォルダにコピーします。
1. `https://localhost:8080/bees`にリクエストを送信します。

   「BEES is operational」というメッセージが表示された場合は、デプロイメントは正常に完了しています。
1. サーバーでSSLを有効にします。
