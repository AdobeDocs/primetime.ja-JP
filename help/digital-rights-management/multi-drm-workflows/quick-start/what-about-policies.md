---
description: ポリシーの設定は、保護されたビデオコンテンツの再生をユーザーに許可するタイミングと方法の条件を指定するプロセスです。
title: ポリシーの設定
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---


# ポリシーの設定{#setting-policies}

ポリシーの設定は、保護されたビデオコンテンツの再生をユーザーに許可するタイミングと方法の条件を指定するプロセスです。

ポリシーの作成は、ライセンストークンリクエストの一部として行われます。 (Widevineの使用例は、[https://www.expressplay.com/developer/restapi/#widevine-license-token-request](https://www.expressplay.com/developer/restapi/#widevine-license-token-request)を参照)。

ユーザーのサーバー側コードは、（権限チェック、位置情報、またはその他の必要な情報に基づいて）ライセンスの発行を決定したら、トークンを要求し、トークン&#x200B;*に*&#x200B;必要な`securityLevel`、`hdcpOutputControl`、`licenseDuration`を指定します。 これらは、Widevineポリシーのクライアント側のオプションです。 その他のDRMソリューションオファーのアプローチは似ていますが、詳細はそれぞれのケースで異なり、個々のワークフローで詳しく説明されています。

>[!NOTE]
>
>Adobeには、独自のエンタイトルメントサーバー/ストアフロントを実装する方法を示すサンプルリファレンスサーバーが用意されています。[リファレンスサーバー：ExpressPlayエンタイトルメントサーバーの例(SEES)](../../multi-drm-workflows/feature-topics/sees-reference-server.md)

