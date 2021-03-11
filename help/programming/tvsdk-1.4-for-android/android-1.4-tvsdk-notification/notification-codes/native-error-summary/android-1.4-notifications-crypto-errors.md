---
description: Adobeビデオエンジンの暗号化モジュールは、NATIVE_ERRORメタデータオブジェクトに以下の通知を返します。
title: NATIVE_ERROR暗号化値
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '84'
ht-degree: 8%

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

