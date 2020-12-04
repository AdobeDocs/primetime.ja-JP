---
seo-title: Tomcatのインストール
title: Tomcatのインストール
uuid: f7663eda-ad18-4a6e-bb9f-01c74721b047
translation-type: tm+mt
source-git-commit: ed1430bdcb590a53fa69b324ef340ad636b2fa7c
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
