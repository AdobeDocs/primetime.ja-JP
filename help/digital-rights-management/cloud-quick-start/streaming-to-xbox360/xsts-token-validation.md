---
seo-title: Xbox Live XSTSトークンの検証
title: Xbox Live XSTSトークンの検証
uuid: 9647f8ee-32d6-4bed-bae2-8b36a72d04ce
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Xbox Live XSTSトークンの検証{#xbox-live-xsts-token-validation}

XSTS要求の場合、このフィールド `customerSpecificAuthToken` にはBase64エンコードされたXSTSトークンが含まれます。 サンプルコー `XSTSValidator` ドは、Base64でデコードされたトークンを調べて、要素が存在するかどうかを調 `EncryptedAssertion` べます。ただし、他の方法を使用して、Xbox以外のリクエストとXbox以外のリクエストを区別できます。 例えば、別のURLを使用できます。

応答メッセージに返されたポリシーは、Xboxキーの要求で提供されるDRMメタデータの元のポリシーより優先されます。 Xboxクライアントでは、ポリシー機能の一部のみがサポートされ、元のポリシーを上書きするのはこれらのフィールドだけです。

トークンの解読と検証をサポートするために必要な追加の設定手順があります。 および秘密鍵証明書をJKS [!DNL xsts_partner_cert.pfx] 形式 [!DNL x_secure_token_service.part.xboxlive.com.cer] キーストアに読み込み、システムプロパティとしてバックエンドのエンタイトルメントサーバーに提供する必要がありま `xsts-keystore`す。 デフォルトでは、パートナーに [!DNL .pfx] はエイリアスが `xsts`、トークン検証証明書にはエイリアスが割り当てられま `xsts-verify-cert`す。 システムプロパティを使用して、これらを上書きすることもできます。 最後に、デフォルト値を持たないシステ `xsts-keystore-password` ムプロパティがあり、キーストアのパスワードが含まれています。 コードで読み取られるシステムプロ `XSTSValidator` パティを以下にまとめます。

| システムプロパティ | デフォルト値 | コメント |
|---|---|---|
| `xsts-keystore` | `xsts.jks` | バリデーターが使用するJKS形式キーストア。 |
| `xsts-keystore-password` |  | キーストアのパスワード |
| `xsts-alias` | `xsts` | キーストアから復号キーを取得するために使用されるエイリアス |
| `xsts-verify-cert-alias` | `xsts-verify-cert` | キーストアから検証証明書を取得するために使用されるエイリアス |

