---
seo-title: Tomcatのインストール
title: Tomcatのインストール
uuid: f7663eda-ad18-4a6e-bb9f-01c74721b047
translation-type: tm+mt
source-git-commit: ed1430bdcb590a53fa69b324ef340ad636b2fa7c

---


# Tomcatのインストール {#install-tomcat}

両方のサーバーにTomcatをインストールする必要があります。
1. インストールDVDの[!DNL \Third Party\Tomcat\6.0.18\]ディレクトリからTomcatをインストールします。

   >[!NOTE]
   >
   >パス内にスペースがない場所にTomcatがインストールされていることを確認します。 入力はできますが、 `C:\Program Files\Tomcat`入力はできませ `C:\Tomcat\`ん。

1. Tomcatを起動するには、と入力しま `TomcatInstallDir>\bin\catalina.bat run`す。
1. インストールを確認するには、と入力してTomcatのランディングページに移動しま `https://<Hostname>:8080/`す。
1. ファイルを作 `crossdomain.xml` 成し、そのファイルをディレクトリに配置 `<TomcatInstallDir>\webapps\ROOT\` します。

   ディレクトリからファイルをコピーすることもで `https://drmtest2.adobe.com/crossdomain.xml` きます。
