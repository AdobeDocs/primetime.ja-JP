---
title: グローバル設定ファイル
description: グローバル設定ファイル
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# グローバル設定ファイル{#global-configuration-file}

パフォーマンスに与える最大の影響は、グローバル設定ファイル flashaccess-global.xml の設定を使用することです。 これらの設定には、 `<Caching>` および `<Logging>` 要素。

* `<Caching>` The `<Caching>` 要素は、メモリ内の設定ファイルのキャッシュを制御します。 The `<Caching>` 要素の構文は次のとおりです。

  ```
  <Caching refreshDelaySeconds="..." numTenants="..."/>
  ```

   * `refreshDelaySeconds` は、サーバが構成ファイルの更新を確認する頻度を制御します。 の低い値： `refreshDelaySeconds` パフォーマンスに悪影響を与えますが、値を大きくするとパフォーマンスが向上します。 詳しくは、 `refreshDelaySeconds`を参照してください。[設定ファイルの更新](../../aaxs-protected-streaming/updating-configuration-files/updating-configuration-files-overview.md)&quot;.

   * `numTenants` テナント数を指定します。 残りのテナントに対する要求によってキャッシュミスが発生するので、テナント数よりも少ない値は、パフォーマンスに影響を与える可能性が高くなります。 設定データのキャッシュミスは、パフォーマンスに悪影響を与えます。 そのため、Adobeでは、考慮すべきメモリ制限がない限り、サーバーに対して設定されたテナント数よりも大きい値を設定することをお勧めします。

* `<Logging>` The `<Logging>` element は、ログレベルとログファイルのロール頻度を指定します。 The `<Logging>` 要素の構文は次のとおりです。

  ```
  <Logging level="..." rollingFrequency=""/>
  ```

   * `level` ログに記録するメッセージを指定します。 値「DEBUG」を指定すると、多くのログメッセージが生成され、パフォーマンスに悪影響を与える可能性があります。 Adobeでは、最適なパフォーマンスを得るために、「WARN」の設定をお勧めします。 ただし、その価値は、ライセンス監査などの重要なランタイム情報を失うリスクを伴います。 パフォーマンスへの影響を最小限に抑えて貴重なログ情報を保持するには、「INFO」の値を使用します。
   * `rollingFrequency` ログファイルの頻度を指定します。 *ロール*. ローリングとは、新しいログファイルがアクティブログになるプロセスですが、以前アクティブだったログファイルは書き込まれず、ロール済みと見なされます。 周期は、「MINUTELY」、「HOURLY」、「TWICE-DAILY」、「DAILY」、「WEEKLY」、「MONTHLY」または「NEVER」に設定できます。

詳しくは、 *コンテンツの保護にAdobeアクセス SDK を使用する* パフォーマンスの最適化に関するその他のヒント
