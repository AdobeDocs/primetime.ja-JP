---
seo-title: DRMクライアントとランタイム秘密鍵証明書の失効
title: DRMクライアントとランタイム秘密鍵証明書の失効
uuid: 774b8ac7-51bb-42fc-a05d-cfa718e24a81
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# DRMクライアントとランタイム秘密鍵証明書の失効{#revoking-drm-client-and-runtime-credentials}

DRM/Runtimeのバージョンは、セキュリティレベル、バージョン番号、およびOSやランタイムなどのその他の属性で識別されます。 DRM/Runtimeの許可されるバージョンを制限するには、ポリシーまたは `HandlerConfiguration`モジュールの制限には、最小のセキュリティレベルと、ライセンスの発行が許可されないモジュールバージョンのリストが含まれる場合があります。 DRM/Runtimeモジ [ュールの識別に使用される属性の詳細については、「保護されたコンテンツに](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-runtime-application-restrictions/content-blacklist-drm-clients.md) 、DRMクライアントのアクセスが制限されたブラックリスト」を参照してください。

最小セキュリティレベルが設定されている場合、クライアント上のバージョン（マシントークンで指定）は、指定した値以上である必要があります。

除外されたバージョンのリストが指定され、クライアントのバージョンがリスト内のいずれかのバージョン識別子と一致する場合、クライアントはこのModuleRequirementsインスタンスを含む権限を使用できません。 モジュールがバージョン情報と一致するには、リリースバージョンを除き、バージョン情報で指定されたすべてのパラメーターが、モジュールの値と完全に一致する必要があります。 クライアントモジュールの値がバージョン情報の値以下の場合、リリースバージョンが一致します。

特定のDRMクライアントまたはランタイムバージョンに違反が報告された場合、コンテンツ所有者とコンテンツ配布者（ライセンスサーバーを実行する）は、アドビが修正を行っていない期間中にライセンスの発行を拒否するようにサーバーを設定できます。 これは、上で説明したように、ま `HandlerConfiguration` たはすべてのポリシーに変更を加えることで設定できます。 後者の場合は、ポリシー更新リストを維持し、それを使用してポリシーが更新されたか失効したかを確認できます。

新しいバージョンのAdobe® Flash® Player/Adobe® AIR® RuntimeまたはAdobe Content Protectionライブラリ（DRMモジュール）が必要な場合は、「Java APIを使用したポリシーの更新」に示すようにポリシーを更新するか、またはを呼び出して [、ポリシー更新リストを設定しま](../../aaxs-protecting-content/content-working-with-policies/content-updating-policy-using-java-api.md)`HandlerConfiguration``HandlerConfiguration.setRuntimeModuleRequirements()``HandlerConfiguration.setDRMModuleRequirements()`す。 これらのブラックリストを有効にして新しいライセンスを要求する場合、ライセンスを発行する前に、新しいランタイムとライブラリをインストールする必要があります。 DRMバージョンとランタイムバージョンのブラックリストの例については、「Java APIを使用したポリシーの更 [新」のサンプルコードを参照してくださ](../../aaxs-protecting-content/content-working-with-policies/content-updating-policy-using-java-api.md)い。
