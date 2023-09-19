---
title: DRM ポリシーの更新
description: DRM ポリシーの更新
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# DRM ポリシーの更新 {#updating-drm-policies}

コンテンツをパッケージ化した後に DRM ポリシーが更新された場合は、更新された DRM ポリシーをライセンスサーバーに提供して、ライセンスの発行時に更新されたバージョンを使用できるようにします。 ライセンスサーバーが DRM ポリシーを保存するためのデータベースにアクセスできる場合、更新された DRM ポリシーをデータベースから取得し、を呼び出すことができます `LicenseRequestMessage.setSelectedPolicy()` を使用して、DRM ポリシーの新しいバージョンを指定します。

中央のデータベースに依存しないライセンスサーバーの場合、SDK は DRM ポリシー更新リストをサポートします。 DRM ポリシー更新リストは、更新または取り消された DRM ポリシーのリストを含むファイルです。 DRM ポリシーが更新されたら、新しい DRM ポリシー更新リストを生成し、定期的にすべてのライセンスサーバーにリストをプッシュします。 を設定して、リストを SDK に渡します。 `HandlerConfiguration.setPolicyUpdateList()`. 更新リストが指定されている場合、SDK は、コンテンツメタデータを解析する際に、このリストを調べます。 `ContentInfo.getUpdatedPolicies()` メタデータで指定されている更新済みバージョンの DRM ポリシーが含まれます。

詳しくは、 [DRM ポリシーの操作](../../../protecting-content/working-policies-overview/working-with-policies.md) および [DRM ポリシーの更新リスト](../../../protecting-content/working-policies-overview/policy-update-lists/working-with-policy-update-lists.md)
