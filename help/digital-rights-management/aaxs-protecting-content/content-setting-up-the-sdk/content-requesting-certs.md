---
title: 証明書の要求
description: 証明書の要求
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---

# 証明書の要求{#requesting-certificates}

登録は、証明書を要求するプロセスです。Adobe キーを生成し、Adobeに送信するリクエストを作成できます。 Adobeが証明書を生成し、返送します。 Adobeは、秘密鍵の内容を認識しません。 したがって、ハードウェア障害が発生した場合にキーを回復できるように、キーをバックアップする方法が必要です。

License Server、Packager または Transport 証明書とは異なり、Domain CA 証明書はAdobeによって発行されません。 この証明書は、証明機関から取得することも、自己署名証明書を生成することもできます。

Adobeアクセス資格情報の取得方法については、 *Adobeアクセス証明書登録ガイド*.
