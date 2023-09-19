---
description: 保護されたストリーミング用にAdobe Access Serverを実行しているサーバーをアップグレードするには、アプリケーションサーバーにデプロイされている flashaccessserver.war ファイルを、最新のAdobeアクセスに含まれているファイルに置き換えます。 上記の新しい設定オプションを使用する場合は、サーバーの flashaccess-tenant.xml を更新します。 また、jsafe.dll または libjsafe.so を、最新のバージョンアクセスに含まれるAdobeに更新する必要があります。
title: 保護されたストリーミング用のAdobe Access Serverの実行
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# 保護されたストリーミング用のAdobe Access Serverの実行{#running-the-adobe-access-server-for-protected-streaming}

保護されたストリーミング用にAdobe Access Serverを実行しているサーバーをアップグレードするには、アプリケーションサーバーにデプロイされている flashaccessserver.war ファイルを、最新のAdobeアクセスに含まれているファイルに置き換えます。 上記の新しい設定オプションを使用する場合は、サーバーの flashaccess-tenant.xml を更新します。 また、jsafe.dll または libjsafe.so を、最新のバージョンアクセスに含まれるAdobeに更新する必要があります。

Adobe Access Server for Protected Streaming を実行する前に、Adobeは、ライセンスサーバーに付属のユーティリティを使用して、設定ファイルが有効であることを確認することをお勧めします。 詳しくは、[設定バリデーター](../../aaxs-protected-streaming/aaxs-protected-streaming-utilities/configuration-validator.md)&quot;.

Tomcat とライセンスサーバーを起動するには、Tomcat の bin ディレクトリから「catalina.bat start」または「catalina.sh start」を実行します。

サーバーが起動したら、 *https:// license-server-host:port/flashaccessserver/tenant-name/flashaccess/license/v1* をクリックします。 テナント設定が正常に読み込まれた場合は、確認メッセージが表示されます。
