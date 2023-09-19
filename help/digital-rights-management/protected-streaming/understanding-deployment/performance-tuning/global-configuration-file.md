---
description: このトピックでは、パフォーマンスに関する考慮事項について説明します。 グローバル設定ファイルの flashaccess-global.xml という設定は、パフォーマンスに影響を与えます。
title: グローバル設定ファイル
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# パフォーマンスの調整 {#performance-tuning}

このトピックでは、パフォーマンスに関する考慮事項について説明します。 グローバル設定ファイルの flashaccess-global.xml という設定は、パフォーマンスに影響を与えます。

## グローバル設定ファイル {#global-configuration-file}

設定ファイルには、次の設定要素が含まれています。

* `<Caching>` The `<Caching>` 要素は、メモリ内の設定ファイルのキャッシュを制御します。 The `<Caching>` 要素では、次の構文をサポートしています。

```
  <Caching refreshDelaySeconds="..." numTenants="..."/>
```

* `refreshDelaySeconds` サーバが構成ファイルの更新を確認する頻度を制御します。 の低い値： `refreshDelaySeconds` パフォーマンスに悪影響を与えますが、値を大きくするとパフォーマンスが向上します。

  詳しくは、 *設定ファイルの更新* 詳しくは、 `refreshDelaySeconds`.

* `numTenants` テナント数を指定します。 テナント数より少ない値は、残りのテナントに対する要求によってキャッシュミスが発生するので、パフォーマンスに影響します。 設定データのキャッシュミスがパフォーマンスに悪影響を与える。 そのため、考慮する必要のあるメモリ制限がない限り、この値は、サーバーに対して設定されているテナントの数よりも大きく設定することをお勧めします。

* `<Logging>` The `<Logging>` element は、ログファイルのロールのレベルと頻度を指定します。 The `<Logging>` 要素では、次の構文をサポートしています。

  ```
  <Logging level="..." rollingFrequency="..."/>
  ```

* `<level>`  `level` ログに対するメッセージを指定します。 値： `DEBUG` は、多くのログメッセージを生成し、パフォーマンスに悪影響を与える可能性があります。 次の設定を適用することをお勧めします。 `WARN` 最適なパフォーマンスを得るため。 ただし、この値を使用すると、ライセンス監査などの重要なランタイム情報が失われる場合があります。 パフォーマンスへの影響を最小限に抑えてログ情報を保存する場合は、 `INFO`.

* `<rollingFrequency>`  `rollingFrequency` ログファイルの頻度を指定します。 *ロール*. *`Rolling`* は、新しいログファイルをアクティブなログとして指定するプロセスです。 したがって、以前アクティブだったログファイルは変更できなくなり、 *`rolled`*. 周期の間隔は、 `MINUTELY`, `HOURLY`, `TWICE-DAILY`, `DAILY`, `WEEKLY`, `MONTHLY`または `NEVER`.

詳しくは、 *コンテンツの保護にAdobe Primetime DRM SDK を使用* パフォーマンスを最適化する方法に関するヒントを参照してください。
