---
title: 付属のPrimetime Offline Packagerの使用
description: 付属のPrimetime Offline Packagerの使用
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---


# 付属のPrimetime Offline Packager{#use-the-included-primetime-offline-packager}を使用

Primetime Java Packagerには、コンテンツのパッケージ化に必要なほとんどの設定があらかじめ用意されています。 開始するために更新する必要がある領域は少数です。

## パッケージャーのプロパティを更新{#section_99904D35E99944A28FF43D924E516CC2}

現在のタスクのコンテキスト

* 設定ファイルを使用してコンテンツをパッケージ化する前に、次のPackagerのプロパティを更新します。

### ユーザー指定のXML設定ファイルのプロパティ

| プロパティ名 | 説明 |
|---|---|
| `policy_file` | ポリシーファイルのパス。 Adobeは、事前設定済みのポリシーをいくつか提供し、その中から選択する必要があります。 |
| `pkgr_pfx` | Packagerの資格情報のパス。 独自のAdobe発行Packager資格情報([!DNL .pfx])をここに入力する必要があります。 |
| `pkgr_pfx_pwd` | Packagerの資格情報のパスワード。 Adobe発行のPackager証明書にパスワードを指定する必要があります。 |

## コマンドライン{#section_DFBE462679E34D62963BE201FD3321F9}を使用したパッケージ

コンテンツをパッケージ化する前に、設定ファイルに必要な情報がすべて提供されていることを確認してください。

* 設定ファイルにコンテンツをパッケージ化するには、コマンドラインで次の構文を使用します。

```
java -jar OfflinePackager.jar -conf_path [configuration filename]
```

コンテンツをHLSまたはHDS形式にパッケージ化するためのサンプル設定ファイルが用意されています。名前は[!DNL config_hds.xml]および[!DNL config.hls.xml]です。

HDSまたはHLSのコンテンツは、Protection Kitディレクトリの下の[!DNL /output]フォルダーに出力されます。 このディレクトリに書き込まれるすべてのアーティファクトを再生するには、HTTP Webサーバーでホストする必要があります。
