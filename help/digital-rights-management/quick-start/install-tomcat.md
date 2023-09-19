---
title: Tomcat のインストール
description: Tomcat のインストール
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 0%

---

# Tomcat のインストール {#install-tomcat}

両方のサーバーに Tomcat をインストールする必要があります。
1. から Tomcat をインストールします。 [!DNL \Third Party\Tomcat\6.0.18\] インストール DVD のディレクトリ。

   >[!NOTE]
   >
   >パスにスペースが含まれていない場所に Tomcat がインストールされていることを確認します。 次の項目を入力できます。 `C:\Program Files\Tomcat`ではなく、 `C:\Tomcat\`.

1. Tomcat を起動するには、次のように入力します。 `TomcatInstallDir>\bin\catalina.bat run`.
1. インストールを検証するには、次を入力して Tomcat のランディングページに移動します。 `https://<Hostname>:8080/`.
1. の作成 `crossdomain.xml` ファイルを開き、 `<TomcatInstallDir>\webapps\ROOT\` ディレクトリ。

   また、 `https://drmtest2.adobe.com/crossdomain.xml` ディレクトリ。
