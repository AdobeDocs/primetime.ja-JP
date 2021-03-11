---
title: Output Protectionポリシーの使用
description: Output Protectionポリシーの使用
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---


# Output Protectionポリシーの使用{#using-output-protection-policies}

**Widevineの出力保護ポリシー**

Widevineは、アナログ出力保護とデジタル出力保護の両方の制限をネイティブでサポートしています。 生成されたライセンスにこれらのポリシーを適用する方法については、Widevineサービスプロバイダーのドキュメントを参照してください。

WidevineサービスプロバイダーとしてExpressplayを使用する場合は、hdcpOutputControlフラグを使用して、トークン生成時にデジタル出力保護ポリシーをアタッチします。
指定できる値は0、1、2です。0 = HDCP_NONE、1 = HDCP_V1、2 = HDCP_V2です。 HDCP_V1とHDCP_V2はどちらも、それぞれHDCPバージョン1.Xと2.Xを適用します。

Expressplayは、現在、アナログ出力制限のアタッチをサポートしていません

**PlayReady出力保護ポリシー**

PlayReadyでは、アナログ出力保護とデジタル出力保護の両方の制限もネイティブでサポートされています。 設定できる出力保護レベルの値です。 [Output Protection Levels](https://msdn.microsoft.com/en-us/library/dn468831.aspx)ページには、設定できる値と、クライアントの期待される動作がドキュメントされます。

Expressplayを使用する場合は、compressedDigitalAudioOPL、uncompressedDigitalAudioOPL、compressedDigitalVideoOPL、uncompressedDigitalVideoOPLおよびunknownOutputBehaviorフラグを使用して、トークン生成時に出力保護レベル値をアタッチします。 これらは[PlayReadyライセンストークンリクエスト](https://www.expressplay.com/developer/restapi/#playready-license-token-request)に記載されています
