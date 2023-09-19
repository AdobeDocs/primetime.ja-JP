---
title: DRM クライアントとランタイムの資格情報の取り消し
description: DRM クライアントとランタイムの資格情報の取り消し
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# DRM クライアントとランタイムの資格情報の取り消し {#revoking-drm-client-and-runtime-credentials}

DRM/Runtime のバージョンは、セキュリティレベル、バージョン番号、およびオペレーティングシステムやランタイムなどのその他の属性で識別されます。 DRM/ランタイムのバージョンを許可する制限を設定するには、DRM ポリシーまたは `HandlerConfiguration`. モジュールの制限には、最低限のセキュリティレベルと、ライセンスの発行が許可されていないモジュールバージョンのリストが含まれる場合があります。

詳しくは、 [保護されたコンテンツへのアクセスが制限された DRM クライアントのブロックリスト](../../protecting-content/introduction/usage-rules/runtime-application-restrictions/blocklist-drm-clients.md) DRM/Runtime モジュールの識別に使用する属性の詳細。

最小セキュリティレベルが設定されている場合、クライアント上のバージョン（マシントークンで指定）は、指定された値以上である必要があります。

除外されたバージョンのリストが指定され、クライアントのバージョンがリスト内のバージョン識別子のいずれかと一致する場合、クライアントはこの ModuleRequirements インスタンスを含む権限を使用できません。 モジュールがバージョン情報を照合するには、バージョン情報で指定されたすべてのパラメータ（リリースバージョンを除く）が、モジュールの値と完全に一致する必要があります。 クライアントモジュールの値がバージョン情報の値以下の場合、リリースバージョンは一致します。

特定の DRM クライアントまたはランタイムバージョンで違反が報告された場合、コンテンツ所有者とコンテンツ配信者（ライセンスサーバーを実行する）は、Adobeが修正を受けられない期間にライセンスの発行を拒否するように設定できます。 これは、 `HandlerConfiguration` 前述のように、またはすべての DRM ポリシーを変更することで、または変更を加えることができます。 後者の場合は、DRM ポリシーの更新リストを維持し、それを使用して DRM ポリシーが更新されたか取り消されたかを確認できます。

AdobeFlash Player/Adobe AIR Runtime またはAdobeコンテンツ保護ライブラリ（DRM モジュール）の新しいバージョンが必要な場合は、DRM ポリシーを更新する必要があります。

詳しくは、 [Java API を使用したポリシーの更新](../../protecting-content/working-policies-overview/updating-policy-using-java-api.md).

次に、DRM ポリシーの更新リストを作成するか、 `HandlerConfiguration` 呼び出しによって `HandlerConfiguration.setRuntimeModuleRequirements()` または `HandlerConfiguration.setDRMModuleRequirements()`. 指定したブロックリストが有効な新しいライセンスをユーザーが要求する場合は、ライセンスを発行する前に、最新のランタイムとライブラリをインストールする必要があります。

詳しくは、 [Java API を使用したポリシーの更新 DRM およびランタイムバージョンのブロックリストの例](../../protecting-content/working-policies-overview/updating-policy-using-java-api.md) を参照してください。
