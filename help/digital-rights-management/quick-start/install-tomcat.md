---
title: Tomcatのインストール
description: Tomcatのインストール
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 0%

---


# Tomcat {#install-tomcat}のインストール

両方のサーバにTomcatをインストールする必要があります。
1. インストールDVDの [!DNL \Third Party\Tomcat\6.0.18\] ディレクトリからTomcatをインストールします。

   >[!NOTE]
   >
   >パスにスペースがない場所にTomcatがインストールされていることを確認します。 `C:\Program Files\Tomcat`と入力できますが、`C:\Tomcat\`は入力できません。

1. Tomcatを開始するには、`TomcatInstallDir>\bin\catalina.bat run`と入力します。
1. インストールを確認するには、`https://<Hostname>:8080/`と入力してTomcatランディングページに移動します。
1. `crossdomain.xml`ファイルを作成し、`<TomcatInstallDir>\webapps\ROOT\`ディレクトリに配置します。

   `https://drmtest2.adobe.com/crossdomain.xml`ディレクトリからファイルをコピーすることもできます。
