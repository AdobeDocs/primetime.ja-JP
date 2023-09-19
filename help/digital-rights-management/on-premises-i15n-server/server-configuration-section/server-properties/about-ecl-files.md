---
title: ECI ファイルについて
description: ECI ファイルについて
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# ECI ファイルについて{#about-eci-files}

CRL に加えて、Embedded Common Interface(ECI) ファイルを定期的に更新する必要があります。 Adobeが新しい Primetime DRM クライアントプラットフォーム (iOS、Android、Windows FlashPlayer など ) のサポートを追加するたびに、新しい ECI レコードが作成されます。 このクライアントの個別化をサポートするには、対応する ECI レコードが個別化サーバーに存在する必要があります。

新しい Primetime DRM クライアントのリリースはあまり頻繁ではないので、Adobeは必要に応じて更新された ECI データをリリースします。 Adobeは定期的に ECI ファイルを収集し、配布用に以下の場所にホストします。

```
http://cdmdownload.adobe.com/indiv/onprem/eci/Latest.txt
```

The [!DNL Latest.txt] ファイルには、最新の CRL 配布ファイルの URL が含まれます。

Adobeは、以下に説明する方法で ECI zip ファイルを作成します。

フォルダー構造：

```
ECI\*
```

フォルダーのコンテンツは再帰的に圧縮されます。

```
zip -R ECI ECI.zip
```

OpenSSL SHA-256 ダイジェストが zip ファイルから計算されます。

```
openssl dgst -sha256 -hex ECI.zip
```

zip ファイルの名前が、アーカイブ日と SHA-256 ダイジェストが含まれるように変更されます。

```
Rename ECI.zip to <DATE_SHA-256>.zip
```

例：

```
20150310_aea45bf06241f04fba2b310ff9a8066c6aba73c8d22387b60509481e9cefc43e.zip
```

上記の場所を定期的に調べ、更新された ECI ファイルがないか確認する必要があります。

ダウンロード後に、次のインストールプロセスを実行します。

1. SHA-256 ダイジェストに注意し、OpenSSL または同等のツールを使用して再計算します。
1. ファイル名で指定されたファイルと比較します。
1. ファイル名をに変更します。 [!DNL ECI.zip].
1. を解凍します。 [!DNL ECI] ディレクトリ。
1. 古い ECI ディレクトリを新しいディレクトリに置き換えます。
1. 個別化サーバーを再起動します。
