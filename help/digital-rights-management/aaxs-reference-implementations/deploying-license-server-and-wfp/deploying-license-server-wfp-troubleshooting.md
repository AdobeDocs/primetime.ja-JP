---
title: トラブルシューティング
description: トラブルシューティング
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---

# トラブルシューティング {#troubleshooting}

次に、デプロイメントに関する一般的な問題と解決策を示します。

* 次のエラーが表示される場合：

  ```
      "Error decoding the password for HandlerConfiguration.ServerTransportCredential.password  
      javax.crypto.IllegalBlockSizeException: Input length must be multiple of 8 when decrypting with padded cipher"
  ```

  指定した `ScrambleUtil` クラス。

* 次のエラーが表示される場合：

  ```
      "Unable to load credential from file.pfx -- possibly wrong password."
  ```

  PFX ファイルに正しい暗号化パスワードを指定していることを確認してください。

* 次のエラーが表示される場合：

  ```
      "javax.crypto.BadPaddingException: Given final block not properly padded"
  ```

  参照実装で提供されるAdobeスクランブラクラスを使用していることを確認してください ( このスクランブラユーティリティは、Protected Streaming 用の Password® Access™ Server で提供されるものとは異なります )。
