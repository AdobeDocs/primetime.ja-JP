---
description: 次の暗号化オプションは、パッケージ化時に選択され、ライセンス取得時に変更できません。
title: キーの回転
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---

# キーの回転{#key-rotation}

次の暗号化オプションは、パッケージ化時に選択され、ライセンス取得時に変更できません。

パッケージ化の際、通常、コンテンツはコンテンツ暗号化キー (CEK) を使用して暗号化され、クライアントはコンテンツを消費するために CEK を含むライセンスを取得します。 キーのローテーションが有効な場合、ローテーションキーを使用してコンテンツが暗号化され、各ローテーションキーを使用してコンテンツの一部が暗号化されるようにキーを変更できます。 ローテーションキーはコンテンツ暗号化キーを使用して保護され、クライアントはコンテンツを使用するために CEK を含む 1 つのライセンスを取得します。 パッケージャの実装では、使用するコンテンツ暗号化キーとローテーションキー、およびローテーションキーが変更される頻度を制御できます。

キーローテーションを使用してパッケージ化されたコンテンツは、Adobeアクセスクライアントバージョン 3.0 以降でのみ再生できます。 古いクライアントは、このコンテンツを再生するためにアップグレードする必要があります。
