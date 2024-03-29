---
title: 監視フォルダーのプロパティ
description: 監視フォルダーのプロパティ
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# 監視フォルダーのプロパティ {#watched-folder-properties}

各監視フォルダーには、 [!DNL properties/watchfolder.properties]. このファイルには、暗号化する内容や適用するポリシーなど、このフォルダーに配置されたコンテンツのパッケージ化オプションが含まれています。 プロパティファイルの値に加えた変更は、次回監視フォルダーパッケージャーが実行されたときに有効になります（サーバーを再起動する必要はありません）。

packager のプロパティファイルに設定エラーが発生すると、packager のスレッドは停止します。 監視フォルダーパッケージャを再開するには、サーバーを再起動します。 監視フォルダーのプロパティファイルに設定エラーが発生した場合、その監視フォルダーは一時的にパッケージャが処理するフォルダーのリストから削除されます。 監視フォルダーをリストに戻すには、サーバーを再起動するか、パッケージャーのプロパティファイルを変更します。 特定のファイルのパッケージ化中にエラーが発生した場合（ファイルが破損しているなど）は、ファイルはスキップされ、フォルダー内の残りのファイルが処理されます。
