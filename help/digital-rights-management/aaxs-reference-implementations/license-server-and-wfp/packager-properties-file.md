---
title: Packager プロパティファイル
description: Packager プロパティファイル
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---

# Packager プロパティファイル {#packager-properties-file}

以下を使用します。 [!DNL flashaccess-refimpl-packager.properties] ファイルを参照実装の監視フォルダーパッケージャコンポーネントを設定します。 少なくとも、ライセンスサーバーの URL、ライセンスサーバーの証明書、パッケージャの資格情報、および鍵の保護オプションを必ず設定してください。 このファイルには、各監視フォルダー (packager.watchfolder.source) の場所も含まれています。 `n`). このプロパティファイルの値に加えた変更は、次回監視フォルダーパッケージャが実行されたときに有効になります（サーバーを再起動する必要はありません）。 ただし、パッケージャーに設定エラーが発生した場合は、監視フォルダーパッケージャーのスレッドが終了し、パッケージャーのスレッドを再起動するには、サーバーを再起動する必要があります。
