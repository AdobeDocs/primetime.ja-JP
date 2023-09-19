---
title: FMRMS 1.0 または 1.5 からAdobeAccess 2.0 以降への移行
description: FMRMS 1.0 または 1.5 からAdobeAccess 2.0 以降への移行
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# FMRMS 1.0 または 1.5 からAdobeAccess 2.0 以降への移行 {#migrating-from-fmrms-or-to-adobe-access-and-above}

FlashMedia MediaRights Managementサーバー (FMRMS)1.0 または 1.5 を使用してパッケージ化されたコンテンツのライセンスを引き続き発行するには、Adobeアクセス SDK に基づいて、LiveCycleES サーバーからお客様の新しいサーバーにライセンスとポリシーのデータを移行する必要があります。 重要な手順は次のとおりです。

1. ライセンス情報の読み込み
1. FMRMS ポリシーをAdobeアクセス形式に変換中
1. 1.x の互換性リクエストのサポート ( `FMRMSv1RequestHandler` および `FMRMSv1MetadataHandler`

LiveCycleES からAdobeアクセスベースのサーバーにライセンス情報を読み込むには、 [!DNL Reference Implementation\Server\migration\db] フォルダー。 MySQL、Oracle、または SQL Server のデータベースから関連するデータを CSV ファイル形式に書き出すためのサンプルスクリプトが用意されています。 データをエクスポートした後は、任意のデータベースにインポートできます。 書き出されるライセンス情報には、ライセンス ID、パッケージ化時に割り当てられたコンテンツ ID、使用されたポリシーの ID、コンテンツがパッケージ化された時刻、およびコンテンツ暗号化キーが含まれます。 Adobeアクセスについては、1.x コンテンツのメタデータをAdobeアクセスのメタデータ形式に変換するために必要な情報です ( `FMRMSv1RequestHandler` および `FMRMSv1MetadataHandler`) をクリックします。 参照実装では、このデータはライセンスデータベーステーブルに格納され、 `RefImplMetadataConvReqHandler`.

メタデータを変換し、1.0 または 1.5 コンテンツのライセンスを発行する際に、既存のポリシーをAdobeアクセス形式に変換する必要があります。 Reference Implementation\Server\migration フォルダーには、古いポリシーに基づくAdobeアクセスポリシーを作成するためのサンプルコードが含まれています。

FMRMS 1.0 からAdobeアクセスに移行する場合は、 V1_0PolicyConverter.java のサンプルを参照してください。 「 」を実行してサンプルコードをコンパイルします。 `ant-f build-migration.xml build-1.0-converter`&quot; ( スクリプトは、1.0 およびAdobeアクセスライブラリが [!DNL libs/1.0] と libs/flashaccess のそれぞれ ) に関連付けられています。 converter.properties ファイルを編集して、LiveCycleES サーバを指すようにします。 次に、「 `ant -f build-migration.xml migrate-all-1.0-policies`すべての FMRMS 1.0 ポリシーをAdobe・アクセス形式に変換する。

FMRMS 1.5 からAdobeアクセスに移行する場合は、 V1_5PolicyConverter.java のサンプルを参照してください。 「 」を実行してサンプルコードをコンパイルします。 `ant-f build-migration.xml build-1.5-converter`&quot; （スクリプトでは、1.5 ライブラリと 3.0 ライブラリがそれぞれ libs/1.5 および libs/flashaccess にある必要があります）。 converter.properties ファイルを編集して、LiveCycleES サーバを指すようにします。 次に、「 `ant -f build-migration.xml migrate-all-1.5-policies`すべての FMRMS 1.5 ポリシーをAdobe・アクセス形式に変換する。

変換後のポリシーは、一連のファイルに書き込まれます。 さらに、PolicyConverter は、古いポリシー ID の新しいポリシー ID へのマッピングを含む CSV ファイルを出力します。 このファイルは、参照実装データベースの「PolicyConversion」テーブルにインポートでき、 `RefImplMetadataConvReqHandler`.

関連するデータがAdobeのアクセスベースのサーバーに移行されたら、1.x 互換リクエストのサポートを実装する準備が整います。 詳しくは、 `RefImplUpgradeV1ClientHandler` および `RefImplMetadataConvReqHandler` を参照してください。
