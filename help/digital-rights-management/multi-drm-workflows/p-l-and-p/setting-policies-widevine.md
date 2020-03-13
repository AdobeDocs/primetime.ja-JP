---
seo-title: Output Protectionポリシーの使用
title: Output Protectionポリシーの使用
uuid: f00d2a97-0036-41a6-ab44-391cc40b146e
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Output Protectionポリシーの使用{#using-output-protection-policies}

**Widevineの出力保護ポリシー**

Widevineは、アナログ出力保護とデジタル出力保護の両方の制限をネイティブにサポートしています。 これらのポリシーを生成されたライセンスにアタッチする方法については、Widevineサービスプロバイダーのドキュメントを参照してください。

WidevineサービスプロバイダーとしてExpressplayを使用する場合は、hdcpOutputControlフラグを使用して、トークン生成時にデジタル出力保護ポリシーをアタッチします。指定できる値は0、1、2です。0はHDCP_NONE、1はHDCP_V1、2はHDCP_V2です。 HDCP_V1とHDCP_V2の両方で、それぞれHDCPバージョン1.Xと2.Xが適用されます。

現在、Expressplayはアナログ出力の制限のアタッチをサポートしていません

**PlayReady出力保護ポリシー**

また、PlayReadyは、アナログ出力保護とデジタル出力保護の両方の制限をネイティブでサポートしています。 設定できる出力保護レベルの値。 「 [Output Protection Levels](https://msdn.microsoft.com/en-us/library/dn468831.aspx) 」ページには、設定できる値と、クライアントの期待される動作が記載されています。

Expressplayを使用する場合は、compressedDigitalAudioOPL、uncompressedDigitalAudioOPL、compressedDigitalVideoOPL、uncompressedDigitalVideoOPLおよびunknownOutputBehaviorフラグを使用して、トークン生成時に出力保護レベルの値を添付します。 これらは、 [PlayReadyライセンストークンリクエストでドキュメント化されます](https://www.expressplay.com/developer/restapi/#playready-license-token-request)
