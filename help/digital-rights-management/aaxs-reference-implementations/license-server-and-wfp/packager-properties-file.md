---
title: Packagerのプロパティファイル
description: Packagerのプロパティファイル
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---


# Packagerのプロパティファイル{#packager-properties-file}

[!DNL flashaccess-refimpl-packager.properties]ファイルを使用して、参照実装のWatched Folder Packagerコンポーネントを設定します。 少なくとも、ライセンスサーバーのURL、ライセンスサーバー証明書、Packagerの資格情報、およびキー保護オプションを設定してください。 このファイルには、各監視フォルダー(packager.watchfolder.source)の場所も含まれています。 `n`)をクリックします。このプロパティファイルの値に対して行った変更は、次回監視フォルダーパッケージャーを実行したときに有効になります（サーバーの再起動は不要です）。 ただし、パッケージャーで設定エラーが発生した場合は、監視フォルダーパッケージャーのスレッドが終了し、サーバーを再起動してパッケージャーのスレッドを再起動する必要があります。
