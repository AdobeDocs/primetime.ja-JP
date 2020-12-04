---
seo-title: DRMポリシーの更新
title: DRMポリシーの更新
uuid: 6f7a1432-88e4-499b-a008-6c8cf0e9c09b
translation-type: tm+mt
source-git-commit: d5986e9bc8689bf37abdf242a41aea5e768df754
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---


# DRMポリシー{#updating-drm-policies}を更新しています

コンテンツをパッケージ化した後にDRMポリシーを更新する場合は、更新したDRMポリシーをライセンスサーバーに提供して、更新したバージョンをライセンスの発行時に使用できるようにします。 ライセンスサーバーがDRMポリシーを保存するデータベースにアクセスできる場合、更新されたDRMポリシーをデータベースから取得し、`LicenseRequestMessage.setSelectedPolicy()`を呼び出してDRMポリシーの新しいバージョンを提供できます。

中央データベースに依存しないライセンスサーバーの場合、SDKはDRMポリシーの更新リストをサポートします。 DRMポリシーの更新リストは、更新または失効したDRMポリシーのリストを含むファイルです。 DRMポリシーが更新されたら、新しいDRMポリシー更新リストを生成し、定期的にすべてのライセンスサーバーにリストをプッシュします。 `HandlerConfiguration.setPolicyUpdateList()`を設定して、リストをSDKに渡します。 更新リストが指定されている場合、SDKは、コンテンツのメタデータを解析する際に、このリストを問い合わせます。 `ContentInfo.getUpdatedPolicies()` メタデータで指定された更新されたDRMポリシーのバージョンが含まれます。

[DRMポリシーの操作](../../../protecting-content/working-policies-overview/working-with-policies.md)および[DRMポリシーの更新リスト](../../../protecting-content/working-policies-overview/policy-update-lists/working-with-policy-update-lists.md)を参照してください。