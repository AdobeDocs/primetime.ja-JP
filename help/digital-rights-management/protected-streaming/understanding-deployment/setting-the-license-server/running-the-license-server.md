---
seo-title: 保護されたストリーミング用のDRMサーバーの実行
title: 保護されたストリーミング用のDRMサーバーの実行
uuid: 9bbe211d-268b-43c2-9e55-7ce62de40d30
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 0%

---


# 保護されたストリーミング用のDRMサーバーの実行 {#running-the-drm-server-for-protected-streaming}

保護されたストリーミング用のAdobe Primetime DRMサーバーを開始する前に、設定ファイルの設定の有効性を確認することをお勧めします。

ライセンスサーバーに付属のユーティリティを使用して、設定の有効性を確認できます。 (このガイドの *設定バリデーター* を参照してください。

Tomcatとライセンスサーバを開始する場合は、を実行する [!DNL catalina.bat start] か、Tomcatの [!DNL catalina.sh start] ディレクトリ [!DNL bin] からを実行する必要があります。

サーバーを起動した後、 [!DNL https://<lic<span></span>ense-server-host:port>/flashaccessserver/を開いて、サーバーが正しく設定されていることを確認する必要があります<tenant-name>/flashaccess/license/v1] （ブラウザーウィンドウ）。 テナント構成が正常に読み込まれた場合は、確認メッセージが表示されます。

## ログファイル {#log-files}

Adobe Primetime DRM Serverで保護されたストリーミングアプリケーション用に生成されるログファイルは、LicenseServer.LogRootで指定されたディレクトリにあります。

>[!NOTE] {class=&quot;- topic/note &quot;
>
>サーバーの実行中に現在のログファイルを削除または移動した場合、ログファイルは再作成できない場合があります。 したがって、一部のログ情報は削除される場合があります。

### ログディレクトリ構造 {#section_F490A483D60145ADBC21038914C39203}

ログディレクトリは使いやすいように構造化されています。 ログディレクトリの構造は次のとおりです。

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

グローバルログファイル [!DNL flashaccess-global.log]は、LicenseServer.LogRootにあり *ます*。 ログには、Adobe Primetime DRM Java SDKやログメッセージが生成されたログメッセージが含まれる場合があります。ログメッセージは、サーバーが初期化された時間に生成されたものです。

### パーティションログファイル {#section_5660137CD6AA40519E72A4315534846B}

パーティションログファイル [!DNL flashaccess-partition.log]は、 [!DNL <LicenseServer.LogRoot>/flashaccesserver] ディレクトリ内にあります。 これには、ライセンス要求の処理中に生成されたログメッセージが含まれます。

### テナントログファイル {#section_F0257CC0831647F18A746B4F02E3E910}

各テナントのテナントログファイル [!DNL flashaccess-tenant.log]は、 [!DNL &lt;LicenseServer.LogRoot>/flashaccessserver/tenants/にあります。<tenantname>]. テナントログには、このテナント用に生成された各ライセンスを説明する監査情報が含まれます。

## 設定ファイルの更新 {#updating-configuration-files}

ライセンスサーバーがライセンスサーバー構成ファイル（グローバル構成またはテナント構成）の1つを読み取るとすぐに、構成情報がメモリにキャッシュされます。 したがって、ライセンス要求ごとにファイルをディスクから読み込む必要はありません。 ただし、サーバーでは、設定ファイルのほとんどの値を変更できます。変更を有効にするためにサーバーを再起動する必要はありません。

設定ファイルを変更すると、ライセンスサーバにファイルが最後に変更された時間が保存されます。 設定可能な間隔で、サーバーはファイル変更時刻が変更されたかどうかを確認します。 変更した場合、サーバーは設定ファイルの内容を自動的に再読み込みします。

サーバーが更新をチェックする頻度を制御する場合は、グローバル設定ファイルの `refreshDelaySeconds``Caching` 要素に属性を設定する必要があります。 例えば、3600秒 `refreshDelaySeconds` に設定した場合、設定ファイルの変更時刻から最大1時間以内に、サーバーが設定を更新します。 0に設定 `refreshDelaySeconds` すると、サーバーは要求が発生するたびに設定の更新を確認します。 どの実稼働環境でも低い値 `refreshDelaySeconds` に設定することは推奨されません。これは、この設定がパフォーマンスに影響を与える可能性があるためです。

この `Caching` 要素は、一度にキャッシュされるテナントの設定の数も制御します。 この値をテナントの合計数より少ない数に設定して、設定情報のキャッシュに使用するメモリの量を制限できます。 キャッシュにないテナントに対する要求を受け取った場合、その設定は、要求を処理する前に読み込まれます。 キャッシュがいっぱいの場合、前回使用したテナントがキャッシュから削除されます。

次の状況（次回サーバーが更新をチェックするまで）では、キャッシュされたバージョンの設定が引き続き使用されます。

* サーバーがファイルの読み取りを試行したときに、変更が設定ファイルまたは [!DNL flashaccess-tenant.xml] ファイル内で参照されている証明書ファイルのいずれかに保存された場合
* ファイルのタイムスタンプが現在の時刻より1秒未満であると判断された場合
* ファイルのタイムスタンプが未来の場合

キャッシュされたバージョンがない場合、設定の読み込みは失敗し、エラーがクライアントに返されます。 次に、サーバーは、そのテナントに対する要求を次回受け取ったときに、ファイルの読み込みを再試行します。

### グローバル設定ファイルの更新 {#section_AA546C72442646CFB8906AEEBDF50587}

HSMパスワードは、いつでも変更 [!DNL flashaccess-global.xml] できます。 この変更は、次回サーバーが設定ファイルをリロードしたときに有効になります。 ただし、ログおよびキャッシュ要素に対する変更は再読み込みされません。 これらの要素に対する変更が有効になる前に、サーバーを再起動する必要があります。

### テナント構成ファイルを更新しています {#section_71624DB8DF28480F84F34F0FF7FD4365}

フ [!DNL flashaccess-tenant.xml] ァイルで指定されているすべての値は、いつでも変更できます。 この変更は、次回サーバーが設定ファイルをリロードしたときに有効になります。 また、サーバーは、テナント構成ファイルで参照されているすべての資格情報( [!DNL .pfx])ファイルとPackager許可リスト証明書ファイルに変更がないかを確認します。