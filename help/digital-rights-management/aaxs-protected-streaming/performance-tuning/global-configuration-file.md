---
seo-title: グローバル設定ファイル
title: グローバル設定ファイル
uuid: 48c45f56-55c2-4526-b854-5552caf21541
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# グローバル設定ファイル{#global-configuration-file}

パフォーマンスに最も大きな影響を与えるのは、グローバル設定ファイルflashaccess-global.xmlの設定を使用することです。 これらの設定には、要素と要素 `<Caching>` が含ま `<Logging>` れます。

* `<Caching>` この要素 `<Caching>` は、メモリ内の設定ファイルのキャッシュを制御します。 要素の `<Caching>` 構文は次のとおりです。

   ```
   <Caching refreshDelaySeconds="..." numTenants="..."/>
   ```

   * `refreshDelaySeconds` サーバーが設定ファイルの更新をチェックする頻度を制御します。 値を小さくするとパフォーマン `refreshDelaySeconds` スに悪影響を与え、値を大きくするとパフォーマンスが向上します。 詳しくは、「設定ファ `refreshDelaySeconds`イルの更[新](../../aaxs-protected-streaming/updating-configuration-files/updating-configuration-files-overview.md)」を参照してください。

   * `numTenants` テナントの数を指定します。 残りのテナントに対する要求はキャッシュミスを引き起こすので、テナント数より少ない値はパフォーマンスに影響する可能性が高くなります。 設定データのキャッシュミスはパフォーマンスに悪影響を与えます。 したがって、考慮する必要のあるメモリ制限がない限り、この値はサーバーに対して設定されているテナント数よりも大きい値に設定することをお勧めします。

* `<Logging>` この要 `<Logging>` 素は、ログレベルと、ログファイルをロールする頻度を指定します。 要素の `<Logging>` 構文は次のとおりです。

   ```
   <Logging level="..." rollingFrequency=""/>
   ```

   * `level` ログに記録するメッセージを指定します。 「DEBUG」の値を指定すると、多くのログメッセージが生成され、パフォーマンスに悪影響を与える可能性があります。 最適なパフォーマンスを得るために、「WARN」を設定することをお勧めします。 ただし、この値によって、ライセンス監査などの重要な実行時情報が失われるリスクはあります。 パフォーマンスへの影響を最小限に抑えて貴重なログ情報を保持するには、「INFO」の値を使用します。
   * `rollingFrequency` ログファイルをロールする頻度を指定 *します*。 ローリングとは、新しいログファイルがアクティブなログになるプロセスです。以前にアクティブだったログファイルは、書き込まれず、ロールされたと見なされます。 周期間隔は、「MINUTELY」、「HOURLY」、「TWOYS-DAILY」、「DAILY」、「WEEKLY」、「MONTHLY」または「NEVER」に設定できます。

パフォ *ーマンスの最適化に関するその他のヒントについては、「Adobe Access SDKを使用した* Protecting Content」を参照してください。
