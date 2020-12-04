---
seo-title: ライセンスプレビュー
title: ライセンスプレビュー
uuid: 61ff171f-b977-40ef-8e8d-2900316fa89a
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---


# ライセンスプレビュー{#license-preview}

Primetime DRMライセンスを利用して完全に適用できるかどうかに関する質問がある場合は、ライセンスプレビュー機能を使用できます。 プレビューライセンスは、最終的なライセンスで定義されているすべての制約と制限に完全に一致しますが、保護されたコンテンツの復号化に必要なコンテンツ暗号化キー(CEK)は含まれません。 この機能は、コンテンツ配信者がクライアントに特定のライセンスを提供する決定を行う前に、クライアントが実際にライセンスを消費できるかどうかを判断するのに役立ちます。 例えば、HDコンテンツの視聴を希望する顧客が、コンテンツ配布者はデバイスがHDCPを完全に検出し関与できるようにしたいと考えています。 この場合、クライアントは`DRMManager.loadPreviewVoucher()`を呼び出すことができます。 `DRMErrorEvent`ではなく`DRMStatusEvent`を受け取った場合、クライアントがライセンスの出力保護制限を完全に適用できることが確認され、コンテンツ配信者はこの種類のライセンスをクライアントに自由に提供できます。

[iOS acquirePreviewLicense:](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a3baac603bdd8826624dbe97f9faaba10)

[Android acquirePreviewLicense()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#acquirePreviewLicense(com.adobe.ave.drm.DRMMetadata,%20com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMLicenseAcquiredCallback))
