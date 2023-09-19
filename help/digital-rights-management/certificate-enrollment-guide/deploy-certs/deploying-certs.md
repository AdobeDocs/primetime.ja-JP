---
title: 証明書をデプロイする
description: 証明書をデプロイする
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 0%

---

# 証明書をデプロイする{#deploy-certificates}

PFX パスワードがライセンスサーバー上の明確なテキストで使用できないように、参照実装と保護されたストリーミング用Adobe Primetime DRM サーバーでは、設定ファイルで指定したパスワードを暗号化する必要があります。 詳しくは、 *Primetime DRM 参照実装の使用* または *Primetime DRM サーバーの使用* 保護されたストリーミング用を参照してください。 それぞれに独自のスクランブルユーティリティが含まれ、暗号化されたパスワードは、これら 2 つのライセンスサーバの実装間で交換できません。

証明書とスクランブルされたパスワードをライセンスサーバにデプロイするには、 *Primetime DRM 参照実装の使用* または *保護されたストリーミング用の Primetime DRM サーバーの使用*.
