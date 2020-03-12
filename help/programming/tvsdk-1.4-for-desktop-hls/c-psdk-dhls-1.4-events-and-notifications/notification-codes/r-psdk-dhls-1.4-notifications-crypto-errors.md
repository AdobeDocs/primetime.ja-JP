---
description: Adobeビデオエンジンの暗号化モジュールは、NATIVE_ERRORメタデータオブジェクトに次の通知を返します。
seo-description: Adobeビデオエンジンの暗号化モジュールは、NATIVE_ERRORメタデータオブジェクトに次の通知を返します。
seo-title: NATIVE_ERROR暗号値
title: NATIVE_ERROR暗号値
uuid: 6f5cea7d-688f-421e-bba6-62aeae1ec9ee
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# NATIVE_ERROR:暗号化値{#native-error-crypto-values}

Adobeビデオエンジンの暗号化モジュールは、NATIVE_ERRORメタデータオブジェクトに次の通知を返します。

| RUNTIME_CODEメタデータキーの値 | RUNTIME_CODE_MESSAGEメタデータキーの値 | 意味 |
|---|---|---|
| 300 | `CRYPTO_ALGORITHM_NOT_SUPPORTED` | 使用中のアルゴリズムはサポートされていません。 |
| 301 | `CRYPTO_ERROR_CORRUPTED_DATA` | データが破損しています。 |
| 302 | `CRYPTO_ERROR_BUFFER_TOO_SMALL` | バッファが小さすぎます。 |
| 303 | `CRYPTO_ERROR_BAD_CERTIFICATE` | 証明書が正しくありません。 |
| 304 | `CRYPTO_ERROR_DIGEST_UPDATE` | ダイジェストの更新。 |
| 305 | `CRYPTO_ERROR_DIGEST_FINISH` | ダイジェストの完了。 |
| 306 | `CRYPTO_ERROR_BAD_PARAMETER` | パラメータが正しくありません。 |

