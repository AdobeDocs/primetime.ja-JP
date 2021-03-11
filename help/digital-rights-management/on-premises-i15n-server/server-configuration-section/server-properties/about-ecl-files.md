---
title: ECIファイルについて
description: ECIファイルについて
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---


# ECIファイルについて{#about-eci-files}

CRLに加えて、Embedded Common Interface(ECI)ファイルも定期的に更新する必要があります。 Adobeが新しいPrimetime DRMクライアントプラットフォームのサポートを追加した場合(例：iOS、Android、Windows FlashPlayerなど)では、新しいECIレコードが作成されます。 このクライアントの個別化をサポートするには、対応するECIレコードが個別化サーバーに存在する必要があります。

新しいPrimetime DRMクライアントのリリースはあまり頻繁に行われないので、Adobeは必要に応じて更新されたECIデータをリリースします。 定期的に、AdobeはECIファイルを収集し、以下の場所にホストして配布します。

```
http://cdmdownload.adobe.com/indiv/onprem/eci/Latest.txt
```

[!DNL Latest.txt]ファイルには、最新のCRL配布ファイルへのURLが含まれます。

Adobeは、次に示す方法でECI zipファイルを作成します。

フォルダ構造：

```
ECI\*
```

フォルダーの内容が再帰的に圧縮されます。

```
zip -R ECI ECI.zip
```

OpenSSL SHA-256ダイジェストは、次のzipファイルに基づいて計算されます。

```
openssl dgst -sha256 -hex ECI.zip
```

zipファイルの名前が変更され、アーカイブ日とSHA-256ダイジェストが含まれます。

```
Rename ECI.zip to <DATE_SHA-256>.zip
```

例：

```
20150310_aea45bf06241f04fba2b310ff9a8066c6aba73c8d22387b60509481e9cefc43e.zip
```

上記の場所を定期的にチェックし、更新されたECIファイルがないか確認する必要があります。

ダウンロード後に、次のプロセスを実行してインストールします。

1. SHA-256ダイジェストをメモし、OpenSSLまたは同等のツールを使用して再計算します。
1. ファイル名に指定されたものと比較します。
1. ファイル名を[!DNL ECI.zip]に変更します。
1. [!DNL ECI]ディレクトリを解凍します。
1. 古いECIディレクトリを新しいディレクトリに置き換えます。
1. 個別化サーバーを再起動します。

