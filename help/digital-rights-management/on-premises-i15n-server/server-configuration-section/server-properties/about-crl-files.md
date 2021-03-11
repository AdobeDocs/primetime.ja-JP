---
title: CRLファイルについて
description: CRLファイルについて
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---


# CRLファイルについて{#about-crl-files}

個別化サーバーとライセンスサーバーが正しく機能するには、実行中のアプリケーションサーバー（Tomcatなど）上のディスクに複数の証明書失効リスト(CRL)ファイルをキャッシュする必要があります。 新しいCRLファイルは、定期的にディスクにダウンロードしてキャッシュする必要があります。 ディスク上のCRLファイルの有効期間が切れると、個別化サーバーはクライアントの個別化を拒否し、ライセンスサーバーはライセンスの発行を拒否します。

ディスクにキャッシュされるCRLには、対応するURLと一致するファイル名が必要です。 コロン「:」や「/」のスラッシュなどの特殊文字は、ファイル名のアンダースコア「_」に変換されます。

次のリストは、個別化サーバーとライセンスサーバーの両方で使用される、外部でホストされているCRLです。

* **Intermediate CRL:**

   * URL:[!DNL <ht<span></span>tps://crl2.adobe.com/Adobe/FlashAccessIntermediateCA.crl>]
   * ファイル：[!DNL http___crl2.adobe.com_Adobe_FlashAccessIntermediateCA.crl]
   * 有効性：作成から約12ヶ月は有効

* **Root CRL:**

   * URL:[!DNL <ht<span></span>tps://crl2.adobe.com/Adobe/FlashAccessRootCA.crl>]
   * ファイル：[!DNL http___crl2.adobe.com_Adobe_FlashAccessRootCA.crl]
   * 有効性：創造から約5年間有効

* **Latest CRL:**

   * URL:[!DNL <ht<span></span>tps://crl3.adobe.com/AdobeSystemsIncorporatedFlashAccessRuntime/LatestCRL.crl>]
   * ファイル：[!DNL http___crl3.adobe.com_AdobeSystemsIncorporatedFlashAccessRuntime_LatestCRL.crl]
   * 有効性：作成から約3か月間有効

次は、License Serverでのみ使用される、外部でホストされているCRLです。

* URL:[!DNL <ht<span></span>tps://crl2.adobe.com/Adobe/FlashAccessIndividualizationCA.crl>]
* ファイル：[!DNL http___crl2.adobe.com_Adobe_FlashAccessIndividualizationCA.crl]
* 有効性：作成から約3か月間有効

* URL:[!DNL <ht<span></span>tps://individualization-crl.primetime.adobe.com/FlashAccessIndividualizationCA.crl>]
* ファイル：[!DNL http___individualization-crl.primetime.adobe.com_FlashAccessIndividualizationCA.crl]
* 有効性：作成から約3か月間有効

* URL:[!DNL <ht<span></span>tps://individualization-crl.s3-website-us-east-1.amazonaws.com/FlashAccessIndividualizationCA.crl]
* ファイル：[!DNL http___individualization-crl.s3-website-us-east-1.amazonaws.com_FlashAccessIndividualizationCA.crl]
* 有効性：作成から約3か月間有効

前述のCRLに加えて、追加のCRLを作成して管理する必要があります。 これは、このドキュメントの[Create Individualization CA CRL](../../../on-premises-i15n-server/server-configuration-section/server-properties/create-i15n-ca-crl.md)セクションで指定されている個別化CRLです。

CRLは、有効期限が切れる45日前に更新されるようにスケジュールされます。 これにより、新たに生成されたCRLをインターネットから取得してインストールするのに十分な時間が確保されます。 CRLファイルの有効期限が切れる前に、必ずCRLファイルを更新してください。
