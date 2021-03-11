---
title: 暗号化されたファイルの内容を調べる
description: 暗号化されたファイルの内容を調べる
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---


# 暗号化されたファイルの内容を調べています{#examining-encrypted-file-content}

Java APIを使用してFLVまたはF4Vファイルのコンテンツを調べるには、次の手順を実行します。

1. 開発環境を設定し、プロジェクト内の[開発環境の設定](../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md)で説明されているすべてのJARファイルを含めます。
1. `MediaEncrypter`インスタンスを作成します。
1. 暗号化されたファイルを`MediaEncrypter.examineEncryptedContent`メソッドに渡し、`KeyMetaData`オブジェクトを返します。
1. `KeyMetaData`オブジェクト内の情報をInspectします。

暗号化されたファイルからDRMメタデータを抽出する方法を示すサンプルコードについては、リファレンス実装のコマンドラインツールの「samples」ディレクトリの`com.adobe.flashaccess.samples.mediapackager.ExamineContent`を参照してください。
