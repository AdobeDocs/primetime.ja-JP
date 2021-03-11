---
title: トラブルシューティング
description: トラブルシューティング
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---


# トラブルシューティング{#troubleshooting}

次に、展開に関する一般的な問題と解決策を示します。

* 次のエラーが表示される場合：

   ```
       "Error decoding the password for HandlerConfiguration.ServerTransportCredential.password  
       javax.crypto.IllegalBlockSizeException: Input length must be multiple of 8 when decrypting with padded cipher"
   ```

   指定した`ScrambleUtil`クラスを使用してパスワードが暗号化されていることを確認します。

* 次のエラーが表示される場合：

   ```
       "Unable to load credential from file.pfx -- possibly wrong password."
   ```

   PFXファイルに正しい暗号化パスワードを指定していることを確認してください。

* 次のエラーが表示される場合：

   ```
       "javax.crypto.BadPaddingException: Given final block not properly padded"
   ```

   リファレンス実装に付属のパスワードスクランブラクラスを使用していることを確認してください(このスクランブラユーティリティは、Adobe® Access™ Server for Protected Streamingで提供されるものとは異なります)。

