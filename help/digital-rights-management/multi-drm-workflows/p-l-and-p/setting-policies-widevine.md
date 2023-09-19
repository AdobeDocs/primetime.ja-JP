---
title: 出力保護ポリシーの使用
description: 出力保護ポリシーの使用
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# 出力保護ポリシーの使用{#using-output-protection-policies}

**Widevine の出力保護ポリシー**

Widevine は、アナログとデジタルの両方の出力保護制限をネイティブにサポートしています。 生成されたライセンスにこれらのポリシーを添付する方法については、Widevine サービスプロバイダーのドキュメントを参照してください。

Widevine サービスプロバイダーとして Expressplay を使用する場合、hdcpOutputControl フラグを使用して、トークン生成時にデジタル出力保護ポリシーを添付します。使用できる値は、0、1、2 です。 0 = HDCP_NONE、1 = HDCP_V1、2 = HDCP_V2 です。 HDCP_V1 と HDCP_V2 の両方で、それぞれ HDCP バージョン 1.X と 2.X が適用されます。

Expressplay は、現在、アナログ出力制限のアタッチをサポートしていません

**PlayReady 出力保護ポリシー**

PlayReady は、アナログとデジタルの両方の出力保護制限もネイティブにサポートしています。 設定可能な出力保護レベルの値です。 ページ [出力保護レベル](https://msdn.microsoft.com/en-us/library/dn468831.aspx) には、設定できる値と、クライアントの期待される動作が記載されています。

Expressplay を使用する場合は、 compressedDigitalAudioOPL、uncompressedDigitalAudioOPL、compressedDigitalVideoOPL、uncompressedDigitalVideoOPL および unknownOutputBehavior フラグを使用して、トークン生成時に出力保護レベル値をアタッチします。 これらについては、で説明しています。 [PlayReady ライセンストークンリクエスト](https://www.expressplay.com/developer/restapi/#playready-license-token-request)
