---
seo-title: 既存のDRMコンテンツを更新してCloud DRMを使用する（オプション）
title: 既存のDRMコンテンツを更新してCloud DRMを使用する（オプション）
uuid: cfabeb06-210f-45af-b8a6-8e0b03a76103
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---


# 既存のDRMコンテンツを更新してCloud DRM（オプション） {#update-existing-drm-content-to-use-cloud-drm-optional}を使用

Primetime DRMで保護されているコンテンツの既存のライブラリがある場合は、元のソースファイルを再パッケージ化または暗号化する代わりに、既存のコンテンツを「ヘッダーを再」してPrimetime Cloud DRMサービスを使用できます。 コンテンツのリヘッドリングは、HLSマニフェスト内のコンテンツのDRMメタデータを更新するだけです。 元のアセットの非暗号化/再暗号化は実行されません。 これは、元のソースコンテンツが利用できない場合や、大きなライブラリの再パッケージ化に必要なリソースの量が心配な場合に便利です。

Primetime DRM Java SDKを使用して、メタデータをプログラム的に更新できます。 また、この保護キットに含まれる[!DNL OfflinePackager.jar]コマンドラインツールでは、`-drm_refresh`オプションを使用してこのタスクを行うこともできます。

## 再ヘッダーの詳細{#section_3F3980D8E775450588C64E02A8448189}

CloudDRMを使用するには、リヘアリングで次のフィールドを更新する必要があります。

* ライセンスサーバーURL ([!DNL ht<span></span>tps://access.adobeprimetime.com/flashaccessserver/axs_prod]へ)
* ライセンスサーバー証明書（CloudDRMライセンスサーバー証明書へ）
* トランスポート証明書（CloudDRMトランスポート証明書へ）
* Packagerの資格情報（CloudDRMで使用するためにアクティベートしたPackagerの資格情報を指定）

## DRMメタデータの検索{#section_28721CB7966F40708AEC8637F2E9BB72}

HTTPテクノロジーを使用するコンテンツ（HDSやHLSなど）は、AdobeアクセスDRMメタデータを参照するマニフェストを使用します。 HDSでは、メタデータは`<drmmeta>`タグで参照され、HLSでは`#EXT-X-FAXS-CM`タグで参照されます。 どちらのシナリオでも、メタデータは、base64エンコードされたblobとしてマニフェスト内にインラインで含めたり、外部からバイナリファイルとして参照したりできます。 メタデータがマニフェストに埋め込まれている/インラインの場合、DRMメタデータをインスタンス化するために使用する前に、最初にbase64-decodeでメタデータをバイナリデータにデコードする必要がある場合があります。

## 付属のOfflinePackager.jar {#section_37C2091856E44AA380D742C72B4DD1A7}を使用

コマンドラインに`-drm_refresh option`を指定します。 更新されたDRMメタデータを使用して新しいマニフェストファイルが作成されますが、コンテンツは再暗号化されません。

## Primetime DRM Java SDKを使用した再ヘッダー{#section_7EDBAC4C78DF4CD5BE8410EEAD8437A2}

既存のDRMメタデータを更新するには、Primetime DRM（旧称Primetime Access DRM）Java SDKを使用してプログラム的なアプローチを行います。 詳しくは、SDKの[!DNL /Reference Implmentation/Command Line Tools/samples/]パッケージ内の[!DNL RegenerateMetadata.java]コードサンプルを参照してください。 AdobeアクセスJava SDKは、このCloudDRM保護キットに含まれていないので、Adobeから直接取得する必要があります。 詳細については、Adobeのビジネス担当者にお問い合わせください。