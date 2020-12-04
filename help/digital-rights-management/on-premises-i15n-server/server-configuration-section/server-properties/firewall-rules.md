---
seo-title: ファイアウォール規則
title: ファイアウォール規則
uuid: f1629ceb-22de-4bb5-b73f-9b874d97ea8b
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '63'
ht-degree: 0%

---


# ファイアウォール規則{#firewall-rules}

個別化サーバーへのアクセスを保護するには、特定のアプリケーションパスのみを公開する必要があります。 個別化サーバーは、クライアントから次のパスへの要求を受け入れる必要があります。

* [!DNL /flashaccess/i15n/*]
* [!DNL /flashaccess/status]
* [!DNL /crossdomain.xml]

[!DNL /flashaccess/admin/*]（例：ステータスページと管理ページ）などのサービスパスは、ファイアウォール内からのみアクセスできる必要があります。 Key Generation Serverの一部は、ファイアウォールの外部からアクセスできません。
