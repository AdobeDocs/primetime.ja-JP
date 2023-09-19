---
title: トラブルシューティング
description: トラブルシューティング
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---

# トラブルシューティング{#troubleshooting}

デプロイメント中に発生する可能性のあるいくつかの問題と解決策を次に示します。

* 次のエラーメッセージが表示される場合：

  ```
  "Error decoding the password for HandlerConfiguration.ServerTransportCredential.password  
      javax.crypto.IllegalBlockSizeException: Input length must be multiple of 8 when decrypting with padded cipher"
  ```

  パスワードが `ScrambleUtil` クラス。

* 次のエラーメッセージが表示される場合：

  ```
  "Unable to load credential from file.pfx -- possibly wrong password."
  ```

  PFX ファイルに正しい暗号化パスワードが指定されていることを確認してください。

* 次のエラーメッセージが表示される場合：

  ```
  "javax.crypto.BadPaddingException: Given final block not properly padded"
  ```

  パスワードの scrambler クラスを使用していることを確認します。 *を参照してください。*. このスクランブラユーティリティは、保護されたストリーミング用のAdobe Primetime DRM サーバーで提供されているものとは異なります。
