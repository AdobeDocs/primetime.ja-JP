---
title: ファイアウォール規則
description: ファイアウォール規則
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '63'
ht-degree: 0%

---

# ファイアウォール規則{#firewall-rules}

個別化サーバーへの安全なアクセスを実現するには、特定のアプリケーションパスのみを公開する必要があります。 個別化サーバーは、クライアントから次のパスへの要求を受け入れる必要があります。

* [!DNL /flashaccess/i15n/*]
* [!DNL /flashaccess/status]
* [!DNL /crossdomain.xml]

サービスパス（例： ） [!DNL /flashaccess/admin/*] （つまり、status ページと admin ページ）は、ファイアウォール内からのみアクセスできる必要があります。 キー生成サーバーの一部は、ファイアウォールの外部からアクセスできません。
