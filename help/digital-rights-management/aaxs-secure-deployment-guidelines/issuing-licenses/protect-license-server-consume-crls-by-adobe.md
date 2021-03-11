---
title: Adobeが発行したCRLを使用
description: Adobeが発行したCRLを使用
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 0%

---


# Adobe{#consume-crls-published-by-adobe}が発行したCRLを使用

SDKは、Adobeが発行したCRLを定期的にダウンロードします。 これらのファイルへのアクセスをブロックしたり、これらのCRLの強制を防いだりしないでください。

SDKには、AdobeCRLを取得する際にエラーを無視する設定オプションがあります。 このオプションは、開発環境でのみ使用できます。 実稼働環境では、ライセンスサーバーがAdobeからCRLを取得できる必要があります。 有効なCRLを取得できない場合は、エラーです。
