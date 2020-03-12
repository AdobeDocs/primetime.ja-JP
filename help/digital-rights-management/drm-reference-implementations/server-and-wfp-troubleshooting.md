---
description: 'null'
seo-description: 'null'
seo-title: トラブルシューティング
title: トラブルシューティング
uuid: 06b86067-1ff6-4b4e-922f-7f968260ba19
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# トラブルシューティング{#troubleshooting}

以下に、展開中に発生する可能性のある問題と解決策を示します。

* 次のエラーメッセージが表示される場合：

   ```
   "Error decoding the password for HandlerConfiguration.ServerTransportCredential.password  
       javax.crypto.IllegalBlockSizeException: Input length must be multiple of 8 when decrypting with padded cipher"
   ```

   パスワードがクラスで暗号化されていることを確認 `ScrambleUtil` します。

* 次のエラーメッセージが表示される場合：

   ```
   "Unable to load credential from file.pfx -- possibly wrong password."
   ```

   PFXファイルで、正しい暗号化パスワードが指定されていることを確認します。

* 次のエラーメッセージが表示される場合：

   ```
   "javax.crypto.BadPaddingException: Given final block not properly padded"
   ```

   参照実装で提供されているパスワードスクラ *ンブラクラスを使用してください*。 このスクランブラユーティリティは、保護されたストリーミング用のAdobe Primetime DRMサーバーで提供されているユーティリティとは異なります。

