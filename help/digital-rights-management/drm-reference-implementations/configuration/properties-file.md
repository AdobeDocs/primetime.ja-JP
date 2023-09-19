---
title: ライセンスサーバーのプロパティファイル
description: ライセンスサーバーのプロパティファイル
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 0%

---

# ライセンスサーバーのプロパティファイル{#license-server-properties-file}

ライセンスサーバーは、 [!DNL flashaccess-refimpl.properties] ファイル。 特定の値の詳細や、各プロパティの使用方法については、そのファイルを直接参照できます。 完全に機能するサンプルは、 [!DNL resources] 参照実装のディレクトリ ( `([DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\resources/).`) をクリックします。

**資格情報** - properties ファイルには、Adobeが発行する資格情報の場所の設定が含まれています。 これらの資格情報は、 [!DNL .pfx] ファイルにパスワードを入力するか、HSM に保存されている秘密鍵証明書のエイリアスとパスワードを入力します。 少なくともトランスポート秘密鍵証明書とライセンスサーバー秘密鍵証明書に関連するプロパティを構成する必要があります。 で指定したディレクトリに対する、資格情報ファイルの相対的な場所を指定します。 `config.resourcesDirectory` プロパティ。

**FlashメディアRights Managementサーバ** - `flashaccess-refimpl.properties` ファイルには、コンテンツのパッケージ化に関連するいくつかのプロパティも含まれています。 これらのプロパティは、FlashMediaRights ManagementServer 1.x のメタデータ変換にのみ使用されます。 このプロパティファイルの値を変更した後、変更を有効にするには、ライセンスサーバーを再起動します。
