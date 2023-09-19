---
title: パッケージ化されたコンテンツのテスト
description: パッケージ化されたコンテンツのテスト
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 0%

---

# パッケージ化されたコンテンツのテスト {#test-the-packaged-content}

(Flash Playerを介して ) 公開されているAdobe Primetime Desktop Player を使用して、パッケージ化処理が成功したことを検証する必要があります。 このプレーヤーは HDS コンテンツのみをサポートできます。 HLS コンテンツをテストするには、Primetime ブラウザー TVSDK 対応のプレーヤーが必要です。

1. Web サーバー上でコンテンツをホストします。
1. https://drmtest2.adobe.com:8080/AccessPlayer/player.htmlで Primetime DRM( 旧称：Adobeアクセス ) プレーヤーを起動します。
1. URL を HDS マニフェスト ( [!DNL .f4m]) をプレーヤーのナビゲーションフィールドに移動し、 **[!UICONTROL Play]** 」ボタンをクリックします。
