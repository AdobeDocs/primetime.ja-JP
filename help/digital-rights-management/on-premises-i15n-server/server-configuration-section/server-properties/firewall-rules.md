---
seo-title: ファイアウォール規則
title: ファイアウォール規則
uuid: f1629ceb-22de-4bb5-b73f-9b874d97ea8b
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# ファイアウォール規則{#firewall-rules}

個別化サーバーへのアクセスを保護するには、特定のアプリケーションパスのみを公開する必要があります。 個別化サーバーは、クライアントから次のパスへの要求を受け入れる必要があります。

* [!DNL /flashaccess/i15n/*]
* [!DNL /flashaccess/status]
* [!DNL /crossdomain.xml]

ステータスや管理ページな [!DNL /flashaccess/admin/*] どのサービスパスは、ファイアウォール内からのみアクセスできる必要があります。 鍵生成サーバーの一部は、ファイアウォールの外部からアクセスしないでください。
