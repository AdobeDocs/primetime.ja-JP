---
title: 保護されたストリーミング用のAdobe Primetime DRM サーバーのアップグレード
description: 保護されたストリーミング用のAdobe Primetime DRM サーバーのアップグレード
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---

# 保護されたストリーミング用のAdobe Primetime DRM サーバーのアップグレード{#upgrading-the-adobe-primetime-drm-server-for-protected-streaming}

Primetime DRM サーバーを実行しているサーバーを保護されたストリーミング用にアップグレードする場合は、 `flashaccessserver.war` 最新の Primetime DRM に含まれるファイルを使用して、アプリケーションサーバーにデプロイされたファイル。

新しい設定オプションを使用する場合は、サーバーの `flashaccess-tenant.xml`. また、 [!DNL jsafe.dll] または [!DNL libjsafe.so] を、最新の Primetime DRM に含まれているバージョンに置き換えます。
