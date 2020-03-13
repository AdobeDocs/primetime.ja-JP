---
seo-title: ライセンスのプレビュー
title: ライセンスのプレビュー
uuid: 61ff171f-b977-40ef-8e8d-2900316fa89a
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# ライセンスのプレビュー {#license-preview}

デバイスがPrimetime DRMライセンスを利用し、完全に実施できるかどうかに関する質問がある場合は、ライセンスプレビュー機能を使用できます。 プレビューライセンスは、最終的なライセンスで定義されているすべての制約と制限に完全に一致しますが、保護されたコンテンツの復号化に必要なコンテンツ暗号化キー(CEK)は含まれません。 この機能は、コンテンツ配信者がクライアントに特定のライセンスを提供する決定を行う前に、クライアントが実際にライセンスを使用できるかどうかを判断する際に役立ちます。 例えば、顧客がHDコンテンツを視聴したいが、コンテンツ配信者は、デバイスがHDCPを完全に検出し、関与できることを確認したいと考えているとします。 この場合、クライアントからの呼び出しが可能で `DRMManager.loadPreviewVoucher()`す。 を受け取っ `DRMStatusEvent``DRMErrorEvent`た場合は、を受け取る代わりに、クライアントがライセンスの出力保護の制限を完全に実施できることが確認され、コンテンツ配布者はこの種類のライセンスをクライアントに自由に提供できます。

[iOS acquirePreviewLicense:](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a3baac603bdd8826624dbe97f9faaba10)

[Android acquirePreviewLicense()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#acquirePreviewLicense(com.adobe.ave.drm.DRMMetadata,%20com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMLicenseAcquiredCallback))
