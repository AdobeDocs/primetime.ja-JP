---
seo-title: ECIファイルについて
title: ECIファイルについて
uuid: 124d8ab1-933b-4a1b-992a-919f3d799460
translation-type: tm+mt
source-git-commit: d8e4c39c297d69b154baf0b4d67cf09b5cf0a9d4

---


# ECIファイルについて{#about-eci-files}

CRLに加えて、Embedded Common Interface(ECI)ファイルも定期的に更新する必要があります。 アドビが新しいPrimetime DRMクライアントプラットフォームのサポートを追加するたびに(例：iOS、Android、Windows FlashPlayerなど)、新しいECIレコードが作成されます。 このクライアントの個別化をサポートするには、対応するECIレコードが個別化サーバーに存在する必要があります。

新しいPrimetime DRMクライアントのリリースはあまり頻繁ではないので、アドビは必要に応じて更新されたECIデータをリリースします。 アドビは定期的にECIファイルを収集し、以下の場所にホストして配布します。

```
http://cdmdownload.adobe.com/indiv/onprem/eci/Latest.txt
```

このフ [!DNL Latest.txt] ァイルには、最新のCRL配布ファイルのURLが含まれます。

アドビは、次に示す方法でECIのzipファイルを作成します。

フォルダ構造：

```
ECI\*
```

フォルダーの内容が再帰的に圧縮されます。

```
zip -R ECI ECI.zip
```

OpenSSL SHA-256ダイジェストがzipファイルの計算されます。

```
openssl dgst -sha256 -hex ECI.zip
```

zipファイルの名前が、アーカイブ日とSHA-256ダイジェストが含まれるように変更されます。

```
Rename ECI.zip to <DATE_SHA-256>.zip
```

例：

```
20150310_aea45bf06241f04fba2b310ff9a8066c6aba73c8d22387b60509481e9cefc43e.zip
```

上記の場所を定期的に確認し、更新されたECIファイルを確認する必要があります。

ダウンロード後に、次のプロセスを実行してインストールします。

1. SHA-256ダイジェストをメモし、OpenSSLまたは同等のツールを使用して再計算します。
1. ファイル名で指定されたものと比較します。
1. ファイルの名前をに変更しま [!DNL ECI.zip]す。
1. ディレクトリを解 [!DNL ECI] 凍します。
1. 古いECIディレクトリを新しいディレクトリに置き換えます。
1. 個別化サーバーを再起動します。

