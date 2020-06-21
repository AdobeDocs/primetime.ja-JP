---
seo-title: DRMクライアントとランタイム秘密鍵証明書の失効
title: DRMクライアントとランタイム秘密鍵証明書の失効
uuid: 8e36536a-8eed-4d27-8a5f-8d3219817e57
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---


# DRMクライアントとランタイム秘密鍵証明書の失効 {#revoking-drm-client-and-runtime-credentials}

DRM/Runtimeのバージョンは、セキュリティレベル、バージョン番号、およびオペレーティングシステムやランタイムなどのその他の属性で識別されます。 DRM/Runtimeのバージョンを許可する制限を設定するには、DRMポリシーまたは内でモジュールの制限を設定し `HandlerConfiguration`ます。 モジュールの制限には、ライセンスの発行が許可されないモジュールバージョンのセキュリティレベルとリストが含まれる場合があります。

DRM/Runtimeモジュールの識別に使用される属性について詳しくは、「保護されたコンテンツ [(DRMクライアントが保護されたコンテンツにアクセスできないように制限された場合の](../../protecting-content/introduction/usage-rules/runtime-application-restrictions/blocklist-drm-clients.md) ブロックリスト」を参照してください。

最小セキュリティレベルが設定されている場合、クライアント上のバージョン（マシントークンで指定）は、指定された値以上である必要があります。

除外されたバージョンのリストが指定され、クライアントのバージョンがリスト内のバージョン識別子のいずれかと一致する場合、クライアントは、このModuleRequirementsインスタンスを含む権限を使用できません。 モジュールがバージョン情報と一致するには、リリースバージョンを除き、バージョン情報で指定されたすべてのパラメーターが、モジュールの値と完全に一致する必要があります。 クライアントモジュールの値がバージョン情報の値以下の場合は、リリースバージョンが一致します。

特定のDRMクライアントまたはランタイムバージョンに対する違反がイベントで報告されると、コンテンツの所有者とコンテンツの配布者（ライセンスサーバーを実行する）は、アドビが修正を行っていない間にライセンスの発行を拒否するように設定できます。 これは、上記の説明に従って、またはすべてのDRMポリシーに変更を加え `HandlerConfiguration` ることで設定できます。 後者の場合は、DRMポリシーの更新リストを維持し、それを使用してDRMポリシーが更新されたか失効したかを確認できます。

新しいバージョンのAdobe Flash Player/Adobe AIR RuntimeまたはAdobe Content Protectionライブラリ（DRMモジュール）が必要な場合は、DRMポリシーを更新する必要があります。

「Java APIを使用したポリシーの [更新](../../protecting-content/working-policies-overview/updating-policy-using-java-api.md)」を参照してください。

次に、またはを呼び出して、DRMポリシー更新リストを作成するか、で制限を設定する必要があ `HandlerConfiguration` り `HandlerConfiguration.setRuntimeModuleRequirements()``HandlerConfiguration.setDRMModuleRequirements()`ます。 指定したブロックリストが有効な新しいライセンスをユーザーが要求する場合、ライセンスを発行する前に、最新のランタイムとライブラリをインストールする必要があります。

DRMとランタイムバージョンをリストするブロックの例については、Java APIを使用したポリシーの [更新を参照してください。DRMとランタイムバージョンをリストするブロックの例については](../../protecting-content/working-policies-overview/updating-policy-using-java-api.md) 、Java APIを使用したポリシーの更新を参照してください。
