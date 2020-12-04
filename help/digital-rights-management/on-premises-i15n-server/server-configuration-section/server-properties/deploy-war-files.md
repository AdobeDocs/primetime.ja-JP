---
seo-title: WARファイルのデプロイ
title: WARファイルのデプロイ
uuid: 435a6a6e-c981-46fb-bca9-7f5f34eecd6a
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '64'
ht-degree: 0%

---


# WARファイルのデプロイ{#deploy-the-war-files}

1. WARファイルをTomcatの[!DNL webapps]ディレクトリにコピーします。

   * 個別化サーバー：[!DNL flashaccess.war]
   * Key Generation Server:[!DNL flashaccess-kgs.war]

1. Adobeが提供するパッケージの[!DNL ROOT]フォルダーを[!DNL webapps]ディレクトリにコピーします。

   個別化サーバーは、[!DNL crossdomain.xml]ファイルもホストする必要があります。 ([!DNL ROOT]フォルダーには[!DNL crossdomain.xml]ファイルが含まれています。[!DNL ROOT]はすべて大文字にする必要があります。) キー生成サーバーでは、このファイルは必要ありません。

