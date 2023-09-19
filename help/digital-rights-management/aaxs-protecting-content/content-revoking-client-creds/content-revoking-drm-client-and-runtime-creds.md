---
title: DRM クライアントとランタイムの資格情報の取り消し
description: DRM クライアントとランタイムの資格情報の取り消し
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# DRM クライアントとランタイムの資格情報の取り消し{#revoking-drm-client-and-runtime-credentials}

DRM/Runtime のバージョンは、セキュリティレベル、バージョン番号、および OS やランタイムなどのその他の属性で識別されます。 DRM/ランタイムバージョンを許可するには、ポリシーまたは `HandlerConfiguration`. モジュールの制限には、最低限のセキュリティレベルと、ライセンスの発行が許可されていないモジュールバージョンのリストが含まれる場合があります。 詳しくは、 [保護されたコンテンツへのアクセスが制限された DRM クライアントのブロックリスト](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-runtime-application-restrictions/content-blocklist-drm-clients.md) DRM/Runtime モジュールの識別に使用する属性の詳細。

最小セキュリティレベルが設定されている場合、クライアント上のバージョン（マシントークンで指定）は、指定された値以上である必要があります。

除外されたバージョンのリストが指定され、クライアントのバージョンがリスト内のバージョン識別子のいずれかと一致する場合、クライアントはこの ModuleRequirements インスタンスを含む権限を使用できません。 モジュールがバージョン情報を照合するには、バージョン情報で指定されたすべてのパラメータ（リリースバージョンを除く）が、モジュールの値と完全に一致する必要があります。 クライアントモジュールの値がバージョン情報の値以下の場合、リリースバージョンは一致します。

特定の DRM クライアントまたはランタイムバージョンで違反が報告された場合、コンテンツ所有者とコンテンツ配信者（ライセンスサーバーを実行する）は、Adobeが修正を受けられない期間にライセンスの発行を拒否するように設定できます。 これは、 `HandlerConfiguration` 前述のように、またはすべてのポリシーを変更して、 後者の場合は、ポリシーの更新リストを維持し、それを使用して、ポリシーが更新されたか失効したかを確認できます。

新しいバージョンのAdobe®Flash® Player/Adobe® AIR® Runtime またはAdobeコンテンツ保護ライブラリ（DRM モジュール）が必要な場合は、次に示すようにポリシーを更新します。 [Java API を使用したポリシーの更新](../../aaxs-protecting-content/content-working-with-policies/content-updating-policy-using-java-api.md) ポリシー更新リストを作成するか、 `HandlerConfiguration` 呼び出しによって `HandlerConfiguration.setRuntimeModuleRequirements()` または `HandlerConfiguration.setDRMModuleRequirements()`. ユーザーがこれらのブロックリストを有効にして新しいライセンスを要求する場合、ライセンスを発行する前に、新しいランタイムとライブラリをインストールする必要があります。 DRM とランタイムバージョンをリストするブロックの例については、 [Java API を使用したポリシーの更新](../../aaxs-protecting-content/content-working-with-policies/content-updating-policy-using-java-api.md).
