---
title: 保護されたストリーミング用の DRM サーバーの実行
description: 保護されたストリーミング用の DRM サーバーの実行
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '795'
ht-degree: 0%

---

# 保護されたストリーミング用の DRM サーバーの実行 {#running-the-drm-server-for-protected-streaming}

保護されたストリーミング用のAdobe Primetime DRM サーバーを起動する前に、設定ファイル内の設定の有効性を確認することをお勧めします。

ライセンスサーバーに付属のユーティリティを使用して、設定の有効性を確認できます。 ( 詳しくは、 *設定バリデーター* 」を参照してください。

Tomcat とライセンスサーバーを起動する場合は、を実行する必要があります。 [!DNL catalina.bat start] または [!DNL catalina.sh start] Tomcat の [!DNL bin] ディレクトリ。

サーバーが起動したら、 `https://<lic<span></span>ense-server-host:port>/flashaccessserver/<tenant-name>/flashaccess/license/v1` をクリックします。 テナント設定が正常に読み込まれた場合は、確認メッセージが表示されます。

## ログファイル {#log-files}

保護されたストリーミングアプリケーション用にAdobe Primetime DRM サーバーで生成されたログファイルは、LicenseServer.LogRoot で指定されたディレクトリにあります。

>[!NOTE]
>
>サーバーの実行中に現在のログファイルが削除または移動された場合、ログファイルは再作成できない場合があります。 したがって、一部のログ情報が削除される場合があります。

### ログディレクトリ構造 {#section_F490A483D60145ADBC21038914C39203}

ログディレクトリは使いやすく構造化されています。 ログディレクトリの構造は次のとおりです。

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

グローバルログファイル [!DNL flashaccess-global.log]は、次の場所にあります。 *LicenseServer.LogRoot*. ログには、Adobe Primetime DRM Java SDK またはログメッセージが、サーバーの初期化中に生成された可能性のあるログメッセージが含まれる場合があります。

### パーティションログファイル {#section_5660137CD6AA40519E72A4315534846B}

パーティション・ログ・ファイル [!DNL flashaccess-partition.log]は、 `<LicenseServer.LogRoot>/flashaccesserver` ディレクトリ。 これには、ライセンスリクエストの処理中に生成されたログメッセージが含まれます。

### テナントログファイル {#section_F0257CC0831647F18A746B4F02E3E910}

各テナントのテナントログファイル [!DNL flashaccess-tenant.log]は、次の場所にあります。 `<LicenseServer.LogRoot>/flashaccesserver/tenants/<tenantname>`. テナントログには、このテナントに対して生成される各ライセンスを説明する監査情報が含まれます。

## 設定ファイルの更新 {#updating-configuration-files}

ライセンスサーバがライセンスサーバの構成ファイル（グローバル構成またはテナント構成）の 1 つを読み取ると、その構成情報がメモリにキャッシュされます。 したがって、ライセンス要求ごとにファイルをディスクから読み取る必要はありません。 ただし、サーバーでは、変更を有効にするためにサーバーを再起動する必要なく、設定ファイル内のほとんどの値を変更することもできます。

設定ファイルを変更すると、ライセンスサーバにファイルが最後に変更された時刻が保存されます。 設定可能な間隔で、サーバーはファイルの変更時刻が変更されたかどうかを確認します。 変更された場合、サーバは設定ファイルの内容を自動的にリロードします。

サーバーが更新を確認する頻度を制御する場合は、 `refreshDelaySeconds` 属性 `Caching` グローバル設定ファイルの要素。 例えば、 `refreshDelaySeconds` が 3600 秒に設定されている場合、サーバーは設定ファイルの変更時から最大 1 時間以内に設定を更新します。 次の場合 `refreshDelaySeconds` が 0 に設定されている場合、サーバーはリクエストのたびに設定の更新を確認します。 次の設定はお勧めしません。 `refreshDelaySeconds` を任意の実稼動環境で低い値に設定すると、パフォーマンスに影響を与える可能性があるので、お勧めしません。

The `Caching` 要素は、一度にキャッシュされるテナントの設定の数も制御します。 この値をテナントの合計数より少ない数に設定すると、設定情報のキャッシュに使用するメモリの量を制限できます。 キャッシュにないテナントのリクエストを受け取った場合、リクエストを処理する前に設定が読み込まれます。 キャッシュがいっぱいの場合、最も古く使用されたテナントはキャッシュから削除されます。

次の状況（次回サーバーが更新を確認するまで）では、キャッシュされたバージョンの設定が引き続き使用されます。

* 変更が設定ファイルまたは [!DNL flashaccess-tenant.xml] ファイルを読み込もうとしている間にサーバがファイルを読み込む
* ファイルのタイムスタンプが現在の時刻より 1 秒前になっている場合
* ファイルのタイムスタンプが未来の場合

キャッシュされたバージョンがない場合、設定の読み込みに失敗し、エラーがクライアントに返されます。 その後、サーバーは、そのテナントに対する要求を次回受け取ったときに、ファイルの読み込みを再試行します。

### グローバル設定ファイルの更新 {#section_AA546C72442646CFB8906AEEBDF50587}

HSM パスワードは、 [!DNL flashaccess-global.xml] いつでも 変更は、次回サーバーが設定ファイルをリロードしたときに有効になります。 ただし、Logging 要素と Caching 要素に対する変更は再読み込みされません。 これらの要素に対する変更が有効になる前に、サーバーを再起動する必要があります。

### テナント設定ファイルの更新 {#section_71624DB8DF28480F84F34F0FF7FD4365}

指定した値をすべて変更できます。 [!DNL flashaccess-tenant.xml] ファイルをいつでも作成できます。 変更は、次回サーバーが設定ファイルをリロードしたときに有効になります。 また、サーバーは、すべての資格情報 ( [!DNL .pfx]) ファイルと、テナント設定ファイルで参照される packager許可リスト証明書ファイル。
