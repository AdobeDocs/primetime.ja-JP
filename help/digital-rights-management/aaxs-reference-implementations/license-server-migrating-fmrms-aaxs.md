---
title: FMRMS 1.0または1.5からAdobeアクセス2.0以降への移行
description: FMRMS 1.0または1.5からAdobeアクセス2.0以降への移行
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---


# FMRMS 1.0または1.5からAdobeアクセス2.0以降への移行{#migrating-from-fmrms-or-to-adobe-access-and-above}

FlashメディアRights Managementサーバー(FMRMS)1.0または1.5を使用してパッケージ化されたコンテンツのライセンスを引き続き発行するには、AdobeアクセスSDKに基づいて、LiveCycleESサーバーからお客様の新しいサーバーにライセンスとポリシーデータを移行する必要があります。 重要な手順は次のとおりです。

1. ライセンス情報の読み込み
1. FMRMSポリシーのAdobeアクセス形式への変換
1. `FMRMSv1RequestHandler`と`FMRMSv1MetadataHandler`を介した1.x互換リクエストのサポート

LiveCycleESからAdobeアクセスベースのサーバーにライセンス情報を読み込むには、[!DNL Reference Implementation\Server\migration\db]フォルダーにあるサンプルのデータベーススクリプトを参照してください。 MySQL、OracleまたはSQL Serverのデータベースから関連データをCSVファイル形式に書き出すためのサンプルスクリプトが用意されています。 エクスポートしたデータは、任意のデータベースにインポートできます。 書き出されるライセンス情報には、ライセンスID、パッケージ化時に割り当てられるコンテンツID、使用されるポリシーのID、コンテンツがパッケージ化された日時、およびコンテンツ暗号化キーが含まれます。 Adobeアクセスの場合、1.xコンテンツのメタデータをAdobeアクセスのメタデータ形式に変換するためには、この情報が必要です（`FMRMSv1RequestHandler`と`FMRMSv1MetadataHandler`を参照）。 参照実装では、このデータはライセンスデータベーステーブルに格納され、`RefImplMetadataConvReqHandler`が使用します。

メタデータを変換して1.0または1.5コンテンツのライセンスを発行する場合、既存のポリシーをAdobeアクセス形式に変換して使用する必要があります。 リファレンスImplementation\Server\migration folder contains sample code for creating an Adobe Access policy based on older policies。

FMRMS 1.0からAdobeアクセスに移行する場合は、V1_0PolicyConverter.javaのサンプルを参照してください。 「`ant-f build-migration.xml build-1.0-converter`」を実行してサンプルコードをコンパイルします(スクリプトでは、1.0ライブラリとAdobeアクセスライブラリがそれぞれ[!DNL libs/1.0]とlibs/flashaccessにある必要があります)。 converter.propertiesファイルを編集し、LiveCycleESサーバーを指すようにします。 次に、&quot; `ant -f build-migration.xml migrate-all-1.0-policies`&quot;を実行し、すべてのFMRMS 1.0ポリシーをAdobeアクセス形式に変換します。

FMRMS 1.5からAdobeアクセスに移行する場合は、V1_5PolicyConverter.javaのサンプルを参照してください。 「 `ant-f build-migration.xml build-1.5-converter` 」を実行してサンプルコードをコンパイルします（スクリプトでは、1.5ライブラリと3.0ライブラリがそれぞれlibs/1.5とlibs/flashaccessにある必要があります）。 converter.propertiesファイルを編集し、LiveCycleESサーバーを指すようにします。 次に、&quot; `ant -f build-migration.xml migrate-all-1.5-policies`&quot;を実行し、すべてのFMRMS 1.5ポリシーをAdobeアクセス形式に変換します。

変換されたポリシーは、一連のファイルに書き込まれます。 また、PolicyConverterは、古いポリシーIDと新しいポリシーIDとのマッピングを含むCSVファイルを出力します。 このファイルは、参照実装データベースの&quot;PolicyConversion&quot;テーブルにインポートでき、`RefImplMetadataConvReqHandler`で使用されます。

関連データがAdobeアクセスベースのサーバーに移行されたら、1.x互換要求のサポートを実装する準備が整います。 これらのタイプのリクエストを処理する方法の例については、リファレンス実装の`RefImplUpgradeV1ClientHandler`と`RefImplMetadataConvReqHandler`を参照してください。
