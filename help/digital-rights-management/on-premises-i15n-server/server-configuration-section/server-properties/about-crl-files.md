---
seo-title: CRLファイルについて
title: CRLファイルについて
uuid: 672c3ca0-5c5d-4ec7-83b1-f0f8e34c8d09
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# CRLファイルについて {#about-crl-files}

個別化サーバーとライセンスサーバーが正しく機能するには、実行中のアプリケーションサーバー（Tomcatなど）上のディスクに複数の証明書失効リスト(CRL)ファイルをキャッシュする必要があります。 新しいCRLファイルは、定期的にスケジュールされた状態でディスクにダウンロードし、キャッシュする必要があります。 ディスク上のCRLファイルの有効期間の終了が許可されている場合、個別化サーバーはクライアントの個別化を拒否し、ライセンスサーバーはライセンスの発行を拒否します。

ディスクにキャッシュされたCRLには、対応するURLと一致するファイル名が必要です。 コロン「:」や「/」のスラッシュなどの特殊文字は、ファイル名のアンダースコア「_」に変換されます。

次に、個別化サーバーとライセンスサーバーの両方で使用される、外部でホストされているCRLの一覧を示します。

* **Intermediate CRL:**

   * URL: [!DNL <ht<span></span>tps://crl2.adobe.com/Adobe/FlashAccessIntermediateCA.crl>]
   * ファイル： [!DNL http___crl2.adobe.com_Adobe_FlashAccessIntermediateCA.crl]
   * 有効性：作成から約12ヶ月間有効

* **Root CRL:**

   * URL: [!DNL <ht<span></span>tps://crl2.adobe.com/Adobe/FlashAccessRootCA.crl>]
   * ファイル： [!DNL http___crl2.adobe.com_Adobe_FlashAccessRootCA.crl]
   * 有効性：創造から約5年間有効

* **最新のCRL:**

   * URL: [!DNL <ht<span></span>tps://crl3.adobe.com/AdobeSystemsIncorporatedFlashAccessRuntime/LatestCRL.crl>]
   * ファイル： [!DNL http___crl3.adobe.com_AdobeSystemsIncorporatedFlashAccessRuntime_LatestCRL.crl]
   * 有効性：作成から約3か月間有効

次に示すのは、License Serverでのみ使用される外部でホストされるCRLです。

* URL: [!DNL <ht<span></span>tps://crl2.adobe.com/Adobe/FlashAccessIndividualizationCA.crl>]
* ファイル： [!DNL http___crl2.adobe.com_Adobe_FlashAccessIndividualizationCA.crl]
* 有効性：作成から約3か月間有効

* URL: [!DNL <ht<span></span>tps://individualization-crl.primetime.adobe.com/FlashAccessIndividualizationCA.crl>]
* ファイル： [!DNL http___individualization-crl.primetime.adobe.com_FlashAccessIndividualizationCA.crl]
* 有効性：作成から約3か月間有効

* URL: [!DNL <ht<span></span>tps://individualization-crl.s3-website-us-east-1.amazonaws.com/FlashAccessIndividualizationCA.crl]>
* ファイル： [!DNL http___individualization-crl.s3-website-us-east-1.amazonaws.com_FlashAccessIndividualizationCA.crl]
* 有効性：作成から約3か月間有効

前述のCRLに加え、追加のCRLを作成および管理する必要があります。 これは、このドキュメントの「個別化CA CRLの作成」セクシ [ョンで指定されている個別化CA](../../../on-premises-i15n-server/server-configuration-section/server-properties/create-i15n-ca-crl.md) CRLです。

CRLは、有効期限が切れる45日前に更新される予定です。 これにより、新しく生成されたCRLをインターネットから取得し、インストールするのに十分な時間を確保できます。 CRLファイルの有効期限が切れる前に、更新の作業を慎重に行う必要があります。
