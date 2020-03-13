---
description: Flash Media Rights Management Server(FMRMS)1.0または1.5でパッケージ化されたコンテンツのライセンスの発行を続行するには、LiveCycle ESサーバーのライセンスとDRMポリシーデータを、Adobe Primetime DRM SDKに基づくお客様の新しいサーバーに移行する必要があります。
seo-description: Flash Media Rights Management Server(FMRMS)1.0または1.5でパッケージ化されたコンテンツのライセンスの発行を続行するには、LiveCycle ESサーバーのライセンスとDRMポリシーデータを、Adobe Primetime DRM SDKに基づくお客様の新しいサーバーに移行する必要があります。
seo-title: FMRMS 1.0または1.5からAdobe Primetime DRM 2.0以降への移行
title: FMRMS 1.0または1.5からAdobe Primetime DRM 2.0以降への移行
uuid: 49ecbbd2-d83b-4bf2-841e-c3f9e5d5e141
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# FMRMS 1.0または1.5からAdobe Primetime DRM 2.0以降への移行{#migrate-from-fmrms-or-to-adobe-primetime-drm-or-later}

Flash Media Rights Management Server(FMRMS)1.0または1.5でパッケージ化されたコンテンツのライセンスの発行を続行するには、LiveCycle ESサーバーのライセンスとDRMポリシーデータを、Adobe Primetime DRM SDKに基づくお客様の新しいサーバーに移行する必要があります。

移行するには、次のタスクを実行します。

1. ライセンス情報の読み込み：

   1. LiveCycle ESからPrimetime DRMベースのサーバーにライセンス情報を読み込むには、フォルダー内のサンプルデータベーススクリプトを参照してく [!DNL Reference Implementation\Server\migration\db] ださい。
   1. サンプルスクリプトを実行して、MySQL、OracleまたはSQL Serverデータベースから関連するデータをCSVファイル形式にエクスポートします。
   1. LiveCycle ESからデータを書き出した後、データをデータベースに読み込みます。

      書き出されるライセンス情報には、次の情報が含まれます。

      * ライセンスID
      * パッケージ化時に割り当てられるコンテンツID
      * 適用されるDRMポリシーのID
      * コンテンツがパッケージ化された時刻
      * コンテンツ暗号化キー
      この情報は、1.xコンテンツのメタデータをPrimetime DRMメタデータ形式に変換する前に必要です。 参照実装では、このデータはライセンスデータベーステーブルに格納され、によって使用されま `RefImplMetadataConvReqHandler`す。 For more information, see `FMRMSv1RequestHandler` and `FMRMSv1MetadataHandler`.


1. FMRMSポリシーをPrimetime DRM形式に変換します。

   1. DRMポリシーを適用してメタデータを変換し、バージョン1.0またはバージョン1.5コンテンツのライセンスを発行する前に、既存のDRMポリシーをPrimetime DRM形式に変換します。

      このフォ `Reference Implementation\Server\migration` ルダーには、古いDRMポリシーに基づくPrimetime DRMポリシーを作成するためのサンプルコードが含まれています。 FMRMS 1.0からPrimetime DRMに移行するには、サンプルを参照してくだ `V1_0PolicyConverter.java` さい。
   1. スクリプトを実行してサンプルコー `ant-f build-migration.xml build-1.0-converter` ドをコンパイルします。スクリプトは、とのディレクトリ内の1.0およびPrimetime DRMライブラリを検索 [!DNL libs/1.0] し [!DNL libs/flashaccess] ます。

   1. ファイルを編 [!DNL converter.properties] 集して、LiveCycle ESサーバーを指すようにします。
   1. を実行 `ant -f build-migration.xml migrate-all-1.0-policies` して、すべてのFMRMS 1.0 DRMポリシーをPrimetime DRM形式に変換します。

      FMRMS 1.5からPrimetime DRMに移行するには、サンプルを参照してくだ `V1_5PolicyConverter.java` さい。

   1. スクリプトを実行してサンプルコ `ant-f build-migration.xml build-1.5-converter` ードをコンパイルします。このスクリプトでは、1.5と3.0のライブラリがとのディレクトリにあ [!DNL libs/1.5] る必要があ [!DNL libs/flashaccess] ります。

   1. ファイルを編 [!DNL converter.properties] 集して、LiveCycle ESサーバーを指すようにします。
   1. を実行 `ant -f build-migration.xml migrate-all-1.5-policies` して、すべてのFMRMS 1.5 DRMポリシーをPrimetime DRM形式に変換します。

      変換されたDRMポリシーは、ファイルのセットとして保存されます。 古いDRM `DRM PolicyConverter` ポリシーIDと新しいDRMポリシーIDとのマッピングを含むCSV形式のファイルが生成されます。 このファイルは、参照実装データベ [!DNL PolicyConversion] ース内の表に読み込むことができます。この表は、で使用されま `RefImplMetadataConvReqHandler`す。

1. 1.x互換要求を、およびプロパティを使用してサポ `FMRMSv1RequestHandler` ートし `FMRMSv1MetadataHandler` ます。

   1. 関連データがPrimetime DRMベースのサーバーに移行された後、1.x互換性要求のサポートを実装します。

      これらのタイプのリクエストの処理方法の例については、およびのリファレンス実装 `RefImplUpgradeV1ClientHandler` を参照 `RefImplMetadataConvReqHandler` してください。

