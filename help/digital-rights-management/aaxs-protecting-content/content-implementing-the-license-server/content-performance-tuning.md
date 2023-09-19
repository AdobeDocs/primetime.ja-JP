---
title: パフォーマンスの調整
description: パフォーマンスの調整
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# パフォーマンスの調整{#performance-tuning}

パフォーマンスを向上させるには、次のヒントを使用します。

* ネットワーク HSM の使用は、直接接続された HSM の使用に比べて大幅に遅くなる可能性があります。
* パフォーマンスを向上させるには、SDK の「thirdparty/cryptoj」フォルダーにあるプラットフォーム固有のライブラリをデプロイして、暗号化操作のネイティブサポートをオプションで有効にできます。 ネイティブサポートを有効にするには、プラットフォーム用のライブラリ（Windows の場合は jsafe.dll 、Linux の場合は libjsafe.so ）をパスに追加します。

  >[!NOTE]
  >
  >同じ Tomcat インスタンスで複数の Web アプリケーションを実行し、 `jsafe.dll` パスで、を読み込めるのは最初の web アプリケーションのみです。 `jsafe.dll` ライブラリ。 したがって、ネイティブサポートのメリットを得られるのは最初の Web アプリケーションのみです。 このような場合、すべての Web アプリケーションのパフォーマンスを向上させるには、 `cryptoj.jar`WAR ファイルの外側にあります。 例えば、 `<tomcat_installation_folder>/lib` ディレクトリ。

* 64 ビット版の Red Hat®や Windows などの 64 ビットオペレーティングシステムは、32 ビット版のオペレーティングシステムと比べてはるかに高いパフォーマンスを発揮します。
