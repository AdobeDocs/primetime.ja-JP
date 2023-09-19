---
description: コンテンツのパッケージ化は、Web 上で再生するビデオコンテンツを準備するプロセスです。 パッケージ化には、生のビデオをマニフェストファイルに変換し、必要に応じて、デバイスやブラウザーごとに異なる DRM ソリューションを使用してコンテンツを暗号化する処理が含まれます。
title: コンテンツのパッケージ化
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---

# コンテンツのパッケージ化 {#package-your-content}

コンテンツのパッケージ化は、Web 上で再生するビデオコンテンツを準備するプロセスです。 パッケージ化には、生のビデオをマニフェストファイルに変換し、必要に応じて、デバイスやブラウザーごとに異なる DRM ソリューションを使用してコンテンツを暗号化する処理が含まれます。

コンテンツを準備するには、Adobeオフラインパッケージャまたは ExpressPlay の Bento4 パッケージャなどの他のツールを使用できます。 パッケージャーは、再生するビデオを準備し（元のファイルをフラグメント化してマニフェストに含めるなど）、選択した DRM ソリューション（PlayReady、Widevine、FairPlay、Access など）でビデオを保護します。:

* [Adobeオフラインパッケージャ](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf)
* [ExpressPlay パッケージャー](https://www.expressplay.com/developer/packaging-tools/)

<!--<a id="fig_jbn_fw5_xw"></a>-->

![](assets/pkg_lic_play_web.png)

1. 設定のテストに使用するコンテンツをパッケージ化するか、取得します。

   パッケージ化に関して覚えておくべき重要なポイントの 1 つは、このパッケージ化手順で使用するキー ID（コンテンツ ID）が、後続のライセンストークンリクエストで指定する必要があるものと同じである点です。 キー ID は、CEK を識別する唯一の項目です ( 独自のキー管理データベースに保存することも、 [ExpressPlay の Key Storage Service](https://www.expressplay.com/developer/key-storage/).

   >[!NOTE]
   >
   >Adobeアクセスに詳しい人にとって、これは異なるソリューションの動作の仕組みに関する重要な違いです。 Access では、ライセンスキーが DRM メタデータに埋め込まれ、保護されたコンテンツと共に繰り返し渡されます。 ここで説明する Multi-DRM システムでは、実際のライセンスは渡されず、安全に保存され、キー ID を介して取得されます。

<!--<a id="example_52AF76B730174B79B6088280FCDF126D"></a>-->

Widevine 用に Widevine Offline Packager を使用したAdobe化の例を以下に示します。 Packager は設定ファイル ( [!DNL widevine.xml]) は次のようになります。

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

* `in_path`  — このエントリは、ローカルパッケージングマシン上のソースビデオの場所を指します。
* `out_type`  — このエントリは、パッケージ化された出力のタイプを示します。この場合は DASH (HTML5 の Widevine 保護用 )。
* `out_path`  — 出力先のローカルマシン上の場所。
* `drm_sys`  — パッケージ化する DRM ソリューション。 次のいずれかになります。 `widevine`, `fairplay`または `playready`.

* `frag_dur` および `target_dur` は、ビデオの再生に関する DASH 固有の期間のエントリです。

* `key_file_path`  — これは、コンテンツ暗号化キー (CEK) として機能する、パッケージ化マシン上のライセンスファイルの場所です。 Base-64 でエンコードされた 16 バイトの 16 進文字列です。
* `widevine_content_id`  — これは Widevine の「ボイラープレート」です。常に `2a`. ( これを `widevine_key_id`.)

* `widevine_provider`  — 当社では、常に、次のように設定します。 `intertrust`.

* `widevine_key_id`  — これは、 `key_file_path` エントリ。 つまり、コンテンツの暗号化に使用するキーを識別します。 この ID は、自分で作成する 16 バイトの 16 進文字列です。

次に示すように、 [Packager のドキュメント](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf)「ベストプラクティスとして、出力の生成に使用する共通オプションを含む設定ファイルを作成します。 次に、特定のオプションをコマンドライン引数として指定して出力を作成します。」 この場合、設定ファイルは完全に完成しているので、次のように出力を作成できます。

```
java -jar OfflinePackager.jar -conf_path widevine.xml -out_path test_dash/ 
```

>[!NOTE]
>
>コマンドラインパラメータは、設定ファイルのパラメータよりも優先されます。 この例では、必要なものはすべて config ファイルに含まれていますが、config ファイルで指定された出力パスを `-out_path test_dash/`.
