---
title: BEES リファレンス実装の構築
description: BEES リファレンス実装の構築
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 0%

---

# BEES リファレンス実装の構築 {#build-the-bees-reference-implementation}

Java 1.6.0_24 以降を使用していることを確認します。
1. 次のような必要な空のパスを入力します。 `tomcatdir` および `fasterxmldir` in [!DNL build-bees.xml]

   FasterXML/Jackson が含まれています。 また、からダウンロードすることもできます。 [https://jar-download.com/artifacts/com.fasterxml.jackson.core](https://jar-download.com/artifacts/com.fasterxml.jackson.core).
1. の実際の JAR ファイル名を更新 [!DNL build.common.xml] 別のバージョンの Jackson ライブラリを使用する場合。
1. を実行します。 `all` ～の標的 [!DNL build-bees.xml]:

   ```
   ant -f build-bees.xml
   ```

The [!DNL bees.war] が [!DNL bees-build/wars] フォルダー。
