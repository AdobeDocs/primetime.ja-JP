---
description: Media MediaRights Managementサーバー (FMRMS)1.0 または 1.5 でパッケージ化されたコンテンツのライセンスを引き続き発行するには、LiveCycleES サーバーからAdobe Primetime DRM SDK に基づくお客様の新しいサーバーに、ライセンスと DRM ポリシーデータを移行する必要があります。
title: FMRMS 1.0 または 1.5 からAdobe Primetime DRM 2.0 以降への移行
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# FMRMS 1.0 または 1.5 からAdobe Primetime DRM 2.0 以降への移行{#migrate-from-fmrms-or-to-adobe-primetime-drm-or-later}

Media MediaRights Managementサーバー (FMRMS)1.0 または 1.5 でパッケージ化されたコンテンツのライセンスを引き続き発行するには、LiveCycleES サーバーからAdobe Primetime DRM SDK に基づくお客様の新しいサーバーに、ライセンスと DRM ポリシーデータを移行する必要があります。

移行するには、次のタスクを実行します。

1. ライセンス情報を読み込む：

   1. LiveCycleES から Primetime DRM ベースのサーバーにライセンス情報を読み込むには、 [!DNL Reference Implementation\Server\migration\db] フォルダー。
   1. サンプルスクリプトを実行して、MySQL、Oracle、または SQL Server のデータベースから CSV ファイル形式に関連データを書き出します。
   1. LiveCycleES からデータを書き出した後、データをデータベースに読み込みます。

      書き出されるライセンス情報には、次の情報が含まれます。

      * ライセンス ID
      * パッケージ化時に割り当てられるコンテンツ ID
      * 適用される DRM ポリシーの ID
      * コンテンツがパッケージ化された時間
      * コンテンツ暗号化キー

      この情報は、1.x のコンテンツメタデータを Primetime DRM メタデータ形式に変換する前に必要です。 参照実装では、このデータはライセンスデータベーステーブルに格納され、 `RefImplMetadataConvReqHandler`. 詳しくは、 `FMRMSv1RequestHandler` および `FMRMSv1MetadataHandler`.

1. FMRMS ポリシーを Primetime DRM 形式に変換します。

   1. DRM ポリシーを適用してメタデータを変換し、バージョン 1.0 またはバージョン 1.5 のコンテンツのライセンスを発行する前に、既存の DRM ポリシーを Primetime DRM 形式に変換します。

      The `Reference Implementation\Server\migration` フォルダーには、古い DRM ポリシーに基づく Primetime DRM ポリシーを作成するためのサンプルコードが含まれています。 FMRMS 1.0 から Primetime DRM に移行するには、 `V1_0PolicyConverter.java` サンプル。
   1. を実行してサンプルコードをコンパイルします。 `ant-f build-migration.xml build-1.0-converter` スクリプトを使用して、 [!DNL libs/1.0] および [!DNL libs/flashaccess] ディレクトリ。

   1. を編集します。 [!DNL converter.properties] ファイルを使用して、LiveCycleES サーバーを指定します。
   1. 実行 `ant -f build-migration.xml migrate-all-1.0-policies` を使用して、すべての FMRMS 1.0 DRM ポリシーを Primetime DRM 形式に変換します。

      FMRMS 1.5 から Primetime DRM に移行するには、 `V1_5PolicyConverter.java` サンプル。

   1. を実行してサンプルコードをコンパイルします。 `ant-f build-migration.xml build-1.5-converter` スクリプトでは、1.5 ライブラリと 3.0 ライブラリが [!DNL libs/1.5] および [!DNL libs/flashaccess] ディレクトリ。

   1. を編集します。 [!DNL converter.properties] ファイルを使用して、LiveCycleES サーバーを指定します。
   1. 実行 `ant -f build-migration.xml migrate-all-1.5-policies` を使用して、すべての FMRMS 1.5 DRM ポリシーを Primetime DRM 形式に変換できます。

      変換された DRM ポリシーは、ファイルのセットとして保存されます。 The `DRM PolicyConverter` は、古い DRM ポリシー ID と新しい DRM ポリシー ID のマッピングを含む CSV 形式のファイルを生成します。 このファイルは、 [!DNL PolicyConversion] 参照実装データベースの表。この表は、 `RefImplMetadataConvReqHandler`.

1. 1.x の互換性リクエストを `FMRMSv1RequestHandler` および `FMRMSv1MetadataHandler` プロパティ：

   1. 関連するデータを Primetime DRM ベースのサーバーに移行した後、1.x の互換性リクエストのサポートを実装します。

      これらのタイプのリクエストの処理方法の例については、 `RefImplUpgradeV1ClientHandler` および `RefImplMetadataConvReqHandler` を参照してください。
