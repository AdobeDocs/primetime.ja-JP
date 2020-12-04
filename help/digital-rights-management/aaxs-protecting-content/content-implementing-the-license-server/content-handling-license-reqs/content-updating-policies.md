---
seo-title: ポリシーの更新
title: ポリシーの更新
uuid: f6686c8b-bedf-4ec5-a14e-f03326519f89
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---


# ポリシーの更新{#updating-policies}

コンテンツのパッケージ化後にポリシーが更新される場合は、更新されたポリシーをライセンスサーバーに提供して、ライセンスの発行時に更新されたバージョンを使用できるようにします。 ライセンスサーバーがポリシーを保存するデータベースにアクセスできる場合は、更新されたポリシーをデータベースから取得し、`LicenseRequestMessage.setSelectedPolicy()`を呼び出してポリシーの新しいバージョンを提供できます。

中央データベースに依存しないライセンスサーバーの場合、SDKはポリシー更新リストをサポートします。 ポリシー更新リストは、更新または失効したポリシーのリストを含むファイルです。 ポリシーを更新したら、新しいポリシー更新リストを生成し、定期的にリストをすべてのライセンスサーバーにプッシュします。 `HandlerConfiguration.setPolicyUpdateList()`を設定して、リストをSDKに渡します。 更新リストが指定されている場合、SDKは、コンテンツメタデータを解析する際に、このリストを問い合わせます。 `ContentInfo.getUpdatedPolicies()` メタデータで指定されている、更新されたポリシーのバージョンが含まれます。

「[ポリシー](../../../aaxs-protecting-content/content-working-with-policies/content-working-with-policies-overview.md)と[ポリシー更新リストの使用」を参照してください。](/help/digital-rights-management/protecting-content/working-policies-overview/policy-update-lists/working-with-policy-update-lists.md)
