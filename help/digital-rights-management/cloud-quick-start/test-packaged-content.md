---
seo-title: パッケージ化されたコンテンツのテスト
title: パッケージ化されたコンテンツのテスト
uuid: 99df417a-85ce-45da-bfcf-33df2197bf5b
translation-type: tm+mt
source-git-commit: b7f52b71bde1d7bf59ef51d4f6f90dfaa07e347b
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 0%

---


# パッケージ化されたコンテンツをテスト{#test-the-packaged-content}

(Flash Player経由で)一般公開されているAdobe Primetimeデスクトッププレイヤーを使用して、パッケージ化処理が成功したことを検証する必要があります。 このプレイヤーは、HDSコンテンツのみをサポートできます。 HLSコンテンツをテストするには、Primetime Browser TVSDK対応のプレイヤーが必要です。

1. コンテンツをWebサーバー上でホストします。
1. https://drmtest2.adobe.com:8080/AccessPlayer/player.htmlでPrimetime DRM(旧称「Adobeアクセス」)プレイヤーを起動します。
1. HDSマニフェスト([!DNL .f4m])へのURLをプレイヤーのナビゲーションフィールドに貼り付け、**[!UICONTROL Play]**&#x200B;ボタンをクリックします。
