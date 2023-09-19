---
description: Adobeビデオエンジンの暗号モジュールは、NATIVE_ERROR メタデータオブジェクトにこれらの通知を返します。
title: NATIVE_ERROR 暗号値
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 8%

---

# NATIVE_ERROR：暗号値{#native-error-crypto-values}

Adobeビデオエンジンの暗号モジュールは、NATIVE_ERROR メタデータオブジェクトにこれらの通知を返します。

| RUNTIME_CODE メタデータキーの値 | RUNTIME_CODE_MESSAGE メタデータキーの値 | 意味 |
|---|---|---|
| 300 | `CRYPTO_ALGORITHM_NOT_SUPPORTED` | 使用中のアルゴリズムはサポートされていません。 |
| 301 | `CRYPTO_ERROR_CORRUPTED_DATA` | データが破損しています。 |
| 302 | `CRYPTO_ERROR_BUFFER_TOO_SMALL` | バッファが小さすぎます。 |
| 303 | `CRYPTO_ERROR_BAD_CERTIFICATE` | 証明書が正しくありません。 |
| 304 | `CRYPTO_ERROR_DIGEST_UPDATE` | ダイジェストの更新。 |
| 305 | `CRYPTO_ERROR_DIGEST_FINISH` | ダイジェストが完了しました。 |
| 306 | `CRYPTO_ERROR_BAD_PARAMETER` | 無効なパラメータです。 |
