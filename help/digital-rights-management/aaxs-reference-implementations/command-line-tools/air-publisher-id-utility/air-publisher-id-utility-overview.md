---
title: AIR Publisher IDユーティリティの概要
description: AIR Publisher IDユーティリティの概要
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---


# AIRパブリッシャーIDユーティリティの概要{#air-publisher-id-utility-overview}

AIRファイルの構築プロセスの一環として、AIR Developer Tool(ADT)は発行者IDを生成します。 これは、AIRファイルの構築に使用される証明書に固有の識別子です。 同じ証明書を複数のAIRアプリケーションに再利用する場合、同じ発行者IDが割り当てられます。AIR発行者IDユーティリティは、AIRアプリケーションの発行者IDを計算するために使用されます。 1.5.2より後のAIRリリースでは、生成された発行者IDはファイルに書き込まれないので、AIRアプリケーション許可リストを使用している場合は、このツールを使用して発行者IDを特定する必要があります。

>[!NOTE]
>
>AIR許可リストの適用に使用されるPublisher IDは、アプリケーションの[!DNL application.xml]ファイル内のアプリケーションの発行者が指定したPublisher IDとは異なります。
