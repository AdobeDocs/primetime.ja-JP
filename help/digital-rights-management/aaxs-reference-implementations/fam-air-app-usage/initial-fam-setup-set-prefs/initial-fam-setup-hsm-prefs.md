---
seo-title: HSMの環境設定
title: HSMの環境設定
uuid: 1b97d582-d4b6-48cd-9c24-2d13493571e9
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# HSMの環境設定 {#hsm-preferences}

このタブの環境設定は、「Packager」タブでチェックボックスが選択さ **[!UICONTROL Enable HSM]** れている場合にのみ指定する必要があります。 次の表で、これらの環境設定について説明します。

| 環境設定 | 説明 |
|---|---|
| Sun PKCS#11構成ファイル名 | Sun PKCS#11プロバイダの設定ファイルのフルパスです。 この設定ファイルの内容の詳細については、SunのWebサイトのJava PKCS#11 Reference Guideを参照してください。 |
| Partition Password | PKCS#11設定ファイルで指定されたHSMパーティションのパスワードです。 |
| ライセンスサーバー証明書エイリアス | HSMに保存されるアドビ発行のライセンスサーバー証明書のエイリアス。 この証明書は、パッケージ化時にCEKを暗号化するために使用されます。 「Packager」タブで、「 *License Server Certificate* 」の代わりに「Packager」を指定します。 |
| ライセンスサーバートランスポート証明書エイリアス | HSMに保存されるアドビが発行するサーバートランスポート証明書のエイリアス。 この証明書は、クライアントとライセンスサーバー間の通信をセキュリティで保護するために使用されます。 「パッケージャー」タブで、「 *License Server Transport Certificate* 」の代わりにこの証明書を指定します。 |
| Packager Credential Alias | HSMに保存されるAdobeが発行するPackagerの秘密鍵証明書（証明書と秘密鍵）のエイリアス。 これは、パッケージ化時にメタデータに署名するために使用されます。 「Packager」タブで、「 *Packager Credential* 」の代わりに「Packager」を指定します。 |
| ライセンスサーバー資格情報エイリアス | HSMに保存されるアドビ発行のライセンスサーバー証明書（証明書および秘密鍵）のエイリアス。 この証明書は、ポリシー更新リストへの署名に使用されます。 「ポリシー更新リスト」タブで *、「* License Server Credential」の代わりにこの情報を指定します。 (このエイリアスは、通常、 *License Server Certificate Aliasと同じです*)。 |

