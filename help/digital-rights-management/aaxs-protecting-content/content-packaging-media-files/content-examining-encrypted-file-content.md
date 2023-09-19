---
title: 暗号化されたファイルコンテンツの検査
description: 暗号化されたファイルコンテンツの検査
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---

# 暗号化されたファイルコンテンツの検査 {#examining-encrypted-file-content}

Java API を使用して FLV または F4V ファイルの内容を調べるには、次の手順を実行します。

1. 開発環境を設定し、 [開発環境の設定](../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md) を選択します。
1. の作成 `MediaEncrypter` インスタンス。
1. 暗号化されたファイルをに渡します。 `MediaEncrypter.examineEncryptedContent` メソッド。 `KeyMetaData` オブジェクト。
1. Inspect `KeyMetaData` オブジェクト。

暗号化されたファイルから DRM メタデータを抽出する方法を示すサンプルコードについては、 `com.adobe.flashaccess.samples.mediapackager.ExamineContent` 「リファレンス実装」コマンドラインツールの「samples」ディレクトリ。
