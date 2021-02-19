---
description: 広告挿入のリクエストはすべて、同じURL構造と同じ基本クエリパラメーターを使用します。 追加のクエリパラメーターを使用すると、マニフェストサーバーが様々なクライアントや状況で機能するようになります。
seo-description: 広告挿入のリクエストはすべて、同じURL構造と同じ基本クエリパラメーターを使用します。 追加のクエリパラメーターを使用すると、マニフェストサーバーが様々なクライアントや状況で機能するようになります。
seo-title: 広告挿入の要求
title: 広告挿入の要求
uuid: e42b3228-bff7-4202-86ed-7f631f3016ae
translation-type: tm+mt
source-git-commit: e437f4143fb939f46d106c64efc391137c33fe17
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---


# 広告挿入の要求{#requests-for-ad-insertion}

広告挿入のリクエストはすべて、同じURL構造と同じ基本クエリパラメーターを使用します。 追加のクエリパラメーターを使用すると、マニフェストサーバーが様々なクライアントや状況で機能するようになります。

| パラメータ | 説明 |
|--- |--- |
| u | アセットIDは、Adobe PrimetimeAd Decisioningメタデータのad_request_idのMD5ハッシュです。 お客様のAdobeテクニカルアカウントマネージャが提供します。 |
| z | Auditudeに指定する必要があるアセットのゾーンID。 お客様のAdobeテクニカルアカウントマネージャが提供します。 |
| `__sid__` | マニフェストサーバーがセッションIDの生成に使用する一意のID。 |

>[!NOTE]
>
>`__sid__`パラメーターは、重複のアンダースコア文字で囲まれます。

マニフェストサーバーは、個々のクライアントまたはクライアントグループのセッションを維持し、異なるクライアントに対するAPIインタラクションのシーケンスを個別に維持します。 クライアントがブートストラップURLをマニフェストサーバーに送信する`__sid__`は、環境内で一意である必要があります。 マニフェストサーバーは、このIDを使用してグローバルに一意のIDを構築し、それをクライアントに返します。

残りのクエリパラメーターは、様々なクライアントや状況に関係します。