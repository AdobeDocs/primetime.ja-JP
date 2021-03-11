---
title: Adobeアクセス資格情報
description: Adobeアクセス資格情報
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---


# Adobeアクセス資格情報{#adobe-access-credentials}

Adobeアクセスクライアントが受け入れた有効なライセンスを発行するには、Adobeが発行した秘密鍵証明書のセットを使用して、保護ストリーミング用のAdobe Access Serverを設定する必要があります。 これらの秘密鍵証明書は、PKCS#12 (.pfx)ファイルに格納するか、HSMに格納することができます。

.pfxファイルはどこにでも配置できますが、設定を容易にするために、テナントの設定ディレクトリに.pfxファイルを配置することをお勧めします。 詳しくは、「[ライセンスサーバー構成ファイル](../../aaxs-protected-streaming/aaxs-license-server-config-files/aaxs-configuration-directory-structure.md)」を参照してください。