---
title: 暗号化されたファイルの内容を調べる
description: 暗号化されたファイルの内容を調べる
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---


# 暗号化されたファイルの内容を調べています{#examining-encrypted-file-content}

Java APIを使用して、暗号化されたメディアファイルの内容を調べることができます。

暗号化されたファイルの内容を調べるには：

1. 開発環境を設定し、すべてのJARファイルを含めます。 プロジェクト用の&#x200B;*SDK*&#x200B;の設定を参照してください。
1. `MediaEncrypter`インスタンスを作成します。
1. 暗号化されたファイルを`MediaEncrypter.examineEncryptedContent`メソッドに渡し、`KeyMetaData`オブジェクトを返します。

1. `KeyMetaData`オブジェクト内の情報をInspectします。

暗号化されたファイルからDRMメタデータを抽出する方法を説明するサンプルコードについては、リファレンス実装のコマンドラインツール[!DNL samples/]ディレクトリの`com.adobe.flashaccess.samples.mediapackager.ExamineContent`を参照してください。
