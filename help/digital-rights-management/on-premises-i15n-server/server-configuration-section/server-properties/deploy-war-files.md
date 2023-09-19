---
title: WAR ファイルのデプロイ
description: WAR ファイルのデプロイ
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '64'
ht-degree: 0%

---

# WAR ファイルのデプロイ{#deploy-the-war-files}

1. WAR ファイルを Tomcat の [!DNL webapps] ディレクトリ。

   * 個別化サーバー： [!DNL flashaccess.war]
   * キー生成サーバー： [!DNL flashaccess-kgs.war]

1. をコピーします。 [!DNL ROOT] フォルダーで指定されたパッケージからAdobeー [!DNL webapps] ディレクトリ。

   また、個別化サーバーが [!DNL crossdomain.xml] ファイル。 ( [!DNL ROOT] フォルダーに [!DNL crossdomain.xml] ファイル； [!DNL ROOT] はすべて大文字にする必要があります )。 Key Generation サーバーでは、このファイルは必要ありません。
