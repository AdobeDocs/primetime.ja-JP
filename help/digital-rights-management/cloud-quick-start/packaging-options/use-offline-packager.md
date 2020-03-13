---
seo-title: 付属のPrimetime Offline Packagerの使用
title: 付属のPrimetime Offline Packagerの使用
uuid: 16b535a9-81b5-43bc-9e42-a64eb6649d9a
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# 付属のPrimetime Offline Packagerの使用{#use-the-included-primetime-offline-packager}

Primetime Java Packagerには、コンテンツのパッケージ化に必要なほとんどの設定があらかじめ用意されています。 開始するために更新する必要がある領域は少数です。

## パッケージャーのプロパティの更新 {#section_99904D35E99944A28FF43D924E516CC2}

現在のタスクのコンテキスト

* 設定ファイルを使用してコンテンツをパッケージ化する前に、次のパッケージャーのプロパティを更新します。

### ユーザー指定のXML設定ファイルのプロパティ

| プロパティ名 | 説明 |
|---|---|
| `policy_file` | ポリシーファイルのパス。 アドビは、事前設定済みのポリシーをいくつか提供し、その中から選択する必要があります。 |
| `pkgr_pfx` | Packagerの資格情報のパス。 ここでは、アドビが発行する独自のPackager証明書( [!DNL .pfx])を指定する必要があります。 |
| `pkgr_pfx_pwd` | Packagerの資格情報のパスワード。 アドビが発行するPackagerの秘密鍵証明書にパスワードを指定する必要があります。 |

## コマンドラインを使用したパッケージ {#section_DFBE462679E34D62963BE201FD3321F9}

コンテンツをパッケージ化する前に、設定ファイルに必要な情報がすべて入力されていることを確認します。

* 設定ファイルと共にコンテンツをパッケージ化するには、コマンドラインで次の構文を使用します。

```
java -jar OfflinePackager.jar -conf_path [configuration filename]
```

コンテンツをHLSまたはHDS形式にパッケージ化するためのサンプル設定ファイルが、およびという名前で用意さ [!DNL config_hds.xml] れていま [!DNL config.hls.xml]す。

HDSまたはHLSのコンテンツは、Protection Kitディレクトリの下 [!DNL /output] のフォルダーに出力されます。 このディレクトリに書き込まれるすべてのアーティファクトは、再生するためにHTTP Webサーバーでホストされている必要があります。
