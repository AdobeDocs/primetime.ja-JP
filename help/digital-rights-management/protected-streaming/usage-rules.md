---
description: Adobe Primetime DRM Server for Protected Streamingを使用すると、設定ファイルを含むサーバー上のすべての使用ルールを指定できます。
seo-description: Adobe Primetime DRM Server for Protected Streamingを使用すると、設定ファイルを含むサーバー上のすべての使用ルールを指定できます。
seo-title: 使用ルールについて
title: 使用ルールについて
uuid: 4a794712-db58-43f5-b867-8871e58e12ae
translation-type: tm+mt
source-git-commit: 68f1318db89cf9422f5969f669c11f3784560db6

---


# 使用ルールについて{#about-usage-rules}

Adobe Primetime DRM Server for Protected Streamingを使用すると、設定ファイルを含むサーバー上のすべての使用ルールを指定できます。

保護されたコンテンツのDRMポリシーで指定された使用ルールはすべて上書きされます。 したがって、アドビでは、コンテンツのパッケージ化時にシンプルで匿名のDRMポリシーを使用することをお勧めします。 設定できる使用ルールは、テナントごとに設定できます。

保護されたストリーミング用のPrimetime DRMサーバーは、次の使用ルールをサポートしています。

* 出力保護
* Adobe® AIR®、SWF、iOSおよびAndroidアプリケーションの制限
* DRMおよびランタイムモジュールの制限
* jailbreak検出をサポートするPrimetime DRMプラットフォームでのJailbreak検出の強制
* ライセンスキャッシュはデフォルトで無効になっています。 キャッシュの終了日またはキャッシュの許容時間を指定することで有効にできるライセンスキャッシュ。ライセンスが発行されると開始されます。
* 複数の再生権限を持ち、出力保護、アプリケーションの制限およびDRM/ランタイムの制限の様々な組み合わせを指定できます。 例えば、出力保護に関するDRMモジュールの制限を使用して、各クライアントプラットフォームに異なる出力保護要件を指定できます。

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>iOSデバイスへのリモートキー配信をサポートする場合は、パッケージ化時に適用されるDRMポリシーでリモートキー配信を有効にする必要があります。 この設定は、サーバー上のテナントの構成で変更できません。

