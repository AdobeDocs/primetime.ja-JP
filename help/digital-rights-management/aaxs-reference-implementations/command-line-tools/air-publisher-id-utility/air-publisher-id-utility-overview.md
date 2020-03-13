---
seo-title: AIR発行者IDユーティリティの概要
title: AIR発行者IDユーティリティの概要
uuid: 31aecc0e-ad9b-43ad-ba58-77d2c999f4a4
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# AIR発行者IDユーティリティの概要 {#air-publisher-id-utility-overview}

AIRファイルの構築プロセスの一環として、AIR開発者ツール(ADT)で発行者IDが生成されます。 これは、AIRファイルの構築に使用される証明書に固有の識別子です。 同じ証明書を複数のAIRアプリケーションに再利用する場合、同じ発行者IDが使用されます。AIR発行者IDユーティリティは、AIRアプリケーションの発行者IDを計算するために使用されます。 1.5.2より後のAIRリリースでは、生成された発行者IDはファイルに書き込まれないので、AIRアプリケーションのホワイトリストを使用している場合は、このツールを使用して発行者IDを特定する必要があります。

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>AIRホワイトリストの適用に使用される発行者IDは、アプリケーションのファイルでアプリケーションの発行者が指定する発行者IDとは異な [!DNL application.xml] ります。

