---
seo-title: パッケージ化されたコンテンツのテスト
title: パッケージ化されたコンテンツのテスト
uuid: 99df417a-85ce-45da-bfcf-33df2197bf5b
translation-type: tm+mt
source-git-commit: b7f52b71bde1d7bf59ef51d4f6f90dfaa07e347b

---


# パッケージ化されたコンテンツのテスト {#test-the-packaged-content}

（Flash Playerを介して）公開されているAdobe Primetime Desktop Playerを使用して、パッケージ化操作が成功したことを検証する必要があります。 このプレーヤーはHDSコンテンツのみをサポートできます。 HLSコンテンツをテストするには、Primetime Browser TVSDK対応のプレーヤーが必要です。

1. コンテンツをWebサーバーでホストします。
1. https://drmtest2.adobe.com:8080/AccessPlayer/player.htmlでPrimetime DRM（旧称Adobe Access）プレーヤーを起動します。
1. HDSマニフェスト( [!DNL .f4m])へのURLをプレイヤーのナビゲーションフィールドに貼り付け、ボタンをクリック **[!UICONTROL Play]** します。
