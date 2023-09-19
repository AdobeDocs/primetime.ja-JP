---
title: 使用ルール
description: 使用ルール
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# 使用ルール{#usage-rules}

Adobe Access Server for Protected Streaming では、すべての使用ルールが設定ファイルを通じてサーバー上で指定されます。 保護されたコンテンツで指定された使用ルールはすべて上書きされるので、コンテンツのパッケージ化時に単純な匿名ポリシーを使用することをお勧めします。 設定可能な使用ルールは、テナントごとに設定できます。

Adobe Access Server for Protected Streaming では、次の使用ルールをサポートしています。

* 出力保護
* Adobe® AIR®、SWF、iOS、Android のアプリケーション制限
* DRM とランタイムモジュールの制限
* Jailbreak 検出の適用 (jailbreak 検出をサポートするAdobeアクセスプラットフォーム上 )
* ライセンスのキャッシュは、デフォルトで無効になっています。 ライセンスのキャッシュを有効にするには、キャッシュの終了日を指定するか、（ライセンス発行時から）キャッシュを許可する時間を指定します。
* 複数の再生権限。出力保護、アプリケーション制限、DRM/ランタイム制限の様々な組み合わせを指定できます。 例えば、DRM モジュールの制限と出力保護を使用して、クライアントプラットフォームごとに異なる出力保護要件を指定できます。

>[!NOTE]
>
>iOSデバイスへのリモートキー配信をサポートするには、パッケージ化時に使用されるポリシーでリモートキー配信が有効になっている必要があります。 この設定は、サーバーのテナント設定では変更できません。 ***Adobe Primetimeは、アクセスで保護されたAdobeコンテンツを再生できるiOSアプリケーションを構築するために必要です。***
