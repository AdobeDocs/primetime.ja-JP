---
description: ポリシーの設定とは、保護されたビデオコンテンツの再生をユーザーに許可するタイミングと方法に関する条件を指定するプロセスです。
title: ポリシーの設定
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# ポリシーの設定{#setting-policies}

ポリシーの設定とは、保護されたビデオコンテンツの再生をユーザーに許可するタイミングと方法に関する条件を指定するプロセスです。

ポリシーの作成は、ライセンストークンリクエストの一部として行われます。 ( 詳しくは、 [https://www.expressplay.com/developer/restapi/#widevine-license-token-request](https://www.expressplay.com/developer/restapi/#widevine-license-token-request) Widevine の使用例を参照 )。

お客様のサーバー側コードが（権利チェック、位置情報またはその他の必要な情報に基づいて）ライセンスの発行を決定したら、トークンをリクエストし、 *トークン内* 必要なを指定します `securityLevel`, `hdcpOutputControl`、および `licenseDuration`. これらは、Widevine ポリシーのクライアントサイドオプションです。 他の DRM ソリューションも同様のアプローチを提供しますが、詳細はケースごとに異なり、個々のワークフローで詳細を説明します。

>[!NOTE]
>
>Adobeには、独自の使用権限サーバー/ストアフロントの実装方法を示すサンプルの参照サーバーが用意されています。 [参照サーバー： ExpressPlay 使用権限サーバーの例 (SEES)](../../multi-drm-workflows/feature-topics/sees-reference-server.md)
