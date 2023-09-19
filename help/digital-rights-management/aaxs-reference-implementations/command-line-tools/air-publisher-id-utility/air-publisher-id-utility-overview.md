---
title: AIR Publisher ID ユーティリティの概要
description: AIR Publisher ID ユーティリティの概要
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---

# AIR Publisher ID ユーティリティの概要 {#air-publisher-id-utility-overview}

AIRファイルを構築するプロセスの一環として、AIR Developer Tool(ADT) は Publisher ID を生成します。 これは、AIRファイルの作成に使用される証明書に固有の識別子です。 複数のAIRアプリケーションで同じ証明書を再利用する場合、同じ Publisher ID が割り当てられます。AIR Publisher ID ユーティリティは、AIRアプリケーションの Publisher ID の計算に使用されます。 1.5.2 以降のAIRリリースでは、生成された Publisher ID はファイルに書き込まれないので、AIRアプリケーション許可リストを使用している場合は、このツールを使用して Publisher ID を特定する必要があります。

>[!NOTE]
>
>AIR許可リストの適用に使用される Publisher ID は、アプリケーションのの [!DNL application.xml] ファイル。
