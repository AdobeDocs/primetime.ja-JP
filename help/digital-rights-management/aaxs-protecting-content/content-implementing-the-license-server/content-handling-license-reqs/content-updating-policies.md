---
seo-title: ポリシーの更新
title: ポリシーの更新
uuid: f6686c8b-bedf-4ec5-a14e-f03326519f89
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# ポリシーの更新 {#updating-policies}

コンテンツのパッケージ化後にポリシーが更新される場合は、更新されたポリシーをライセンスサーバーに提供し、更新されたバージョンをライセンスの発行時に使用できるようにします。 ライセンスサーバーがポリシーを保存するデータベースにアクセスできる場合は、更新されたポリシーをデータベースから取得し、新しいバージョンのポリシーを提供す `LicenseRequestMessage.setSelectedPolicy()` るための呼び出しを行うことができます。

中央データベースに依存しないライセンスサーバーの場合、SDKはポリシー更新リストをサポートします。 ポリシー更新リストとは、更新または失効したポリシーのリストを含むファイルです。 ポリシーが更新されたら、新しいポリシー更新リストを生成し、定期的にすべてのライセンスサーバーにリストをプッシュします。 SDKにリストを渡すには、を設定しま `HandlerConfiguration.setPolicyUpdateList()`す。 更新リストが指定されている場合、SDKは、コンテンツメタデータの解析時にこのリストを参照します。 `ContentInfo.getUpdatedPolicies()` メタデータで指定されたポリシーの更新バージョンが含まれます。

詳しくは、ポ [リシーおよびポリシーの更新](../../../aaxs-protecting-content/content-working-with-policies/content-working-with-policies-overview.md) リストの [操作を参照してください。](/help/digital-rights-management/protecting-content/working-policies-overview/policy-update-lists/working-with-policy-update-lists.md)
