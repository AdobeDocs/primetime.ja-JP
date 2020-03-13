---
seo-title: WARファイルのデプロイ
title: WARファイルのデプロイ
uuid: 435a6a6e-c981-46fb-bca9-7f5f34eecd6a
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# WARファイルのデプロイ{#deploy-the-war-files}

1. WARファイルをTomcatのディレクトリにコピーし [!DNL webapps] ます。

   * 個別化サーバー： [!DNL flashaccess.war]
   * Key Generation Server: [!DNL flashaccess-kgs.war]

1. アドビが提供 [!DNL ROOT] するパッケージからディレクトリにフォルダーをコピー [!DNL webapps] します。

   また、個別化サーバーがファイルをホストする必要が [!DNL crossdomain.xml] あります。 (フォルダ [!DNL ROOT] ーにはファイルが含ま [!DNL crossdomain.xml] れます。は、す [!DNL ROOT] べて大文字にする必要があります)。キー生成サーバーでは、このファイルは必要ありません。

