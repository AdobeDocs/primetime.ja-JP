---
title: 要求証明書の概要
description: 要求証明書の概要
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---


# 概要{#request-certificates-overview}

Adobe PrimetimeDRM実稼動SDKを使用するには、次の手順を繰り返して各証明書（License Server、Packager、トランスポート）をリクエストします。 評価SDKと体験版SDKは、1つの証明書を使用します。

>[!NOTE]
>
>このドキュメントの例ではOpenSSLを使用しています。 他のユーティリティも使用できます。 以下の例は、参照用にのみ使用してください。 キーペアの生成、およびハードウェアセキュリティモジュール(HSM)へのキーと証明書の格納について詳しくは、HSMのドキュメントを参照してください。