---
title: ライセンスサーバの設定ファイル
description: ライセンスサーバの設定ファイル
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 0%

---

# ライセンスサーバの設定ファイル{#license-server-configuration-files}

保護されたストリーミング用のAdobe Primetime DRM サーバーには、次の種類の設定ファイルが必要です。

* グローバル設定ファイル ( [!DNL flashaccess-global.xml])
* 各テナントのテナント設定ファイル ( [!DNL flashaccess-tenant.xml])

設定ファイルの編集が完了したら、Adobeで、保護されたストリーミング用 Primetime DRM サーバーに付属のユーティリティを使用して、ファイルの形式が正しいことを確認することをお勧めします。

詳しくは、 *設定バリデーター*.

Adobeを設定ファイル内のクリアテキストで使用できないようにする場合は、設定で指定した Scrambler ツールを使用して、グローバル設定ファイルとテナント設定ファイルで指定したすべてのパスワードを暗号化する必要があります。

詳しくは、 *パスワードスクランブラ* パスワードの暗号化方法の詳細については、を参照してください。
