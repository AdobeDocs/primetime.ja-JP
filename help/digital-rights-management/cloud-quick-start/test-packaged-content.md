---
title: パッケージ化されたコンテンツのテスト
description: パッケージ化されたコンテンツのテスト
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 0%

---


# パッケージ化されたコンテンツをテスト{#test-the-packaged-content}

(Flash Player経由で)一般公開されているAdobe Primetimeデスクトッププレイヤーを使用して、パッケージ化処理が成功したことを検証する必要があります。 このプレイヤーは、HDSコンテンツのみをサポートできます。 HLSコンテンツをテストするには、Primetime Browser TVSDK対応のプレイヤーが必要です。

1. コンテンツをWebサーバー上でホストします。
1. https://drmtest2.adobe.com:8080/AccessPlayer/player.htmlでPrimetime DRM(旧称「Adobeアクセス」)プレイヤーを起動します。
1. HDSマニフェスト([!DNL .f4m])へのURLをプレイヤーのナビゲーションフィールドに貼り付け、**[!UICONTROL Play]**&#x200B;ボタンをクリックします。
