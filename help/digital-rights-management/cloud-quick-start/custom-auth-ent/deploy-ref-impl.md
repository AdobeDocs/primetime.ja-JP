---
title: BEESリファレンスの実装のデプロイ
description: BEESリファレンスの実装のデプロイ
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
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
