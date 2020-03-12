---
seo-title: 保護されたストリーミング用のDRMサーバーの実行
title: 保護されたストリーミング用のDRMサーバーの実行
uuid: 9bbe211d-268b-43c2-9e55-7ce62de40d30
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# 保護されたストリーミング用のDRMサーバーの実行 {#running-the-drm-server-for-protected-streaming}

Adobe Primetime DRM Server for Protected Streamingを起動する前に、設定ファイルの設定の有効性を確認することをお勧めします。

ライセンスサーバーに付属のユーティリティを使用して、設定の有効性を確認できます。 (このガイド *の設定バリデータ* ーを参照してください。

Tomcatとライセンスサーバーを起動する場合は、またはTomcatのディレクト [!DNL catalina.bat start] リか [!DNL catalina.sh start] らを実行する必要があり [!DNL bin] ます。

サーバーの起動後、 [!DNL https://<lic<span></span>ense-server-host:port>/flashaccessserver/を開いて、サーバーが正しく設定されていることを確認する必要があります<tenant-name>/flashaccess/license/v1を参照してください] 。 テナント構成が正常に読み込まれた場合は、確認メッセージが表示されます。

## ログファイル {#log-files}

Adobe Primetime DRM Serverで保護されたストリーミングアプリケーション用に生成されたログファイルは、LicenseServer.LogRootで指定されたディレクトリにあります。

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>サーバーの実行中に現在のログファイルが削除または移動された場合、ログファイルは再作成できない場合があります。 そのため、一部のログ情報は削除される場合があります。

### ログディレクトリの構造 {#section_F490A483D60145ADBC21038914C39203}

ログディレクトリは、使いやすさを考慮した構造になっています。 ログディレクトリの構造は次のとおりです。

```
<i class="+ topic ph hi-d="" i "="">
 LicenseServer.LogRoot/ 
 flashaccess-global.log 
     flashaccessserver/ 
         flashaccess-partition.log 
         tenants/ 
             
 <i class="+ topic ph hi-d="" i "="">
  tenantname/ 
                  flashaccess-tenant.log
 </i class="+ topic>
</i class="+ topic>
```

### グローバルログファイル {#section_1CFA90748142439C9F3BE380969539DA}

グローバルログファイル [!DNL flashaccess-global.log]は、 *LicenseServer.LogRootにあります*。 ログには、Adobe Primetime DRM Java SDKを使用したログメッセージや、サーバーの初期化時に生成されたログメッセージが含まれる場合があります。

### パーティションログファイル {#section_5660137CD6AA40519E72A4315534846B}

パーティション・ログ・ファ [!DNL flashaccess-partition.log]イルは、ディレクトリ内にあ [!DNL <LicenseServer.LogRoot>/flashaccesserver] ります。 ライセンス要求の処理中に生成されたログメッセージが含まれます。

### テナントログファイル {#section_F0257CC0831647F18A746B4F02E3E910}

各テナントのテナントログフ [!DNL flashaccess-tenant.log]ァイルは、 [!DNL &lt;LicenseServer.LogRoot>/flashaccesserver/tenants/にあります。<tenantname>]. テナントログには、このテナントに対して生成された各ライセンスを説明する監査情報が含まれます。

## 設定ファイルの更新 {#updating-configuration-files}

ライセンスサーバーがライセンスサーバーの設定ファイル（グローバル設定またはテナント設定）の1つを読み取るとすぐに、設定情報がメモリにキャッシュされます。 したがって、ライセンス要求ごとにファイルをディスクから読み取る必要はありません。 ただし、サーバーでは、設定ファイルのほとんどの値を変更することもできます。変更を有効にするためにサーバーを再起動する必要はありません。

設定ファイルを変更すると、ライセンスサーバにはそのファイルが最後に変更された時刻が保存されます。 設定可能な間隔で、サーバーはファイルの変更時刻が変更されたかどうかを確認します。 変更された場合、サーバーは設定ファイルの内容を自動的に再読み込みします。

サーバーが更新をチェックする頻度を制御する場合は、グローバル設定ファイルの要 `refreshDelaySeconds` 素に属性を設 `Caching` 定する必要があります。 例えば、を3600 `refreshDelaySeconds` 秒に設定した場合、サーバーは設定ファイルの変更時刻から1時間以内に設定を更新します。 を0に設 `refreshDelaySeconds` 定すると、サーバーは要求のたびに設定の更新を確認します。 どの実稼働環境でも低い値を設定するこ `refreshDelaySeconds` とは推奨されません。これは、パフォーマンスに影響を与える可能性があるためです。

この要素 `Caching` は、一度にキャッシュされるテナントの設定の数も制御します。 この値をテナントの合計数より少ない値に設定して、設定情報のキャッシュに使用するメモリの量を制限できます。 キャッシュにないテナントに対する要求を受け取った場合、要求を処理する前に設定が読み込まれます。 キャッシュがいっぱいの場合、最も長く使用されたテナントはキャッシュから削除されます。

キャッシュされたバージョンの設定は、次の状況（次にサーバーが更新をチェックするまで）でも引き続き使用されます。

* サーバーがファイルの読み取りを試みる際に、変更が設定ファイルまたはファイル内で参照されてい [!DNL flashaccess-tenant.xml] る証明書ファイルに保存された場合
* ファイルのタイムスタンプが現在の時刻より1秒前であることが判明した場合
* ファイルのタイムスタンプが将来的に設定される場合

キャッシュされたバージョンがない場合、設定の読み込みは失敗し、エラーがクライアントに返されます。 次に、サーバーは、そのテナントに対する要求を次に受け取ったときに、ファイルの読み込みを再試行します。

### グローバル設定ファイルの更新 {#section_AA546C72442646CFB8906AEEBDF50587}

HSMパスワードは、いつでも変更 [!DNL flashaccess-global.xml] できます。 この変更は、次にサーバーが設定ファイルを再読み込みしたときに有効になります。 ただし、Logging要素とCaching要素に対する変更は再読み込みされません。 これらの要素に対する変更が有効になる前に、サーバーを再起動する必要があります。

### テナント構成ファイルの更新 {#section_71624DB8DF28480F84F34F0FF7FD4365}

ファイルで指定されたすべての値は、いつで [!DNL flashaccess-tenant.xml] も変更できます。 この変更は、次にサーバーが設定ファイルを再読み込みしたときに有効になります。 また、サーバーは、すべての秘密鍵証明書( [!DNL .pfx])ファイルと、テナント設定ファイルで参照されているパッケージャーのホワイトリスト証明書ファイルに変更がないかを確認します。