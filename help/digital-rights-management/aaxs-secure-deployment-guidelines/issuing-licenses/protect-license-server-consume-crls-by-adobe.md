---
seo-title: Adobeが発行したCRLを使用
title: Adobeが発行したCRLを使用
uuid: 43f65edb-0c96-46ab-b787-1b5f0b4b093e
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 0%

---


# Adobe{#consume-crls-published-by-adobe}が発行したCRLを使用

SDKは、Adobeが発行したCRLを定期的にダウンロードします。 これらのファイルへのアクセスをブロックしたり、これらのCRLの強制を防いだりしないでください。

SDKには、AdobeCRLを取得する際にエラーを無視する設定オプションがあります。 このオプションは、開発環境でのみ使用できます。 実稼働環境では、ライセンスサーバーがAdobeからCRLを取得できる必要があります。 有効なCRLを取得できない場合は、エラーです。
