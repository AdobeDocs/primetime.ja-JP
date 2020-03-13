---
seo-title: 既存のDRMコンテンツを更新してCloud DRMを使用する（オプション）
title: 既存のDRMコンテンツを更新してCloud DRMを使用する（オプション）
uuid: cfabeb06-210f-45af-b8a6-8e0b03a76103
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# 既存のDRMコンテンツを更新してCloud DRMを使用する（オプション） {#update-existing-drm-content-to-use-cloud-drm-optional}

Primetime DRMで保護されているコンテンツの既存のライブラリがある場合、元のソースファイルを再パッケージ化/暗号化する代わりに、既存のコンテンツをPrimetime Cloud DRMサービスを使用するように「再ヘッダー」できます。 コンテンツのリヘッドリングは、HLSマニフェスト内のコンテンツのDRMメタデータを更新するだけです。 元のアセットの非暗号化/再暗号化は実行されません。 元のソースコンテンツが使用できない場合や、大きなライブラリを再パッケージ化するために必要なリソースの量に関する懸念がある場合は、このオプションが役に立ちます。

Primetime DRM Java SDKを使用して、メタデータをプログラム的に更新できます。 また、この保護キッ [!DNL OfflinePackager.jar] トに含まれるコマンドラインツールも、このオプションを使用してこのタスクを実行で `-drm_refresh` きます。

## 再ヘッダーの詳細 {#section_3F3980D8E775450588C64E02A8448189}

CloudDRMを使用するには、次のフィールドを更新する必要があります。

* ライセンスサーバのURL( [!DNL ht<span></span>tps://access.adobeprimetime.com/flashaccessserver/axs_prod])
* ライセンスサーバー証明書（CloudDRMライセンスサーバー証明書へ）
* トランスポート証明書（CloudDRMトランスポート証明書へ）
* Packagerの秘密鍵証明書（CloudDRMで使用するためにアクティベートしたPackagerの秘密鍵証明書）

## DRMメタデータの検索 {#section_28721CB7966F40708AEC8637F2E9BB72}

HTTPテクノロジー（HDSやHLSなど）を使用するコンテンツは、Adobe Access DRMメタデータを参照するマニフェストを使用します。 HDSでは、メタデータはタグで参照さ `<drmmeta>` れ、HLSではタグで参照され `#EXT-X-FAXS-CM` ます。 どちらのシナリオでも、メタデータは、base-64エンコードBLOBとしてマニフェストにインラインで含めるか、バイナリファイルとして外部から参照することができます。 メタデータがマニフェストに埋め込まれる/インラインの場合、DRMメタデータのインスタンス化にメタデータを使用する前に、最初にbase64-decodeでバイナリデータにする必要がある場合があります。

## 付属のOfflinePackager.jarの使用 {#section_37C2091856E44AA380D742C72B4DD1A7}

コマンドラ `-drm_refresh option` インにを指定します。 更新されたDRMメタデータを使用して新しいマニフェストファイルが作成されますが、コンテンツは再暗号化されません。

## Primetime DRM Java SDKを使用した再ヘッダー {#section_7EDBAC4C78DF4CD5BE8410EEAD8437A2}

既存のDRMメタデータの更新は、Primetime DRM（旧称Adobe Access DRM）Java SDKを使用してプログラム的なアプローチで実行できます。 詳しくは、SDKのパッケージに含まれ [!DNL RegenerateMetadata.java] るコードサンプルを [!DNL /Reference Implmentation/Command Line Tools/samples/] 参照してください。 Adobe Access Java SDKは、このCloudDRM保護キットの一部ではなく、アドビから直接取得する必要があります。 詳しくは、アドビのビジネス担当者にお問い合わせください。