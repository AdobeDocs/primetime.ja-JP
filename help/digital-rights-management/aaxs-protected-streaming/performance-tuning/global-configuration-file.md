---
title: グローバル設定ファイル
description: グローバル設定ファイル
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---


# グローバル構成ファイル{#global-configuration-file}

パフォーマンスに対する最大の影響は、グローバル設定ファイルflashaccess-global.xmlの設定を使用することです。 これらの設定には、`<Caching>`要素と`<Logging>`要素が含まれます。

* `<Caching>` この `<Caching>` 要素は、メモリ内の設定ファイルのキャッシュを制御します。`<Caching>`要素の構文は次のとおりです。

   ```
   <Caching refreshDelaySeconds="..." numTenants="..."/>
   ```

   * `refreshDelaySeconds` サーバーが設定ファイルの更新をチェックする頻度を制御します。`refreshDelaySeconds`の値を小さくするとパフォーマンスが低下し、大きくするとパフォーマンスが向上します。 `refreshDelaySeconds`の詳細については、「[設定ファイルの更新](../../aaxs-protected-streaming/updating-configuration-files/updating-configuration-files-overview.md)」を参照してください。

   * `numTenants` テナント数を指定します。テナントの数より少ない値は、残りのテナントへの要求によってキャッシュのミスが発生するので、パフォーマンスに影響する可能性があります。 設定データのキャッシュミスはパフォーマンスに悪影響を与えます。 そのため、Adobeでは、考慮すべきメモリ制限がない限り、サーバーに設定されているテナント数よりも大きい値を設定することをお勧めします。

* `<Logging>` この `<Logging>` 要素は、ログレベルと、ログファイルをロールする頻度を指定します。`<Logging>`要素の構文は次のとおりです。

   ```
   <Logging level="..." rollingFrequency=""/>
   ```

   * `level` ログに記録するメッセージを指定します。「DEBUG」の値を指定すると、多くのログメッセージが生成され、パフォーマンスに悪影響を与える可能性があります。 Adobeでは、最適なパフォーマンスを得るために「WARN」の設定を推奨しています。 ただし、この値によって、ライセンス監査などの重要なランタイム情報が失われるリスクがあります。 パフォーマンスへの影響を最小限に抑えながら、貴重なログ情報を保持するには、「INFO」の値を使用します。
   * `rollingFrequency` ログファイルを *ロールする頻度を指定します*。ローリングとは、新しいログファイルがアクティブなログになる処理です。以前アクティブだったログファイルは、書き込まれず、ロールされたと見なされます。 周期間隔は、「MINUTELY」、「HOURLY」、「TWY-DAILY」、「DAILY」、「WEEKLY」、「MONTHLY」または「NEVER」に設定できます。

パフォーマンスの最適化に関するその他のヒントについては、*AdobeアクセスSDKを使用したコンテンツの保護*&#x200B;を参照してください。
