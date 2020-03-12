---
description: ポリシーの設定は、保護されたビデオコンテンツの再生をユーザーに許可するタイミングと方法の条件を指定するプロセスです。
seo-description: ポリシーの設定は、保護されたビデオコンテンツの再生をユーザーに許可するタイミングと方法の条件を指定するプロセスです。
seo-title: ポリシーの設定
title: ポリシーの設定
uuid: 2d2672ce-5ed4-4868-aa5e-0a9e21a809b3
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# ポリシーの設定{#setting-policies}

ポリシーの設定は、保護されたビデオコンテンツの再生をユーザーに許可するタイミングと方法の条件を指定するプロセスです。

ポリシーの作成は、ライセンストークンリクエストの一部として行われます。 (Widevineの使 [用例につ](https://www.expressplay.com/developer/restapi/#widevine-license-token-request) いては、https://www.expressplay.com/developer/restapi/#widevine-license-token-requestを参照)。

お客様のサーバー側コードが、（権限の確認、位置情報、またはその他の必要な情報に基づいて）ライセンスの発行を決定したら、トークンを要求し、トークン内で *必要な* 、およびを指 `securityLevel`定し `hdcpOutputControl`ます `licenseDuration`。 Widevineポリシーのクライアント側のオプションです。 他のDRMソリューションも同様の方法を提供しますが、詳細は各ケースで異なり、個々のワークフローで詳しく説明されています。

>[!NOTE]
>
>独自のエンタイトルメントサーバー/ストアフロントを実装する方法を示すサンプルリファレンスサーバーが用意されています。リファレ [ンスサーバ：ExpressPlayエンタイトルメントサーバーの例(SEE)](../../multi-drm-workflows/feature-topics/sees-reference-server.md)

