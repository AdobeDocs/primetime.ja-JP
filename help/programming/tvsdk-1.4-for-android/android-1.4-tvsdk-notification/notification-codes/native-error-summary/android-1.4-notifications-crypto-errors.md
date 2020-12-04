---
description: Adobeビデオエンジンの暗号化モジュールは、NATIVE_ERRORメタデータオブジェクトに以下の通知を返します。
seo-description: Adobeビデオエンジンの暗号化モジュールは、NATIVE_ERRORメタデータオブジェクトに以下の通知を返します。
seo-title: NATIVE_ERROR暗号化値
title: NATIVE_ERROR暗号化値
uuid: 5e86ba61-93e9-47cf-adad-8794957a1f7c
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 6%

---


# NATIVE_ERROR:暗号化値{#native-error-crypto-values}

Adobeビデオエンジンの暗号化モジュールは、NATIVE_ERRORメタデータオブジェクトに以下の通知を返します。

| NATIVE_ERROR_CODEメタデータキーの値 | NATIVE_ERROR_NAMEメタデータキーの値 | 意味 |
|---|---|---|
| 300 | `CRYPTO_ALGORITHM_NOT_SUPPORTED` | 使用中のアルゴリズムはサポートされていません。 |
| 301 | `CRYPTO_ERROR_CORRUPTED_DATA` | データが破損しています。 |
| 302 | `CRYPTO_ERROR_BUFFER_TOO_SMALL` | バッファが小さすぎます。 |
| 303 | `CRYPTO_ERROR_BAD_CERTIFICATE` | 不正な証明書。 |
| 304 | `CRYPTO_ERROR_DIGEST_UPDATE` | ダイジェストの更新。 |
| 305 | `CRYPTO_ERROR_DIGEST_FINISH` | ダイジェストの終了。 |
| 306 | `CRYPTO_ERROR_BAD_PARAMETER` | 無効なパラメータです。 |

