---
seo-title: FMRMS 1.0または1.5からAdobe Access 2.0以降への移行
title: FMRMS 1.0または1.5からAdobe Access 2.0以降への移行
uuid: 05caeb39-0c62-4053-87a9-8e89030a188d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# FMRMS 1.0または1.5からAdobe Access 2.0以降への移行 {#migrating-from-fmrms-or-to-adobe-access-and-above}

Flash Media Rights Management Server(FMRMS)1.0または1.5を使用してパッケージ化されたコンテンツのライセンスを引き続き発行するには、LiveCycle ESサーバーからAdobe Access SDKに基づいて、ライセンスとポリシーのデータをお客様の新しいサーバーに移行する必要があります。 重要な手順は次のとおりです。

1. ライセンス情報の読み込み
1. FMRMSポリシーのAdobe Access形式への変換
1. およびを使用した1.x互換性リクエストの `FMRMSv1RequestHandler` サポート `FMRMSv1MetadataHandler`

LiveCycle ESからAdobe Accessベースのサーバーにライセンス情報を読み込むには、フォルダーに用意されているサンプルのデータベーススクリプトを参照してく [!DNL Reference Implementation\Server\migration\db] ださい。 MySQL、OracleまたはSQL Serverデータベースから関連データをCSVファイル形式に書き出すためのサンプルスクリプトが用意されています。 データを書き出すと、選択したデータベースに読み込むことができます。 書き出されたライセンス情報には、ライセンスID、パッケージ化時に割り当てられたコンテンツID、使用されたポリシーのID、コンテンツがパッケージ化された時刻、およびコンテンツ暗号化キーが含まれます。 Adobe Accessの場合、1.xコンテンツのメタデータをAdobe Accessのメタデータ形式に変換するには、この情報が必要です(およびを参照 `FMRMSv1RequestHandler` してく `FMRMSv1MetadataHandler`ださい)。 参照実装では、このデータはライセンスデータベーステーブルに保存され、によって使用されま `RefImplMetadataConvReqHandler`す。

メタデータを変換し、1.0または1.5コンテンツのライセンスを発行する際にこれらのポリシーを使用するには、既存のポリシーをAdobe Access形式に変換する必要があります。 リファレンスImplementation\Server\migration folder contains sample code for creating an Adobe Access policy based on older policies。

FMRMS 1.0からAdobe Accessに移行する場合は、V1_0PolicyConverter.javaのサンプルを参照してください。 「 `ant-f build-migration.xml build-1.0-converter`&quot; 」を実行してサンプルコードをコンパイルします(スクリプトでは、1.0ライブラリとAdobe Accessライブラリがそれぞれlibs/flashaccessに含まれ [!DNL libs/1.0] ている必要があります)。 converter.propertiesファイルを編集して、LiveCycle ESサーバーを指定します。 次に、&quot; `ant -f build-migration.xml migrate-all-1.0-policies`&quot;を実行し、すべてのFMRMS 1.0ポリシーをAdobe Access形式に変換します。

FMRMS 1.5からAdobe Accessに移行する場合は、V1_5PolicyConverter.javaのサンプルを参照してください。 &quot; `ant-f build-migration.xml build-1.5-converter`&quot;を実行してサンプルコードをコンパイルします（スクリプトでは、1.5と3.0のライブラリがlibs/1.5とlibs/flashaccessにそれぞれ存在する必要があります）。 converter.propertiesファイルを編集して、LiveCycle ESサーバーを指定します。 次に、&quot; `ant -f build-migration.xml migrate-all-1.5-policies`&quot;を実行して、すべてのFMRMS 1.5ポリシーをAdobe Access形式に変換します。

変換されたポリシーは、ファイルのセットに書き込まれます。 また、PolicyConverterは、古いポリシーIDと新しいポリシーIDとのマッピングを含むCSVファイルを出力します。 このファイルは、参照実装データベースの「PolicyConversion」テーブルにインポートでき、によって使用されま `RefImplMetadataConvReqHandler`す。

関連データがAdobe Accessベースのサーバーに移行されたら、1.x互換性リクエストのサポートを実装する準備が整います。 これらの `RefImplUpgradeV1ClientHandler` タイプの `RefImplMetadataConvReqHandler` リクエストを処理する方法の例については、およびのリファレンス実装を参照してください。
