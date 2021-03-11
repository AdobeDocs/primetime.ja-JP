---
description: 保護されたストリーミング用にAdobe Access Serverを実行しているサーバーをアップグレードするには、アプリケーションサーバーにデプロイされているflashaccessserver.warファイルを、最新のAdobeアクセスに含まれているファイルに置き換えます。 上記の新しい設定オプションを使用する場合は、サーバーのflashaccess-tenant.xmlを更新します。 また、jsafe.dllまたはlibjsafe.soを最新のAdobeアクセスに含まれるバージョンに更新する必要があります。
title: 保護されたストリーミング用にAdobe Access Serverを実行する
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---


# 保護されたストリーミング用にAdobe Access Serverを実行する{#running-the-adobe-access-server-for-protected-streaming}

保護されたストリーミング用にAdobe Access Serverを実行しているサーバーをアップグレードするには、アプリケーションサーバーにデプロイされているflashaccessserver.warファイルを、最新のAdobeアクセスに含まれているファイルに置き換えます。 上記の新しい設定オプションを使用する場合は、サーバーのflashaccess-tenant.xmlを更新します。 また、jsafe.dllまたはlibjsafe.soを最新のAdobeアクセスに含まれるバージョンに更新する必要があります。

保護ストリーミング用Adobe Access Serverを実行する前に、Adobeは、ライセンスサーバに付属のユーティリティを使用して、設定ファイルが有効であることを確認することを推奨します。 詳しくは、「[構成バリデーター](../../aaxs-protected-streaming/aaxs-protected-streaming-utilities/configuration-validator.md)」を参照してください。

Tomcatとライセンスサーバーを開始するには、Tomcatのbinディレクトリから「catalina.bat開始」または「catalina.sh開始」を実行します。

サーバーの起動後、ブラウザーウィンドウで&#x200B;*https:// license-server-host:port/flashaccessserver/tenant-name/flashaccess/license/v1*&#x200B;を開いて、サーバーが正しく構成されていることを確認します。 テナント構成が正常に読み込まれた場合は、確認メッセージが表示されます。
