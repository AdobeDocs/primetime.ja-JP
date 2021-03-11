---
title: ストアキー
description: ストアキー
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---


# ストアキー{#store-keys}

Adobeでは、署名および暗号化のための暗号化秘密鍵を、安全な改ざん配達確認のハードウェアデバイスに格納することを推奨します。 ソフトウェアに保存されるキーは、ハードウェアに保存されるキーよりも、妥協の影響を受けやすくなります。 例えば、ソフトウェアキーが漏れた場合、そのキーを含むキーやファイルは通常コピーされるので、違反を検出するのは困難です。 ハードウェアに保存されるキーは、検出されない妥協に対する脆弱性が低くなります。

ハードウェアセキュリティモジュール(HSM)は、暗号鍵を保存し保護する、専用のハードウェアデバイスです。 詳しくは、「*コンテンツの保護にAdobe PrimetimeDRM SDKを使用する*」の「*資格情報の保存*」を参照してください。
