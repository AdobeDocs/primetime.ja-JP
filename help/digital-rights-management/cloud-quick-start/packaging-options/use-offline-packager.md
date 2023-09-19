---
title: 付属の Primetime Offline Packager を使用
description: 付属の Primetime Offline Packager を使用
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---

# 付属の Primetime Offline Packager を使用{#use-the-included-primetime-offline-packager}

Primetime Java Packager には、コンテンツをパッケージ化するために必要な設定のほとんどが事前に設定されています。 開始するために更新する必要がある領域は少数です。

## Packager のプロパティを更新 {#section_99904D35E99944A28FF43D924E516CC2}

現在のタスクのコンテキスト

* 設定ファイルを使用してコンテンツをパッケージ化する前に、次の Packager プロパティを更新します。

### ユーザー指定の XML 設定ファイルのプロパティ

| プロパティ名 | 説明 |
|---|---|
| `policy_file` | ポリシーファイルのパス。 Adobeは、事前に設定されたポリシーをいくつか提供し、その中から選択します。 |
| `pkgr_pfx` | Packager の資格情報のパス。 独自のAdobe発行 Packager 資格情報 ( [!DNL .pfx]) を参照してください。 |
| `pkgr_pfx_pwd` | Packager の資格情報のパスワード。 ここで、パスワードをAdobe発行の Packager の資格情報に指定する必要があります。 |

## コマンドラインを使用したパッケージ {#section_DFBE462679E34D62963BE201FD3321F9}

コンテンツをパッケージ化する前に、設定ファイルに必要な情報がすべて入力されていることを確認してください。

* コンテンツを設定ファイルにパッケージ化するには、コマンドラインで次の構文を使用します。

```
java -jar OfflinePackager.jar -conf_path [configuration filename]
```

コンテンツを HLS または HDS 形式にパッケージ化するサンプルの設定ファイルが提供され、次の名前が付けられます。 [!DNL config_hds.xml] および [!DNL config.hls.xml].

HDS または HLS コンテンツは、 [!DNL /output] Protection Kit ディレクトリの下のフォルダ。 このディレクトリに書き込まれるアーティファクトを再生するには、すべて HTTP Web サーバーでホストする必要があります。
