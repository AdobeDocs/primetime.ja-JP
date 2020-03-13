---
seo-title: トラブルシューティング
title: トラブルシューティング
uuid: db76d6a4-c285-4d86-95a1-4f1a85ed3743
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# トラブルシューティング {#troubleshooting}

以下に、導入に関する一般的な問題と解決策を示します。

* 次のエラーが表示される場合：

   ```
       "Error decoding the password for HandlerConfiguration.ServerTransportCredential.password  
       javax.crypto.IllegalBlockSizeException: Input length must be multiple of 8 when decrypting with padded cipher"
   ```

   パスワードは、指定したクラスを使用して暗号化されていることを確 `ScrambleUtil` 認します。

* 次のエラーが表示される場合：

   ```
       "Unable to load credential from file.pfx -- possibly wrong password."
   ```

   PFXファイルに正しい暗号化パスワードを指定したことを確認してください。

* 次のエラーが表示される場合：

   ```
       "javax.crypto.BadPaddingException: Given final block not properly padded"
   ```

   参照実装で提供されるパスワードスクランブラクラスを使用していることを確認します（このスクランブラユーティリティは、保護されたストリーミング用のAdobe® Access™ Serverで提供されるものとは異なります）。

