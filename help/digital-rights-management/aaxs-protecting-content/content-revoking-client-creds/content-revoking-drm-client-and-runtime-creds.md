---
seo-title: DRMクライアントとランタイム秘密鍵証明書の失効
title: DRMクライアントとランタイム秘密鍵証明書の失効
uuid: 774b8ac7-51bb-42fc-a05d-cfa718e24a81
translation-type: tm+mt
source-git-commit: fbc175f383c850a7286b1e6e89daa027e00b29ef
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---


# DRMクライアントとランタイム資格情報の失効{#revoking-drm-client-and-runtime-credentials}

DRM/Runtimeのバージョンは、セキュリティレベル、バージョン番号、およびOSやランタイムなどのその他の属性で識別されます。 DRM/Runtimeのバージョンを許可するには、ポリシーまたは`HandlerConfiguration`内にモジュール制限を設定します。 モジュールの制限には、ライセンスの発行が許可されないモジュールバージョンのセキュリティレベルとリストが含まれる場合があります。 DRM/Runtimeモジュールの識別に使用される属性について詳しくは、[保護されたコンテンツ](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-runtime-application-restrictions/content-blocklist-drm-clients.md)へのアクセスが制限されたDRMクライアントのブロックリストを参照してください。

最小セキュリティレベルが設定されている場合、クライアント上のバージョン（マシントークンで指定）は、指定された値以上である必要があります。

除外されたバージョンのリストが指定され、クライアントのバージョンがリスト内のバージョン識別子のいずれかと一致する場合、クライアントは、このModuleRequirementsインスタンスを含む権限を使用できません。 モジュールがバージョン情報と一致するには、リリースバージョンを除き、バージョン情報で指定されたすべてのパラメーターが、モジュールの値と完全に一致する必要があります。 クライアントモジュールの値がバージョン情報の値以下の場合は、リリースバージョンが一致します。

イベントでは、特定のDRMクライアントまたはランタイムバージョンに違反が報告され、コンテンツの所有者とコンテンツの配布者（ライセンスサーバーを実行する）は、Adobeに修正が提供されない間、ライセンスの発行を拒否するように設定できます。 これは、前述の`HandlerConfiguration`で設定するか、すべてのポリシーに変更を加えることで設定できます。 後者の場合は、ポリシー更新リストを維持し、それを使用してポリシーが更新されたか失効したかを確認できます。

新しいバージョンのAdobe®Flash® Player/Adobe® AIR®ランタイムまたはAdobeコンテンツ保護ライブラリ（DRMモジュール）が必要な場合は、「[Java API](../../aaxs-protecting-content/content-working-with-policies/content-updating-policy-using-java-api.md)を使用したポリシーの更新」に示すようにポリシーを更新するか、`HandlerConfiguration.setRuntimeModuleRequirements()`または`HandlerConfiguration.setDRMModuleRequirements()`を呼び出して`HandlerConfiguration`に制限を設定します。 ユーザーがこれらのブロックリストを有効にして新しいライセンスを要求する場合、ライセンスを発行する前に、新しいランタイムとライブラリをインストールする必要があります。 DRMバージョンとランタイムバージョンのリストを示すブロックの例については、[Java API](../../aaxs-protecting-content/content-working-with-policies/content-updating-policy-using-java-api.md)を使用したポリシーの更新のサンプルコードを参照してください。
