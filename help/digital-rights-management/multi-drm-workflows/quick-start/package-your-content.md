---
description: コンテンツのパッケージ化は、Web上で再生するビデオコンテンツを準備するプロセスです。 パッケージ化には、生のビデオをマニフェストファイルに変換し、オプションで、デバイスやブラウザーごとに異なるDRMソリューションを使用してコンテンツを暗号化する機能が含まれます。
seo-description: コンテンツのパッケージ化は、Web上で再生するビデオコンテンツを準備するプロセスです。 パッケージ化には、生のビデオをマニフェストファイルに変換し、オプションで、デバイスやブラウザーごとに異なるDRMソリューションを使用してコンテンツを暗号化する機能が含まれます。
seo-title: コンテンツのパッケージ化
title: コンテンツのパッケージ化
uuid: b9bc6104-a1ea-4ea0-a0a4-af8a606e5d47
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# コンテンツのパッケージ化 {#package-your-content}

コンテンツのパッケージ化は、Web上で再生するビデオコンテンツを準備するプロセスです。 パッケージ化には、生のビデオをマニフェストファイルに変換し、オプションで、デバイスやブラウザーごとに異なるDRMソリューションを使用してコンテンツを暗号化する機能が含まれます。

コンテンツを準備するには、Adobe Offline PackagerまたはExpressPlayのBento4パッケージャーなどの他のツールを使用できます。 パッケージャーは、再生するビデオを準備（元のファイルをフラグメント化してマニフェストに含めるなど）し、選択したDRMソリューション（PlayReady、Widevine、FairPlay、Accessなど）でビデオを保護します。:

* [Adobe Offline Packager](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf)
* [ExpressPlay Packager](https://www.expressplay.com/developer/packaging-tools/)

<!--<a id="fig_jbn_fw5_xw"></a>-->

![](assets/pkg_lic_play_web.png)

1. 設定のテストに使用するコンテンツをパッケージ化するか、取得します。

   パッケージ化の重要なポイントの1つは、このパッケージ化手順で使用するキーID（コンテンツID）が、後続のライセンストークンリクエストで指定する必要があるものと同じであることです。 キーIDは、CEKを識別する唯一の項目です(CEKは、独自のキー管理データベースに保存するか、 [ExpressPlayのKey Storage Serviceを使用して保存します](https://www.expressplay.com/developer/key-storage/))。

   >[!NOTE]
   >
   >Adobe Accessに詳しい方にとって、これは各ソリューションの動作方法に関する重要な違いです。 Accessでは、ライセンスキーはDRMメタデータに埋め込まれ、保護されたコンテンツと共に送受信されます。 ここで説明するMulti-DRMシステムでは、実際のライセンスは渡されず、安全に保存され、キーIDを介して取得されます。

<!--<a id="example_52AF76B730174B79B6088280FCDF126D"></a>-->

Widevine用にAdobe Offline Packagerを使用したパッケージ化の例を次に示します。 Packagerでは設定ファイル(例： [!DNL widevine.xml])が使用され、次のようになります。

```
<config> 
<in_path>sample.mp4</in_path> 
<out_type>dash</out_type> 
<out_path>dash2</out_path> 
<drm/> 
<drm_sys>widevine</drm_sys> 
<frag_dur>4</frag_dur> 
<target_dur>6</target_dur> 
<key_file_path>keyfile.bin</key_file_path> 
<widevine_content_id>2a</widevine_content_id> 
<widevine_provider>intertrust</widevine_provider> 
<widevine_key_id>7debe705d938c76bfd886f077b8fa5f7</widevine_key_id> 
</config>
```

* `in_path`  — このエントリは、ローカルのパッケージ化コンピューター上のソースビデオの場所を指します。
* `out_type`  — このエントリは、パッケージ化された出力のタイプを示します。この場合はDASH（HTML5でのWidevine保護の場合）。
* `out_path`  — 出力先のローカルマシン上の場所。
* `drm_sys`  — パッケージ化するDRMソリューション。 これは、、また `widevine`はのい `fairplay`ずれかで `playready`す。

* `frag_dur` とは、 `target_dur` ビデオ再生に関連するDASH固有の期間エントリです。

* `key_file_path`  — これは、コンテンツ暗号化キー(CEK)として機能するパッケージ化コンピューター上のライセンスファイルの場所です。 これは、Base-64エンコードされた16バイトの16進文字列です。
* `widevine_content_id`  — これはWidevineの&quot;boilerplate&quot;;いつもだ `2a`。 (と混同しないでくだ `widevine_key_id`さい)。

* `widevine_provider`  — この場合、常にをに設定します `intertrust`。

* `widevine_key_id`  — エントリで指定したライセンスの識別子 `key_file_path` です。 つまり、コンテンツの暗号化に使用するキーを識別します。 このIDは、自分で作成する16バイトの16進文字列です。

[Packagerのドキュメントに記載されているように](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf)、「ベストプラクティスとして、出力の生成に使用する一般的なオプションを含む設定ファイルを作成します。 次に、特定のオプションをコマンドライン引数として指定して、出力を作成します。」 この場合、設定ファイルは十分に完成しているので、次のように出力を作成できます。

```
java -jar OfflinePackager.jar -conf_path widevine.xml -out_path test_dash/ 
```

>[!NOTE]
>
>コマンドラインパラメータは、設定ファイルのパラメータよりも優先されます。 この例では、必要なものはすべてconfigファイルに含まれていますが、設定ファイルで指定された出力パスをによって上書きしま `-out_path test_dash/`す。

