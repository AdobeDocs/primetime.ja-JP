---
description: SDKは、Adobeが発行したCRLを定期的にダウンロードします。 これらのファイルへのアクセスをブロックしないようにするか、これらのCRLの適用を妨げないようにする必要があります。
seo-description: SDKは、Adobeが発行したCRLを定期的にダウンロードします。 これらのファイルへのアクセスをブロックしないようにするか、これらのCRLの適用を妨げないようにする必要があります。
seo-title: Adobeが発行したCRLの使用
title: Adobeが発行したCRLの使用
uuid: 7a9088bd-dde6-4445-958c-3e7272215b3c
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---


# Adobe{#consuming-crls-published-by-adobe}が発行したCRLの使用

SDKは、Adobeが発行したCRLを定期的にダウンロードします。 これらのファイルへのアクセスをブロックしないようにするか、これらのCRLの適用を妨げないようにする必要があります。

SDKには、AdobeCRLの取得時にエラーを無視する設定オプションがあり、このオプションは開発環境でのみ適用できます。 実稼働環境では、ライセンスサーバーはAdobeからCRLを取得する必要があります。 ライセンスサーバーが有効なCRLを取得できない場合は、エラーが発生しました。
