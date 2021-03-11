---
title: トラブルシューティング
description: トラブルシューティング
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---


# トラブルシューティング{#troubleshooting}

以下に、展開中に発生する可能性のある問題と解決策を示します。

* 次のエラーメッセージが表示される場合：

   ```
   "Error decoding the password for HandlerConfiguration.ServerTransportCredential.password  
       javax.crypto.IllegalBlockSizeException: Input length must be multiple of 8 when decrypting with padded cipher"
   ```

   パスワードが`ScrambleUtil`クラスで暗号化されていることを確認します。

* 次のエラーメッセージが表示される場合：

   ```
   "Unable to load credential from file.pfx -- possibly wrong password."
   ```

   PFXファイルで、正しい暗号化パスワードが指定されていることを確認してください。

* 次のエラーメッセージが表示される場合：

   ```
   "javax.crypto.BadPaddingException: Given final block not properly padded"
   ```

   リファレンス実装&#x200B;*で提供されているパスワードスクランブラクラス*&#x200B;を使用してください。 このスクランブラユーティリティは、保護ストリーミング用のAdobe PrimetimeDRMサーバに付属のスクランブラユーティリティとは異なります。

