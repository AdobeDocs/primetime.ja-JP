---
seo-title: パフォーマンス調整
title: パフォーマンス調整
uuid: bb5321a0-48ef-49cb-aaf0-00d7ab9562fe
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# パフォーマンス調整{#performance-tuning}

パフォーマンスを向上させるには、次のヒントを参考にしてください。

* ネットワークHSMの使用は、直接接続されたHSMを使用する場合よりも、大幅に遅くなる可能性があります。
* パフォーマンスを向上させるために、SDKの「thirdparty/cryptoj」フォルダーにあるプラットフォーム固有のライブラリをデプロイすることで、オプションで暗号化操作のネイティブサポートを有効にできます。 ネイティブサポートを有効にするには、プラットフォームのライブラリ（Windowsの場合はjsafe.dll、Linuxの場合はlibjsafe.so）をパスに追加します。

   >[!NOTE] {class=&quot;- topic/note &quot;}
   >
   >同じTomcatインスタンスで複数のWebアプリケーションを実行し、パスに `jsafe.dll` ある場合、読み込む最初のWebアプリケーションのみがライブラリを読み込め `jsafe.dll` ます。 したがって、最初のWebアプリケーションのみがネイティブサポートのメリットを受けます。 このような場合、すべてのWebアプリケーションのパフォーマンスを向上させるには、WARファ `cryptoj.jar`イルの外側に配置します。 例えば、ディレクトリ内 `<tomcat_installation_folder>/lib` です。

* 64ビット版のRed Hat®やWindowsなどの64ビット版のオペレーティングシステムは、32ビット版のオペレーティングシステムよりもはるかに高いパフォーマンスを提供します。

