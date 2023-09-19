---
title: パフォーマンスの調整
description: パフォーマンスの調整
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# パフォーマンスの調整{#performance-tuning}

パフォーマンスを向上させるには、次のヒントを使用します。

* ネットワーク HSM の使用は、直接接続された HSM の使用に比べて大幅に遅くなる可能性があります。
* パフォーマンスを向上させるために、オプションで、 [!DNL thirdparty/cryptoj] SDK のフォルダー。 ネイティブサポートを有効にするには、プラットフォーム用のライブラリ（Windows の場合は jsafe.dll 、Linux の場合は libjsafe.so ）をパスに追加します。

  >[!NOTE]
  >
  >同じ Tomcat インスタンスで複数の Web アプリケーションを実行し、 `jsafe.dll` パスで、を読み込めるのは最初の web アプリケーションのみです。 `jsafe.dll` ライブラリ。 したがって、ネイティブサポートのメリットを得られるのは最初の Web アプリケーションのみです。 このような場合、すべての Web アプリケーションのパフォーマンスを向上させるには、 `cryptoj.jar`WAR ファイルの外側にあります。 例えば、 `<tomcat_installation_folder>/lib` ディレクトリ。

* 64 ビット版の Red Hat®や Windows などの 64 ビットオペレーティングシステムは、32 ビット版のオペレーティングシステムと比べてはるかに高いパフォーマンスを発揮します。

## 乱数の生成 (Linux) {#section_3E2E936A538F40B7BF8892C65E117907}

特定の条件下で、Linux 環境は、次のような乱数生成を必要とする Primetime DRM 関連の操作を実行すると一時停止する場合があります。

* Adobe Primetime DRM ライセンスサーバーの起動
* を使用したポリシーの生成 [!DNL AdobePolicyManager] ユーティリティ
* DRM で保護されたコンテンツのAdobe Media Serverまたは Primetime OfflinePackager でのパッケージ化

これらの操作中の遅延は、多くの場合、Linux サーバ上の低エントロピープールの結果です。

Linux では、サーバ環境のエントロピープールから乱数が生成されます。 エントロピープールは、通常、Linux カーネルがハードウェア割り込みを受け取ることで維持されます。 サーバが分離され、HW リソース（マウスやキーボードなど）からの通常の入力を受け取らない場合、はエントロピープールの再充填を待つことができます。 このシナリオでは、操作はからのデータを待機します。 [!DNL /dev/random] 一時停止する場合があります。

十分なエントロピーが生成されるように、Linux サーバ上でハードウェアの乱数ジェネレータを使用できます。 ただし、特定の展開シナリオでハードウェア乱数ジェネレータが使用できない場合は、ソフトウェアベースのソリューションを使用して、エントロピープールのリフレッシュレートを増やすことができます。 Linux 上のそのようなソフトウェアソリューションの 1 つは、 [!DNL haveged] （HArdware Volatile Entropy Gathering and Expansion デーモン）。

## 利用可能なエントロピーの決定 {#section_686B311FE6144566B6939E9F20915ADC}

予期しない遅延の間に、特定のサーバのエントロピープールで使用可能なビット数を確認するには、次のコマンドを実行します。

```
cat /proc/sys/kernel/random/entropy_avail 
```

エントロピーの多い健全な Linux システムは、完全な 4,096 ビットのエントロピーに近い状態で戻る。 返される値が 200 未満の場合、システムのエントロピーは非常に低くなっています。
