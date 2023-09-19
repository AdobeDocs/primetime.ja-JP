---
title: 既存の DRM コンテンツを更新して Cloud DRM を使用する（オプション）
description: 既存の DRM コンテンツを更新して Cloud DRM を使用する（オプション）
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# 既存の DRM コンテンツを更新して Cloud DRM を使用する（オプション） {#update-existing-drm-content-to-use-cloud-drm-optional}

Primetime DRM で保護されたコンテンツの既存のライブラリがある場合は、元のソースファイルを再パッケージ化または暗号化する代わりに、既存のコンテンツを再ヘッダー化して Primetime Cloud DRM サービスを使用できます。 コンテンツのリヘッダーによって、HLS マニフェスト内のコンテンツの DRM メタデータが更新されるだけです。 元のアセットの暗号化解除や再暗号化は実行されません。 これは、元のソースコンテンツが使用できない場合や、大きなライブラリの再パッケージ化に必要なリソースの量に問題がある場合に役立ちます。

Primetime DRM Java SDK を使用して、メタデータをプログラムで更新できます。 また、 [!DNL OfflinePackager.jar] この保護キットに含まれるコマンドラインツールは、 `-drm_refresh` オプション。

## 再ヘッダーの詳細 {#section_3F3980D8E775450588C64E02A8448189}

CloudDRM を使用するには、次のフィールドを更新する必要があります。

* ライセンスサーバー URL （宛先） [!DNL ht<span></span>tps://access.adobeprimetime.com/flashaccessserver/axs_prod])
* ライセンスサーバー証明書（CloudDRM ライセンスサーバー証明書へ）
* トランスポート証明書（CloudDRM トランスポート証明書へ）
* Packager 資格情報（CloudDRM で使用するためにアクティベートした Packager 資格情報）

## DRM メタデータの検索 {#section_28721CB7966F40708AEC8637F2E9BB72}

HTTP テクノロジー（HDS や HLS など）を使用するコンテンツは、Adobeアクセス DRM メタデータを参照するマニフェストを利用します。 HDS では、メタデータは `<drmmeta>` タグに追加し、HLS では、 `#EXT-X-FAXS-CM` タグを使用します。 どちらのシナリオでも、メタデータを Base 64 でエンコードされた BLOB としてマニフェストにインラインで含めたり、外部からバイナリファイルとして参照したりできます。 メタデータがマニフェストに埋め込まれている/インラインの場合、DRM メタデータをインスタンス化するために使用する前に、base64-decode でメタデータをバイナリデータにデコードする必要が生じる場合があります。

## 含まれる OfflinePackager.jar の使用 {#section_37C2091856E44AA380D742C72B4DD1A7}

次を指定： `-drm_refresh option` をコマンドラインに追加します。 更新された DRM メタデータを使用して新しいマニフェストファイルが作成されますが、コンテンツは再暗号化されません。

## Primetime DRM Java SDK を使用した再ヘッダー {#section_7EDBAC4C78DF4CD5BE8410EEAD8437A2}

既存の DRM メタデータの更新は、プログラム的なアプローチに Primetime DRM( 旧称：Adobeアクセス DRM)Java SDK を使用して実行できます。 詳しくは、 [!DNL RegenerateMetadata.java] コードサンプルを [!DNL /Reference Implmentation/Command Line Tools/samples/] SDK のパッケージ。 Adobeアクセス Java SDK は、この CloudDRM 保護キットに含まれていないので、Adobeから直接入手する必要があります。 詳しくは、Adobeのビジネス担当者にお問い合わせください。
