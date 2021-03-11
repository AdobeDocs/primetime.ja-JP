---
description: ここでは、パフォーマンスに関する考慮事項について説明します。 グローバル設定ファイル内のflashaccess-global.xmlという設定は、パフォーマンスに影響します。
title: グローバル設定ファイル
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---


# {#performance-tuning}のパフォーマンス調整

ここでは、パフォーマンスに関する考慮事項について説明します。 グローバル設定ファイル内のflashaccess-global.xmlという設定は、パフォーマンスに影響します。

## グローバル構成ファイル{#global-configuration-file}

設定ファイルには、次の設定要素が含まれます。

* `<Caching>` この `<Caching>` 要素は、メモリ内の設定ファイルのキャッシュを制御します。`<Caching>`要素は、次の構文をサポートします。

```
  <Caching refreshDelaySeconds="..." numTenants="..."/>
```

* `refreshDelaySeconds` サーバーが設定ファイルの更新をチェックする頻度を制御します。`refreshDelaySeconds`の値を小さくするとパフォーマンスが低下し、大きくするとパフォーマンスが向上します。

   `refreshDelaySeconds`の詳細については、*設定ファイルの更新*&#x200B;を参照してください。

* `numTenants` テナント数を指定します。テナントの数より小さい値を指定すると、残りのテナントに対する要求はキャッシュミスを引き起こすので、パフォーマンスが低下します。 設定データのキャッシュミスがパフォーマンスに悪影響を与えます。 そのため、考慮する必要のあるメモリ制限がない限り、サーバーに対して設定されているテナントの数よりも大きい値を設定することをお勧めします。

* `<Logging>` この `<Logging>` 要素は、ログレベルとログファイルのロール頻度を指定します。`<Logging>`要素は、次の構文をサポートします。

   ```
   <Logging level="..." rollingFrequency="..."/>
   ```

* `<level>`  `level` ログに対するメッセージを指定します。`DEBUG`の値を指定すると、多くのログメッセージが生成され、パフォーマンスに悪影響を与える可能性があります。 最適なパフォーマンスを得るために`WARN`の設定を適用することをお勧めします。 ただし、この値を使用すると、ライセンス監査など、重要なランタイム情報を失う場合があります。 パフォーマンスへの影響を最小限に抑えてログ情報を保存する場合は、`INFO`の値を適用する必要があります。

* `<rollingFrequency>`  `rollingFrequency` ログファイルを *ロールする頻度を指定します*。*`Rolling`* は、新しいログファイルをアクティブなログとして指定するプロセスです。したがって、以前にアクティブだったログファイルは変更できなくなり、*`rolled`*&#x200B;と見なされます。 相対間隔は、`MINUTELY`、`HOURLY`、`TWICE-DAILY`、`DAILY`、`WEEKLY`、`MONTHLY`、または`NEVER`に設定できます。

パフォーマンスを最適化する方法のヒントについては、*コンテンツ保護用のAdobe PrimetimeDRM SDKの使用*&#x200B;を参照してください。