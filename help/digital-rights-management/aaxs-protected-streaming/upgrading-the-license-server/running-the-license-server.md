---
description: Adobe Access Serverを実行しているサーバーを保護ストリーミング用にアップグレードするには、アプリケーションサーバーにデプロイされているflashaccessserver.warファイルを、最新のAdobe Accessに含まれているファイルに置き換えます。 上記の新しい設定オプションを使用する場合は、サーバーのflashaccess-tenant.xmlを更新します。 また、jsafe.dllまたはlibjsafe.soを最新のAdobe Accessに含まれているバージョンに更新する必要があります。
seo-description: Adobe Access Serverを実行しているサーバーを保護ストリーミング用にアップグレードするには、アプリケーションサーバーにデプロイされているflashaccessserver.warファイルを、最新のAdobe Accessに含まれているファイルに置き換えます。 上記の新しい設定オプションを使用する場合は、サーバーのflashaccess-tenant.xmlを更新します。 また、jsafe.dllまたはlibjsafe.soを最新のAdobe Accessに含まれているバージョンに更新する必要があります。
seo-title: 保護されたストリーミング用のAdobe Access Serverの実行
title: 保護されたストリーミング用のAdobe Access Serverの実行
uuid: 3819500d-ad2f-49eb-8aa4-e50a55461608
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# 保護されたストリーミング用のAdobe Access Serverの実行{#running-the-adobe-access-server-for-protected-streaming}

Adobe Access Serverを実行しているサーバーを保護ストリーミング用にアップグレードするには、アプリケーションサーバーにデプロイされているflashaccessserver.warファイルを、最新のAdobe Accessに含まれているファイルに置き換えます。 上記の新しい設定オプションを使用する場合は、サーバーのflashaccess-tenant.xmlを更新します。 また、jsafe.dllまたはlibjsafe.soを最新のAdobe Accessに含まれているバージョンに更新する必要があります。

Adobe Access Server for Protected Streamingを実行する前に、ライセンスサーバーに付属のユーティリティを使用して、設定ファイルが有効であることを確認することをお勧めします。 詳しくは、「設定バリデータ[ー](../../aaxs-protected-streaming/aaxs-protected-streaming-utilities/configuration-validator.md)」を参照してください。

Tomcatとライセンスサーバーを起動するには、Tomcatのbinディレクトリから&quot;catalina.bat start&quot;または&quot;catalina.sh start&quot;を実行します。

サーバーの起動後、ブラウザーウィンドウでhttps:// license-server-host:port/flashaccessserver/tenant-name/flashaccess/license/v1 ** を開いて、サーバーが正しく設定されていることを確認します。 テナントの構成が正常に読み込まれた場合は、確認メッセージが表示されます。
