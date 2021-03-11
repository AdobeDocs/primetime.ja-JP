---
title: パフォーマンスの調整
description: パフォーマンスの調整
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# パフォーマンス調整{#performance-tuning}

パフォーマンスを向上させるには、次のヒントを参考にしてください。

* ネットワークHSMの使用は、直接接続されたHSMの使用に比べて、大幅に遅くなる可能性があります。
* パフォーマンスを向上させるために、SDKの「thirdparty/cryptoj」フォルダーにあるプラットフォーム固有のライブラリをデプロイすることで、暗号化操作のネイティブサポートをオプションで有効にできます。 ネイティブサポートを有効にするには、プラットフォーム用のライブラリ（Windowsの場合はjsafe.dll、Linuxの場合はlibjsafe.so）をパスに追加します。

   >[!NOTE]
   >
   >同じTomcatインスタンスで複数のWebアプリケーションを実行し、パスに`jsafe.dll`がある場合、`jsafe.dll`ライブラリをロードできるのは最初のWebアプリケーションだけです。 したがって、最初のWebアプリケーションのみがネイティブサポートのメリットを受けます。 このような場合、すべてのWebアプリケーションのパフォーマンスを向上させるには、WARファイルの外側に`cryptoj.jar`を配置します。 例えば、`<tomcat_installation_folder>/lib`ディレクトリにあります。

* 64ビット版のRed Hat®やWindowsなどの64ビット版のオペレーティングシステムは、32ビット版のオペレーティングシステムと比べて、パフォーマンスが大幅に向上します。

