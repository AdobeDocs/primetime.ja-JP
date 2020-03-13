---
seo-title: Flash Media Rights Management Server 1.xとの互換性の確認
title: Flash Media Rights Management Server 1.xとの互換性の確認
uuid: 0160ca02-ebe6-4090-bf32-1d1a46088844
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Flash Media Rights Management Server 1.xとの互換性の確認{#ensure-compatibility-with-flash-media-rights-management-server-x}

Flash Media Rights Management Server 1.xとAdobe Accessは、コンテンツのパッケージ化とライセンスの要求に異なるメタデータを使用します。 Adobe AccessでFMRMSバージョン1.xコンテンツを使用するには、メタデータを変換する必要があります。

Adobe Access SDKは、メタデータを変換する2つのオプションをサポートしています。

* オフライン（推奨）

   オフラインプロセスでAdobe Accessメタデータを生成し、クライアントが要求したときに使用するために保存します。 アドビでは、このオプションを推奨しています。 メタデータがオフラインで生成される場合、ライセンスサーバーは1.x CEKやPackagerの秘密鍵証明書にアクセスする必要はありません。 また、License Serverでメタデータをリアルタイムで生成する必要がないので、オフラインの変換のパフォーマンスが向上します。

* オンデマンド

   クライアントが要求した場合に、Adobe Accessメタデータをオンデマンドで生成します。 Adobe Accessクライアントは、バージョン1.xのコンテンツをダウンロードすると、DRMメタデータ（DRMヘッダーとも呼ばれます）をAdobe Access SDKに送信します。 SDKは、DRMメタデータを現在の形式に変換します。 SDKは、コンテンツ暗号化キー(CEK)を暗号化してメタデータに埋め込み、コンテンツをAdobe Accessクライアントに返送します。 （Adobe Access 1.xのメタデータにはCEKが含まれていません）。

   メタデータを変換するには、Adobe AccessでAdobe Access 1.xコンテンツ暗号化キーへのアクセスが必要です。 Flash Media Rights Management Server 1.xから移行する場合は、引き続きコンテンツ暗号化キーをLiveCycle ESデータベースに保存するか、カスタムソリューションを実装してコンテンツ暗号化キーを安全に他の場所に保存することができます。 コンテンツ暗号化キーをLiveCycle ESデータベースに保存し続ける場合は、『 *LiveCycle ESの堅牢化とセキュリティ』の「データベース内の機密コンテンツへのアクセスの保護」で概要を説明している推奨事項に従ってください*。

Flash Media Rights Management Server 1.xを使用してパッケージ化されたコンテンツとの互換性を確保する方法について詳しくは、『 *Adobe Access API Reference』を参照してください*。
