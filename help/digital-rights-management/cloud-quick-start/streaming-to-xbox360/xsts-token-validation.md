---
title: Xbox Live XSTSトークンの検証
description: Xbox Live XSTSトークンの検証
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---


# Xbox Live XSTSトークンの検証{#xbox-live-xsts-token-validation}

XSTS要求の場合、`customerSpecificAuthToken`フィールドにはBase64エンコードされたXSTSトークンが含まれます。 サンプル`XSTSValidator`コードは、Base64でデコードされたトークンを調べ、`EncryptedAssertion`要素が存在するかどうかを調べます。ただし、他の方法を使用して、Xbox以外の要求とXbox以外の要求を区別することができます。 例えば、別のURLを使用できます。

応答メッセージに返されたポリシーは、Xboxキーの要求で提供されたDRMメタデータの元のポリシーに優先します。 Xboxクライアントがサポートするポリシー機能の一部のみがサポートされ、元のポリシーを上書きするのはこれらのフィールドのみです。

トークンの復号化と検証をサポートするために必要な追加の設定手順があります。 [!DNL xsts_partner_cert.pfx]秘密鍵証明書と[!DNL x_secure_token_service.part.xboxlive.com.cer]秘密鍵証明書をJKS形式キーストアに読み込み、バックエンドのエンタイトルメントサーバーにシステムプロパティ`xsts-keystore`として提供する必要があります。 デフォルトでは、パートナー[!DNL .pfx]はエイリアス`xsts`を持ち、トークン検証証明書はエイリアス`xsts-verify-cert`を持ちます。 これらは、システムプロパティを使用して上書きすることもできます。 最後に、デフォルトを持たないシステムプロパティ`xsts-keystore-password`があり、キーストアのパスワードが含まれています。 `XSTSValidator`コードで読み取られるシステムプロパティを以下にまとめます。

| システムプロパティ | デフォルト値 | コメント |
|---|---|---|
| `xsts-keystore` | `xsts.jks` | バリデーターで使用されるJKS形式キーストアです。 |
| `xsts-keystore-password` |  | キーストアのパスワード |
| `xsts-alias` | `xsts` | キーストアから復号キーを取得するために使用されるエイリアス |
| `xsts-verify-cert-alias` | `xsts-verify-cert` | キーストアから検証証明書を取得するために使用されるエイリアス |

