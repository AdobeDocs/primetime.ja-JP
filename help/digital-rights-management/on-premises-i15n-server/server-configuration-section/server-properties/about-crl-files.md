---
title: CRL ファイルについて
description: CRL ファイルについて
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# CRL ファイルについて {#about-crl-files}

個別化およびライセンスサーバーが正しく機能するには、実行中のアプリケーションサーバー（Tomcat など）上のディスクに、複数の証明書失効リスト (CRL) ファイルをキャッシュする必要があります。 新しい CRL ファイルは、定期的にスケジュールされた状態で、ディスクにダウンロードしてキャッシュする必要があります。 ディスク上の CRL ファイルの有効期間が経過できる場合、個別化サーバはクライアントの個別化を拒否し、ライセンスサーバはライセンスの発行を拒否します。

ディスクにキャッシュされた CRL には、対応する URL と一致するファイル名が必要です。 コロン「:」やスラッシュ「/」などの特殊文字は、ファイル名ではアンダースコア「_」に変換されます。

次に、個別化サーバーとライセンスサーバーの両方で使用される、外部でホストされる CRL のリストを示します。

* **中間 CRL:**

   * URL: [!DNL <ht<span></span>tps://crl2.adobe.com/Adobe/FlashAccessIntermediateCA.crl>]
   * ファイル： [!DNL http___crl2.adobe.com_Adobe_FlashAccessIntermediateCA.crl]
   * 有効性：作成後約 12 ヶ月間有効

* **ルート CRL:**

   * URL: [!DNL <ht<span></span>tps://crl2.adobe.com/Adobe/FlashAccessRootCA.crl>]
   * ファイル： [!DNL http___crl2.adobe.com_Adobe_FlashAccessRootCA.crl]
   * 有効性：作成から約 5 年間有効

* **最新の CRL:**

   * URL: [!DNL <ht<span></span>tps://crl3.adobe.com/AdobeSystemsIncorporatedFlashAccessRuntime/LatestCRL.crl>]
   * ファイル： [!DNL http___crl3.adobe.com_AdobeSystemsIncorporatedFlashAccessRuntime_LatestCRL.crl]
   * 有効性：作成後約 3 か月間有効

ライセンスサーバーで使用できる外部でホストされている CRL については、Adobeサポートにお問い合わせください。

<!---

Commenting out because of a security vulnerability reported in Jira PSIRT-20689. 

The following are externally hosted CRLs that are used only by the License Servers:

* URL: `https://crl2.adobe.com/Adobe/FlashAccessIndividualizationCA.crl`

* File: `http___crl2.adobe.com_Adobe_FlashAccessIndividualizationCA.crl`

* Validity: Good for approximately 3 months from creation

* URL: `https://individualization-crl.primetime.adobe.com/FlashAccessIndividualizationCA.crl`

* File: `http___individualization-crl.primetime.adobe.com_FlashAccessIndividualizationCA.crl`

* Validity: Good for approximately 3 months from creation

* URL: `https://individualization-crl.s3-website-us-east-1.amazonaws.com/FlashAccessIndividualizationCA.crl`

* File: `http___individualization-crl.s3-website-us-east-1.amazonaws.com_FlashAccessIndividualizationCA.crl`

* Validity: Good for approximately 3 months from creation

--->

外部でホストされる CRL に加えて、追加の CRL を作成および管理できます。 これは、 [個別化 CA CRL の作成](../../../on-premises-i15n-server/server-configuration-section/server-properties/create-i15n-ca-crl.md) 」の節を参照してください。

CRL は、期限が切れる 45 日前に更新されるようにスケジュールされます。 これにより、新しく生成された CRL をインターネットから取得してインストールするのに十分な時間を確保できます。 CRL ファイルの有効期限が切れる前に、CRL ファイルの更新に注意する必要があります。
