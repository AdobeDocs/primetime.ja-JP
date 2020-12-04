---
seo-title: Packagerのプロパティファイル
title: Packagerのプロパティファイル
uuid: 156624ec-66f0-4718-8a66-ed04a47f234d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---


# Packagerのプロパティファイル{#packager-properties-file}

[!DNL flashaccess-refimpl-packager.properties]ファイルを使用して、参照実装のWatched Folder Packagerコンポーネントを設定します。 少なくとも、ライセンスサーバーのURL、ライセンスサーバー証明書、Packagerの資格情報、およびキー保護オプションを設定してください。 このファイルには、各監視フォルダー(packager.watchfolder.source)の場所も含まれています。 `n`)をクリックします。このプロパティファイルの値に対して行った変更は、次回監視フォルダーパッケージャーを実行したときに有効になります（サーバーの再起動は不要です）。 ただし、パッケージャーで設定エラーが発生した場合は、監視フォルダーパッケージャーのスレッドが終了し、サーバーを再起動してパッケージャーのスレッドを再起動する必要があります。
