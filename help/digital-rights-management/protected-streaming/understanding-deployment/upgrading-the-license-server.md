---
seo-title: 保護されたストリーミング用のAdobe Primetime DRMサーバーのアップグレード
title: 保護されたストリーミング用のAdobe Primetime DRMサーバーのアップグレード
uuid: 5c507ae3-d1d9-40ad-ba97-501ec92b45dc
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# 保護されたストリーミング用のAdobe Primetime DRMサーバーのアップグレード{#upgrading-the-adobe-primetime-drm-server-for-protected-streaming}

Primetime DRM Server for Protected Streamingを実行するサーバーをアップグレードする場合は、アプリケーションサーバーにデプロイされたファイルを、最新のPrimetime DRMに含まれているファイルに置き換える必要があります。 `flashaccessserver.war`

新しい設定オプションを使用する場合は、サーバーの更新が必要です `flashaccess-tenant.xml`。 また、最新のPrimetime DRMに含ま [!DNL jsafe.dll] れてい [!DNL libjsafe.so] るバージョンを更新するか、使用する必要があります。
