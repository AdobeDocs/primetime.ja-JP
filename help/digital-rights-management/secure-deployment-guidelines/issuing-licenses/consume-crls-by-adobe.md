---
description: SDKは、Adobeが発行したCRLを定期的にダウンロードします。 これらのファイルへのアクセスをブロックしないようにするか、これらのCRLの適用を妨げないようにする必要があります。
title: Adobeが発行したCRLの使用
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---


# Adobe{#consuming-crls-published-by-adobe}が発行したCRLの使用

SDKは、Adobeが発行したCRLを定期的にダウンロードします。 これらのファイルへのアクセスをブロックしないようにするか、これらのCRLの適用を妨げないようにする必要があります。

SDKには、AdobeCRLの取得時にエラーを無視する設定オプションがあり、このオプションは開発環境でのみ適用できます。 実稼働環境では、ライセンスサーバーはAdobeからCRLを取得する必要があります。 ライセンスサーバーが有効なCRLを取得できない場合は、エラーが発生しました。
