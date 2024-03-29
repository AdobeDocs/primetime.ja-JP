---
description: ライセンスサーバーがライセンスサーバー構成ファイル（グローバル構成またはテナント構成）の1つを読み取るとすぐに、構成情報がメモリにキャッシュされます。 したがって、ライセンス要求ごとにファイルをディスクから読み込む必要はありません。 ただし、サーバーでは、設定ファイルのほとんどの値を変更できます。変更を有効にするためにサーバーを再起動する必要はありません。
title: 設定ファイルの更新
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 0%

---


# 構成ファイル{#updating-configuration-files}を更新中

ライセンスサーバーがライセンスサーバー構成ファイル（グローバル構成またはテナント構成）の1つを読み取るとすぐに、構成情報がメモリにキャッシュされます。 したがって、ライセンス要求ごとにファイルをディスクから読み込む必要はありません。 ただし、サーバーでは、設定ファイルのほとんどの値を変更できます。変更を有効にするためにサーバーを再起動する必要はありません。

設定ファイルを変更すると、ライセンスサーバにファイルが最後に変更された時間が保存されます。 設定可能な間隔で、サーバーはファイル変更時刻が変更されたかどうかを確認します。 変更した場合、サーバーは設定ファイルの内容を自動的に再読み込みします。

サーバーが更新をチェックする頻度を制御する場合は、グローバル設定ファイルの`Caching`要素に`refreshDelaySeconds`属性を設定する必要があります。 例えば、`refreshDelaySeconds`が3600秒に設定されている場合、サーバは設定ファイルの変更時刻から最大1時間以内に設定を更新します。 `refreshDelaySeconds`が0に設定されている場合、サーバは要求のたびに構成の更新をチェックします。 `refreshDelaySeconds`を実稼働環境では低い値に設定しないことをお勧めします。これは、パフォーマンスに影響を与える可能性があるためです。

また、`Caching`要素は、一度にキャッシュされるテナントの数も制御します。 この値をテナントの合計数より少ない数に設定して、設定情報のキャッシュに使用するメモリの量を制限できます。 キャッシュにないテナントに対する要求を受け取った場合、その設定は、要求を処理する前に読み込まれます。 キャッシュがいっぱいの場合、前回使用したテナントがキャッシュから削除されます。

次の状況（次回サーバーが更新をチェックするまで）では、キャッシュされたバージョンの設定が引き続き使用されます。

* サーバーがファイルの読み取りを試みる際に、変更が設定ファイルまたは[!DNL flashaccess-tenant.xml]ファイルで参照されている証明書ファイルのいずれかに保存された場合
* ファイルのタイムスタンプが現在の時刻より1秒未満であると判断された場合
* ファイルのタイムスタンプが未来の場合

キャッシュされたバージョンがない場合、設定の読み込みは失敗し、エラーがクライアントに返されます。 次に、サーバーは、そのテナントに対する要求を次回受け取ったときに、ファイルの読み込みを再試行します。

## グローバル構成ファイル{#section_AA546C72442646CFB8906AEEBDF50587}の更新

[!DNL flashaccess-global.xml]では、HSMパスワードをいつでも変更できます。 この変更は、次回サーバーが設定ファイルをリロードしたときに有効になります。 ただし、ログおよびキャッシュ要素に対する変更は再読み込みされません。 これらの要素に対する変更が有効になる前に、サーバーを再起動する必要があります。

## テナント構成ファイル{#section_71624DB8DF28480F84F34F0FF7FD4365}を更新しています

[!DNL flashaccess-tenant.xml]ファイルに指定されている値は、いつでも変更できます。 この変更は、次回サーバーが設定ファイルをリロードしたときに有効になります。 また、サーバーは、テナント構成ファイルで参照されているすべての資格情報([!DNL .pfx])ファイルとPackager許可リスト証明書ファイルに変更がないかを確認します。
