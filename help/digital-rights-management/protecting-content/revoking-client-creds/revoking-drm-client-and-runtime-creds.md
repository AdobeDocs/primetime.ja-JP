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


# DRMクライアントとランタイム資格情報の失効{#revoking-drm-client-and-runtime-credentials}

DRM/Runtimeのバージョンは、セキュリティレベル、バージョン番号、およびオペレーティングシステムやランタイムなどのその他の属性で識別されます。 DRM/Runtimeのバージョンを許可するには、DRMポリシーまたは`HandlerConfiguration`内にモジュール制限を設定します。 モジュールの制限には、ライセンスの発行が許可されないモジュールバージョンのセキュリティレベルとリストが含まれる場合があります。

DRM/Runtimeモジュールの識別に使用される属性について詳しくは、[保護されたコンテンツ](../../protecting-content/introduction/usage-rules/runtime-application-restrictions/blocklist-drm-clients.md)へのアクセスが制限されたDRMクライアントのブロックリストを参照してください。

最小セキュリティレベルが設定されている場合、クライアント上のバージョン（マシントークンで指定）は、指定された値以上である必要があります。

除外されたバージョンのリストが指定され、クライアントのバージョンがリスト内のバージョン識別子のいずれかと一致する場合、クライアントは、このModuleRequirementsインスタンスを含む権限を使用できません。 モジュールがバージョン情報と一致するには、リリースバージョンを除き、バージョン情報で指定されたすべてのパラメーターが、モジュールの値と完全に一致する必要があります。 クライアントモジュールの値がバージョン情報の値以下の場合は、リリースバージョンが一致します。

イベントでは、特定のDRMクライアントまたはランタイムバージョンに違反が報告され、コンテンツの所有者とコンテンツの配布者（ライセンスサーバーを実行する）は、Adobeに修正が提供されない間、ライセンスの発行を拒否するように設定できます。 これは、上述の`HandlerConfiguration`で設定するか、すべてのDRMポリシーに変更を加えることで設定できます。 後者の場合は、DRMポリシーの更新リストを維持し、それを使用してDRMポリシーが更新されたか失効したかを確認できます。

AdobeFlash Player/Adobe AIRランタイムまたはAdobeコンテンツ保護ライブラリ（DRMモジュール）の新しいバージョンが必要な場合は、DRMポリシーを更新する必要があります。

「[Java APIを使用したポリシーの更新](../../protecting-content/working-policies-overview/updating-policy-using-java-api.md)」を参照してください。

次に、DRMポリシーの更新リストを作成するか、`HandlerConfiguration.setRuntimeModuleRequirements()`または`HandlerConfiguration.setDRMModuleRequirements()`を呼び出して`HandlerConfiguration`に制限を設定する必要があります。 指定したブロックリストが有効な新しいライセンスをユーザーが要求する場合、ライセンスを発行する前に、最新のランタイムとライブラリをインストールする必要があります。

DRMとランタイムバージョンをリストするブロックの例については、[Java APIを使用したポリシーの更新DRMとランタイムバージョンをリストするブロックの例](../../protecting-content/working-policies-overview/updating-policy-using-java-api.md)のサンプルコードを参照してください。
