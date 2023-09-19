---
title: ポリシーの更新
description: ポリシーの更新
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# ポリシーの更新 {#updating-policies}

コンテンツをパッケージ化した後にポリシーを更新する場合は、更新されたポリシーをライセンスサーバーに提供して、ライセンスの発行時に更新されたバージョンを使用できるようにします。 ライセンスサーバーがポリシーを保存するためのデータベースにアクセスできる場合、更新されたポリシーをデータベースから取得し、を呼び出すことができます。 `LicenseRequestMessage.setSelectedPolicy()` ポリシーの新しいバージョンを提供する。

中央のデータベースに依存しないライセンスサーバーの場合、SDK はポリシー更新リストをサポートします。 ポリシー更新リストは、更新または失効したポリシーのリストを含むファイルです。 ポリシーが更新されたら、新しいポリシー更新リストを生成し、定期的にすべてのライセンスサーバにリストをプッシュします。 を設定して、リストを SDK に渡します。 `HandlerConfiguration.setPolicyUpdateList()`. 更新リストが指定された場合、SDK は、コンテンツメタデータを解析する際にこのリストを調べます。 `ContentInfo.getUpdatedPolicies()` メタデータで指定されている、更新されたバージョンのポリシーが含まれます。

詳しくは、 [ポリシーの操作](../../../aaxs-protecting-content/content-working-with-policies/content-working-with-policies-overview.md) および [ポリシー更新リスト。](/help/digital-rights-management/protecting-content/working-policies-overview/policy-update-lists/working-with-policy-update-lists.md)
