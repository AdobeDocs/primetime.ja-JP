---
description: FlashメディアRights Managementサーバー(FMRMS)1.0または1.5でパッケージ化されたコンテンツのライセンスの発行を続けるには、LiveCycleESサーバーのライセンスおよびDRMポリシーデータを、Adobe PrimetimeDRM SDKに基づくお客様の新しいサーバーに移行する必要があります。
seo-description: FlashメディアRights Managementサーバー(FMRMS)1.0または1.5でパッケージ化されたコンテンツのライセンスの発行を続けるには、LiveCycleESサーバーのライセンスおよびDRMポリシーデータを、Adobe PrimetimeDRM SDKに基づくお客様の新しいサーバーに移行する必要があります。
seo-title: FMRMS 1.0または1.5からAdobe PrimetimeDRM 2.0以降への移行
title: FMRMS 1.0または1.5からAdobe PrimetimeDRM 2.0以降への移行
uuid: 49ecbbd2-d83b-4bf2-841e-c3f9e5d5e141
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---


# FMRMS 1.0または1.5からAdobe PrimetimeDRM 2.0以降への移行{#migrate-from-fmrms-or-to-adobe-primetime-drm-or-later}

FlashメディアRights Managementサーバー(FMRMS)1.0または1.5でパッケージ化されたコンテンツのライセンスの発行を続けるには、LiveCycleESサーバーのライセンスおよびDRMポリシーデータを、Adobe PrimetimeDRM SDKに基づくお客様の新しいサーバーに移行する必要があります。

移行するには、次のタスクを実行します。

1. ライセンス情報の読み込み：

   1. LiveCycleESからPrimetime DRMベースのサーバーにライセンス情報を読み込むには、[!DNL Reference Implementation\Server\migration\db]フォルダーにあるサンプルデータベーススクリプトを参照してください。
   1. サンプルスクリプトを実行して、MySQL、OracleまたはSQL Serverのデータベースから関連するデータをCSVファイル形式にエクスポートします。
   1. LiveCycleESからデータを書き出した後、データをデータベースに読み込みます。

      書き出されるライセンス情報には、次の情報が含まれます。

      * ライセンスID
      * パッケージ化時に割り当てられるコンテンツID
      * 適用中のDRMポリシーのID
      * コンテンツがパッケージ化された時刻
      * コンテンツ暗号化キー

      この情報は、1.xコンテンツのメタデータをPrimetime DRMメタデータ形式に変換する前に必要です。 参照実装では、このデータはライセンスデータベーステーブルに格納され、`RefImplMetadataConvReqHandler`によって使用されます。 詳しくは、`FMRMSv1RequestHandler`と`FMRMSv1MetadataHandler`を参照してください。


1. FMRMSポリシーをPrimetime DRM形式に変換します。

   1. DRMポリシーを適用してメタデータを変換し、バージョン1.0またはバージョン1.5コンテンツのライセンスを発行する前に、既存のDRMポリシーをPrimetime DRM形式に変換します。

      `Reference Implementation\Server\migration`フォルダーには、古いDRMポリシーに基づくPrimetime DRMポリシーを作成するためのサンプルコードが含まれています。 FMRMS 1.0からPrimetime DRMに移行するには、`V1_0PolicyConverter.java`サンプルを参照してください。
   1. `ant-f build-migration.xml build-1.0-converter`スクリプトを実行してサンプルコードをコンパイルします。このスクリプトは、[!DNL libs/1.0]と[!DNL libs/flashaccess]のディレクトリ内の1.0およびPrimetime DRMライブラリを検索します。

   1. [!DNL converter.properties]ファイルを編集して、LiveCycleESサーバーを指定します。
   1. `ant -f build-migration.xml migrate-all-1.0-policies`を実行し、すべてのFMRMS 1.0 DRMポリシーをPrimetime DRM形式に変換します。

      FMRMS 1.5からPrimetime DRMに移行するには、`V1_5PolicyConverter.java`サンプルを参照してください。

   1. `ant-f build-migration.xml build-1.5-converter`スクリプトを実行してサンプルコードをコンパイルします。このスクリプトでは、1.5と3.0のライブラリが[!DNL libs/1.5]と[!DNL libs/flashaccess]のディレクトリにある必要があります。

   1. [!DNL converter.properties]ファイルを編集して、LiveCycleESサーバーを指定します。
   1. `ant -f build-migration.xml migrate-all-1.5-policies`を実行し、すべてのFMRMS 1.5 DRMポリシーをPrimetime DRM形式に変換します。

      変換されたDRMポリシーは、ファイルのセットとして保存されます。 `DRM PolicyConverter`は、古いDRMポリシーIDと新しいDRMポリシーIDとのマッピングを含むCSV形式のファイルを生成します。 このファイルは、参照実装データベースの[!DNL PolicyConversion]テーブルにインポートできます。このテーブルは`RefImplMetadataConvReqHandler`で使用されます。

1. 1.x互換要求を`FMRMSv1RequestHandler`および`FMRMSv1MetadataHandler`プロパティでサポートします。

   1. 関連するデータがPrimetime DRMベースのサーバーに移行された後、1.x互換性リクエストのサポートを実装します。

      これらのタイプのリクエストの処理方法の例については、リファレンス実装の`RefImplUpgradeV1ClientHandler`と`RefImplMetadataConvReqHandler`を参照してください。

