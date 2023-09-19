---
title: 証明書の要求の概要
description: 証明書の要求の概要
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---

# 概要 {#request-certificates-overview}

Adobe Primetime DRM Production SDK を使用するには、次の手順を繰り返して、各証明書（ライセンスサーバー、パッケージャー、トランスポート）をリクエストします。 評価 SDK および体験版 SDK は、1 つの証明書を使用します。

>[!NOTE]
>
>このドキュメントで示す例では、OpenSSL を使用しています。 他のユーティリティも使用できます。 以下の例は参照用にのみ使用してください。 キーペアの生成、およびハードウェアセキュリティモジュール (HSM) へのキーと証明書の保存については、HSM のドキュメントを参照してください。
