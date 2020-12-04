---
seo-title: 要求証明書の概要
title: 要求証明書の概要
uuid: 3a4e79d7-1832-49d8-bcf2-a029b3729e6d
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---


# 概要{#request-certificates-overview}

Adobe PrimetimeDRM実稼動SDKを使用するには、次の手順を繰り返して各証明書（License Server、Packager、トランスポート）をリクエストします。 評価SDKと体験版SDKは、1つの証明書を使用します。

>[!NOTE]
>
>このドキュメントの例ではOpenSSLを使用しています。 他のユーティリティも使用できます。 以下の例は、参照用にのみ使用してください。 キーペアの生成、およびハードウェアセキュリティモジュール(HSM)へのキーと証明書の格納について詳しくは、HSMのドキュメントを参照してください。