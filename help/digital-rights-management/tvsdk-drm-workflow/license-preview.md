---
title: ライセンスのプレビュー
description: ライセンスのプレビュー
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# ライセンスのプレビュー {#license-preview}

デバイスが Primetime DRM ライセンスを消費して完全に実施できるかどうかに関する質問がある場合は、ライセンスプレビュー機能を使用できます。 プレビューライセンスは、最終ライセンスで定義されたすべての制約と制限に完全に一致しますが、保護されたコンテンツの復号化に必要なコンテンツ暗号化キー (CEK) は含まれていません。 この機能は、コンテンツ配布者が特定のライセンスをクライアントに提供する決定を下す前に、クライアントが実際にライセンスを使用できるかどうかを判断するのに役立ちます。 例えば、HD コンテンツを視聴したいと考えている顧客が、コンテンツ配布者は、デバイスが HDCP を完全に検出して関与できるようにしたいと考えています。 この場合、クライアントは `DRMManager.loadPreviewVoucher()`. 次の場合、 `DRMStatusEvent` が受信されるため、 `DRMErrorEvent`その後、クライアントがライセンスの出力保護制限を完全に実施でき、コンテンツ配布者がこの種のライセンスをクライアントに自由に提供できることを確認しました。

[iOS acquirePreviewLicense:](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a3baac603bdd8826624dbe97f9faaba10)

[Android acquirePreviewLicense()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#acquirePreviewLicense(com.adobe.ave.drm.DRMMetadata,%20com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMLicenseAcquiredCallback))
