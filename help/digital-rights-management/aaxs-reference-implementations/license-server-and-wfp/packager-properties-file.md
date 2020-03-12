---
seo-title: Packagerプロパティファイル
title: Packagerプロパティファイル
uuid: 156624ec-66f0-4718-8a66-ed04a47f234d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Packagerプロパティファイル {#packager-properties-file}

このファイルを [!DNL flashaccess-refimpl-packager.properties] 使用して、参照実装の監視フォルダーパッケージャーコンポーネントを設定します。 少なくとも、ライセンスサーバーのURL、ライセンスサーバー証明書、パッケージャーの秘密鍵証明書、および鍵の保護オプションを必ず設定してください。 このファイルには、各監視フォルダー(packager.watchfolder.source)の場所も含まれます。 `n`). このプロパティファイルの値に対する変更は、次回監視フォルダーパッケージャーを実行したときに有効になります（サーバーの再起動は不要です）。 ただし、Packagerに設定エラーが発生した場合は、監視フォルダーのPackagerスレッドが終了し、Packagerスレッドを再起動するには、サーバーを再起動する必要があります。
