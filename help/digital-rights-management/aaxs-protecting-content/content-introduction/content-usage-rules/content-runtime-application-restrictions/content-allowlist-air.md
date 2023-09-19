---
title: Adobe® Primetime アプリケーションの許可リストで保護されたコンテンツの再生が許可される
description: Adobe® Primetime アプリケーションの許可リストで保護されたコンテンツの再生が許可される
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---

# Adobe® Primetime アプリケーションの許可リストで保護されたコンテンツの再生が許可される {#allowlist-for-adobe-primetime-applications-allowed-to-play-protected-content}

コンテンツを再生できるAIR/iOSアプリケーションを指定します。 AIR/iOSアプリケーション ID、最小バージョン、最大バージョンおよび発行者 ID を指定します。

使用例：このルールを使用して、特定のAIR/iOSアプリケーションの再生を制限したり、コンテンツにアクセス可能なバージョンを制御したりします。

>[!NOTE]
>
>AdobeFlash Builderを使用して保護されたアプリケーションを構築する場合は、アプリケーションを「デバッグ」モードでデプロイしないようにしてください。 アプリケーションを「デバッグ」モードでデプロイすると、Flash BuilderはAIRアプリケーション ID に「.debug」を追加します。 これにより、許可リストアクセスのAdobe機能が予期せず動作します。
