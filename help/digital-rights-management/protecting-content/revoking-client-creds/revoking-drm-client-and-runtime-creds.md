---
seo-title: DRMクライアントとランタイム秘密鍵証明書の失効
title: DRMクライアントとランタイム秘密鍵証明書の失効
uuid: 8e36536a-8eed-4d27-8a5f-8d3219817e57
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# DRMクライアントとランタイム秘密鍵証明書の失効 {#revoking-drm-client-and-runtime-credentials}

DRM/Runtimeのバージョンは、セキュリティレベル、バージョン番号、およびオペレーティングシステムやランタイムを含むその他の属性で識別されます。 DRM/Runtimeの許可されるバージョンを制限するには、DRMポリシーまたは `HandlerConfiguration`モジュールの制限には、最小のセキュリティレベルと、ライセンスの発行が許可されないモジュールバージョンのリストが含まれる場合があります。

DRM/Runtimeモジ [ュールの識別に使用される属性の詳細については、「保護されたコンテンツに](../../protecting-content/introduction/usage-rules/runtime-application-restrictions/blacklist-drm-clients.md) DRMクライアントがアクセスできないように制限されたDRMクライアントのブラックリスト」を参照してください。

最小セキュリティレベルが設定されている場合、クライアント上のバージョン（マシントークンで指定）は、指定した値以上である必要があります。

除外されたバージョンのリストが指定され、クライアントのバージョンがリスト内のいずれかのバージョン識別子と一致する場合、クライアントはこのModuleRequirementsインスタンスを含む権限を使用できません。 モジュールがバージョン情報と一致するには、リリースバージョンを除き、バージョン情報で指定されたすべてのパラメーターが、モジュールの値と完全に一致する必要があります。 クライアントモジュールの値がバージョン情報の値以下の場合、リリースバージョンが一致します。

特定のDRMクライアントまたはランタイムバージョンに違反が報告された場合、コンテンツ所有者とコンテンツ配布者（ライセンスサーバーを実行する）は、アドビが修正を行っていない期間中にライセンスの発行を拒否するようにサーバーを設定できます。 これは、上記の説明に従って、ま `HandlerConfiguration` たはすべてのDRMポリシーを変更することで設定できます。 後者の場合は、DRMポリシーの更新リストを維持し、それを使用してDRMポリシーが更新されたか取り消されたかを確認できます。

新しいバージョンのAdobe Flash Player/Adobe AIR RuntimeまたはAdobe Content Protectionライブラリ（DRMモジュール）が必要な場合は、DRMポリシーを更新する必要があります。

Java APIを使 [用したポリシーの更新を参照してください](../../protecting-content/working-policies-overview/updating-policy-using-java-api.md)。

次に、またはを呼び出して、DRMポリシー更新リストを作成するか、制限を設 `HandlerConfiguration` 定する必要が `HandlerConfiguration.setRuntimeModuleRequirements()` ありま `HandlerConfiguration.setDRMModuleRequirements()`す。 指定したブラックリストが有効な新しいライセンスをユーザーが要求する場合は、ライセンスを発行する前に最新のランタイムとライブラリをインストールする必要があります。

DRMのブラックリストおよびランタイムバージ [ョンのブラックリストの例については、](../../protecting-content/working-policies-overview/updating-policy-using-java-api.md) Java APIを使用したポリシーの更新を参照してください。DRMのブラックリストおよびランタイムバージョンの例を参照してください。
