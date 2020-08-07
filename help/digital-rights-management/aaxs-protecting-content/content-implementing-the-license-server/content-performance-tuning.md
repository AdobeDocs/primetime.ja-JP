---
seo-title: パフォーマンスの調整
title: パフォーマンスの調整
uuid: bb5321a0-48ef-49cb-aaf0-00d7ab9562fe
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# パフォーマンスの調整{#performance-tuning}

パフォーマンスを向上させるには、次のヒントを参考にしてください。

* ネットワークHSMの使用は、直接接続されたHSMの使用に比べて、大幅に遅くなる可能性があります。
* パフォーマンスを向上させるために、SDKの「thirdparty/cryptoj」フォルダーにあるプラットフォーム固有のライブラリをデプロイすることで、暗号化操作のネイティブサポートをオプションで有効にできます。 ネイティブサポートを有効にするには、プラットフォーム用のライブラリ（Windowsの場合はjsafe.dll、Linuxの場合はlibjsafe.so）をパスに追加します。

   >[!NOTE]
   >
   >同じTomcatインスタンスで複数のWebアプリケーションを実行し、パスにある場合、読み込む最初 `jsafe.dll` のWebアプリケーションのみが `jsafe.dll` ライブラリを読み込めます。 したがって、最初のWebアプリケーションのみがネイティブサポートのメリットを受けます。 このような場合は、すべてのWebアプリケーションのパフォーマンスを向上させるには、WARファイルの `cryptoj.jar`外側に配置します。 例えば、 `<tomcat_installation_folder>/lib` ディレクトリ内。

* 64ビット版のRed Hat®やWindowsなどの64ビット版のオペレーティングシステムは、32ビット版のオペレーティングシステムと比べて、パフォーマンスが大幅に向上します。

