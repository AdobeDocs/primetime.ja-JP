---
seo-title: DRMポリシーの更新
title: DRMポリシーの更新
uuid: 6f7a1432-88e4-499b-a008-6c8cf0e9c09b
translation-type: tm+mt
source-git-commit: d5986e9bc8689bf37abdf242a41aea5e768df754

---


# DRMポリシーの更新 {#updating-drm-policies}

コンテンツのパッケージ化後にDRMポリシーが更新される場合は、更新されたDRMポリシーをライセンスサーバーに提供し、更新されたバージョンをライセンスの発行時に使用できるようにします。 ライセンスサーバーがDRMポリシーを保存するデータベースにアクセスできる場合、更新されたDRMポリシーをデータベースから取得し、DRMポリシーの新しいバージ `LicenseRequestMessage.setSelectedPolicy()` ョンを提供するための呼び出しを行うことができます。

中央データベースに依存しないライセンスサーバーの場合、SDKはDRMポリシー更新リストをサポートします。 DRMポリシー更新リストは、更新または取り消されたDRMポリシーのリストを含むファイルです。 DRMポリシーが更新されたら、新しいDRMポリシー更新リストを生成し、定期的にすべてのライセンスサーバーにリストをプッシュします。 SDKにリストを渡すには、を設定しま `HandlerConfiguration.setPolicyUpdateList()`す。 更新リストが指定されている場合、SDKは、コンテンツのメタデータを解析する際にこのリストを参照します。 `ContentInfo.getUpdatedPolicies()` メタデータで指定されたDRMポリシーの更新バージョンが含まれます。

DRMポリシ [ーおよび](../../../protecting-content/working-policies-overview/working-with-policies.md)[DRMポリシーの更新リストの使用を参照してください。](../../../protecting-content/working-policies-overview/policy-update-lists/working-with-policy-update-lists.md)