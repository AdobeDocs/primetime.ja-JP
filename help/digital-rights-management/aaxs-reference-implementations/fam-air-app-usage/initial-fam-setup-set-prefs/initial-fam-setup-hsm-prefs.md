---
seo-title: HSMの環境設定
title: HSMの環境設定
uuid: 1b97d582-d4b6-48cd-9c24-2d13493571e9
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---


# HSM環境設定{#hsm-preferences}

「Packager」タブで&#x200B;**[!UICONTROL Enable HSM]**&#x200B;チェックボックスが選択されている場合にのみ、このタブの環境設定を指定する必要があります。 次の表に、これらの環境設定を示します。

| 環境設定 | 説明 |
|---|---|
| Sun PKCS#11構成ファイル名 | Sun PKCS#11プロバイダーの設定ファイルへの完全なパスです。 この設定ファイルの内容の詳細については、SunのWebサイトのJava PKCS#11リファレンスガイドを参照してください。 |
| Partition Password | PKCS#11設定ファイルで指定されているHSMパーティションのパスワードです。 |
| ライセンスサーバー証明書エイリアス | HSMに保存されているAdobe発行のライセンスサーバー証明書のエイリアス。 この証明書は、パッケージ化の際にCEKを暗号化するために使用されます。 「Packager」タブで、「*License Server Certificate*」の代わりに「&lt;a0/>」を指定します。 |
| ライセンスサーバートランスポート証明書エイリアス | HSMに保存されているAdobe発行のサーバートランスポート証明書のエイリアス。 この証明書は、クライアントとライセンスサーバー間の通信をセキュリティで保護するために使用されます。 「Packager」タブで、「*License Server Transport Certificate*」の代わりに「&lt;a0/>」を指定します。 |
| Packager Credential Alias | HSMに保存されるAdobe発行のPackager証明書（証明書および秘密鍵）のエイリアス。 これは、パッケージ化の際にメタデータに署名するために使用されます。 「Packager」タブで、*Packagerの資格情報*&#x200B;の代わりにこれを指定します。 |
| License Server Credential Alias | HSMに保存されるAdobe発行のライセンスサーバー秘密鍵証明書（証明書および秘密鍵）のエイリアス。 この資格情報は、ポリシーの更新リストへの署名に使用されます。 「ポリシーの更新リスト」タブで、「*License Server Credential*」の代わりにこれを指定します。 （このエイリアスは、*ライセンスサーバー証明書エイリアス*&#x200B;と同じである可能性があります）。 |

