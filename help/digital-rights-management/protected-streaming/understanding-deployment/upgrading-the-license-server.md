---
seo-title: 保護されたストリーミング用のAdobe PrimetimeDRMサーバーのアップグレード
title: 保護されたストリーミング用のAdobe PrimetimeDRMサーバーのアップグレード
uuid: 5c507ae3-d1d9-40ad-ba97-501ec92b45dc
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---


# 保護されたストリーミング用のAdobe PrimetimeDRMサーバーのアップグレード{#upgrading-the-adobe-primetime-drm-server-for-protected-streaming}

Primetime DRM Server for Protected Streamingを実行するサーバーをアップグレードする場合は、アプリケーションサーバーにデプロイされている`flashaccessserver.war`ファイルを、最新のPrimetime DRMに含まれているファイルに置き換える必要があります。

新しい設定オプションを使用する場合は、サーバの`flashaccess-tenant.xml`を更新する必要があります。 また、[!DNL jsafe.dll]または[!DNL libjsafe.so]を、最新のPrimetime DRMに含まれているバージョンに更新する必要があります。
