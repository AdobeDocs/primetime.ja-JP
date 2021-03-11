---
title: ファイアウォール規則
description: ファイアウォール規則
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
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
