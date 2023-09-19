---
title: 設定ファイルのプロパティ
description: 設定ファイルのプロパティ
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1119'
ht-degree: 0%

---

# 設定ファイルのプロパティ {#configuration-file-properties}

設定ファイルで、次のプロパティを指定します。 次を含むプロパティ名の場合： `n`, `n` は、プロパティの各インスタンスに対して 1 から始まり増加する整数を表します。

<table class="+ topic/table " id="table_p3x_54y_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> プロパティ/コマンドラインオプション </th> 
   <th colname="2" class="- topic/entry entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.name</span> <p class="- topic/p "><span class="codeph"> -n</span> <i class="+ topic/ph hi-d/i ">policyname</i> </p> </td> 
   <td colname="2" class="- topic/entry "> 人間が読み取り可能なポリシー名。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.requireKeyServer</span> <p class="- topic/p "><span class="codeph"> -keyServer</span> <i class="+ topic/ph hi-d/i ">ブール型</i> </p> </td> 
   <td colname="2" class="- topic/entry "> true の場合、iOSへのキー配信には HTTPS キーサーバーが必要です。 指定しない場合のデフォルトは false です。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.enforceJailbreak</span> <p class="- topic/p "><span class="codeph"> -enforceJailbreak</span> <i class="+ topic/ph hi-d/i ">ブール型</i> </p> </td> 
   <td colname="2" class="- topic/entry "> true の場合、jailbreak 検出をサポートするデバイスの場合、jailbreak が検出された場合は再生を許可しません。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.critical</span> <p class="- topic/p "><span class="codeph"> 重要な</span> <i class="+ topic/ph hi-d/i ">ブール型</i> </p> </td> 
   <td colname="2" class="- topic/entry "> ポリシーの重要度を設定します。 true の場合、サーバーはポリシーのすべての部分を理解する必要があります（これがデフォルトの動作です）。 false の場合、サーバーは理解できないポリシー属性を無視する場合があります。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.chaining.asymmetric.certfile</span> </td> 
   <td colname="2" class="- topic/entry ">公開鍵を使用してのルート暗号化キーを暗号化するライセンスサーバー証明書 <a href="../../../aaxs-protecting-content/content-introduction/content-usage-rules/content-other-policy-options/content-enhanced-license-chaining.md" format="dita" scope="local"> 拡張ライセンスチェーニング </a>
   このプロパティは、証明書のみを含むファイルを指定します（PEM または DER 形式が使用可能）。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.chaining.rootKey</span> <p class="- topic/p "><span class="codeph"> -rootKey</span> <i class="+ topic/ph hi-d/i ">root-key</i> </p> </td> 
   <td colname="2" class="- topic/entry "> 拡張ライセンスチェーンのルート暗号化キーを指定します。 キーが指定されておらず、拡張ライセンスチェーニングが有効になっている場合は、ランダムキーが生成されます。 キーの長さは 16 バイトで、16 進数値で指定する必要があります。 16 進数値の間の空白はオプションです。 更新の場合、コマンドラインオプションは許可されず、プロパティは無視されます。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.domain.url</span> <p class="- topic/p "><span class="codeph"> -domainURL</span> <i class="+ topic/ph hi-d/i ">url</i> </p> </td> 
   <td colname="2" class="- topic/entry "> ドメイン登録が必要な場合のドメインサーバーの URL。 更新の場合、コマンドラインオプションは許可されず、プロパティは無視されます。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.domain.anonymous</span> <p class="- topic/p "><span class="codeph"> -domainAnon</span> </p> </td> 
   <td colname="2" class="- topic/entry "> 匿名ドメイン登録を許可するかどうかを指定します。 プロパティを true に設定するか、このコマンドラインオプションを含めて匿名アクセスを許可します。 このオプションは、-domainAuthNS と一緒に使用することはできません。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.domain.authNamespace</span> <p class="- topic/p "><span class="codeph"> -domainAuthNS</span> <i class="+ topic/ph hi-d/i ">名前空間</i> </p> </td> 
   <td colname="2" class="- topic/entry "> ドメイン登録用の認証名前空間。 指定した場合、クライアントは、指定した権限が発行したユーザー名とパスワードを使用して認証する必要があります。 更新の場合、コマンドラインオプションは許可されず、プロパティは無視されます。 このオプションは —domainAnon と一緒に使用することはできません。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.outputProtection.analog</span> <p class="- topic/p "><span class="codeph"> -opAnalog</span> <i class="+ topic/ph hi-d/i ">AnalogOption</i> </p> </td> 
   <td colname="2" class="- topic/entry ">アナログ出力保護の制約。 次の値がサポートされています。 
    <ul class="- topic/ul " id="ul_h4x_54y_n4"> 
     <li class="- topic/li " id="li_5BC8F39B61894E83A7B27570FF848F09"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> NO_PROTECTION</span> </p> </li> 
     <li class="- topic/li " id="li_FF14594A0714480496793A82C3FA1610"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE</span> </p> </li> 
     <li class="- topic/li " id="li_721FCC4DC1F34AE398EFAE4C0D3F50F5"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE_ACP</span> </p> </li> 
     <li class="- topic/li " id="li_D588BB278BEE4CEAB034BD48550EBCDC"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE_CGMSA</span> </p> </li> 
     <li class="- topic/li " id="li_7E5F006D2F114502BA6D0A9C4173004E"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> 必須</span> </p> </li> 
     <li class="- topic/li " id="li_9EBFAA4AACF249C2A94432D88E12C3B9"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> 必須_ACP</span> </p> </li> 
     <li class="- topic/li " id="li_6720C6A085864BEB957C0BF2C38551C9"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> REQUIRED_CGMSA</span> </p> </li> 
     <li class="- topic/li " id="li_6FD98473ECDB4A66AC4B506FB9B3B360"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> NO_PLAYBACK</span> </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.drmVersionBlacklist.n</span> <p class="- topic/p "><span class="codeph"> -drmBlacklist</span> <i class="+ topic/ph hi-d/i ">名前と値のペア</i> </p> </td> 
   <td colname="2" class="- topic/entry ">DRM クライアントは保護されたコンテンツへのアクセスを制限しています。 このオプションは、使用できない DRM モジュールのバージョンのリストを指定します (ブロックリスト)。 値は、次の形式のコンマ区切りの name=value のペアで構成されます。 <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> os|release|arch|model|vendor|env|screen=value</span> </p> <p class="- topic/p ">追加の名前と値のペアは、コンマで区切る必要があります。 例： <span class="codeph"> os=Win,release=2.0,arch=32</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.runtimeVersionBlacklist.n</span> <p class="- topic/p "><span class="codeph"> -runtimeBlacklist</span> <i class="+ topic/ph hi-d/i ">名前と値のペア</i> </p> </td> 
   <td colname="2" class="- topic/entry ">保護されたコンテンツへのアクセスが制限されたアプリケーションランタイム。 このオプションは、使用できないランタイムモジュールのバージョンのリストを指定します (ブロックリスト)。 値は、次の形式のコンマ区切りの name=value のペアで構成されます。 <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> os|release|application|arch|model|vendor|env|screen=value</span> </p> <p class="- topic/p ">追加の名前と値のペアは、コンマで区切る必要があります。 例： <span class="codeph"> os=Win,application=AIR</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.v1DeviceCapabilities</span> <p class="- topic/p "><span class="codeph"> -devCapabilitiesV1</span> <i class="+ topic/ph hi-d/i ">名前と値のペア</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツへのアクセスに必要なデバイス機能を指定します。 値は、次の形式のコンマ区切りの name=value のペアで構成されます。 </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> nonUserAccessibleBus|hardwareRootOfTrust=true|false</span> </p> <p class="- topic/p ">例： <span class="codeph"> nonUserAccessibleBus=false,hardwareRootOfTrust=true</span>. 更新時に、 <span class="codeph"> -devCapabilitiesV1</span> デバイス機能の制限を削除する残りの引数がない場合。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.syncFrequency</span> <p class="- topic/p "><span class="codeph"> -sync</span> <i class="+ topic/ph hi-d/i ">名前と値のペア</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">クライアントが同期メッセージをサーバーに送信する際に必要な頻度を指定します。 設定しない場合、クライアントはこのポリシーで保護されたコンテンツを再生する際に同期メッセージを送信しません。 値はコンマ区切りで構成されます。 <span class="codeph"> name=value</span> のペアの形式は次のとおりです。 </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> start|force|hardStop=numberValue</span> </p> <p class="- topic/p "> 
     <ul id="ul_a5j_q4t_44"> 
      <li id="li_25CAF96C27F34848A95B2E3693847C71"><span class="codeph"> 開始</span> （必須） — 開始間隔は、最後の同期から数分間、クライアントがサーバーとの同期を開始する必要があることを指定します。 </li> 
      <li id="li_CC9068CFE75645029C947C9E1B53351F"><span class="codeph"> 強制</span> （オプション） — 強制同期の確率は、クライアントが再生中に同期メッセージを強制的に送信する確率 (0 ～ 100) です。 </li> 
      <li id="li_C31A6250F19348FBB8B7569D00C6314E"><span class="codeph"> hardStop</span> （オプション） — ハードストップ間隔とは、同期できない場合にクライアントが再生に失敗するまでの時間（分単位）です。 設定する場合は、開始間隔より大きい値を指定する必要があります。 </li> 
     </ul>更新時に、 <span class="codeph"> -sync</span> 同期要件を削除する残りの引数がない場合。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.useRootLicense</span> </td> 
   <td colname="2" class="- topic/entry ">このポリシーにルートライセンスがあるかどうかを示します ( <i class="+ topic/ph hi-d/i ">拡張ライセンスチェーニング</i> in <i class="+ topic/ph hi-d/i ">コンテンツの保護にAdobe・アクセスを使用</i>) をクリックします。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.startDate</span> </td> 
   <td colname="2" class="- topic/entry ">コンテンツが有効になる日付。 形式を使用 <span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd</span> ( 例： <span class="codeph"> 2009-01-31</span> は、 1 月 31 日（午前 0 時）を表します。または <span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd-h24:min:秒</span> ( 例： <span class="codeph"> 2009-01-31-14:30:00</span> は、1 月 31 日（午後 2 時 30 分）を表します。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.expiration.endDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コンテンツが有効な日付の前の日付。 両方 <span class="codeph"> policy.expiration.endDate</span> と policy.expiration.duration は同時に指定できません。 形式を使用 <span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd</span> または <span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd-h24:min:秒</span> ( 例：2009-01-31-14:30:00 は 1 月 31 日（午後 2 時 30 分）を表します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.expiration.duration</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コンテンツがパッケージ化されてから開始する、コンテンツが有効な時間（分単位）。 両方 <span class="codeph"> policy.expiration.endDate</span> および <span class="codeph"> policy.expiration.duration</span> は同時に指定できません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.licenseCaching.duration</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">クライアント上でライセンスがキャッシュされる時間（分単位）。 ライセンスのキャッシュを許可しない場合は、このプロパティを 0 に設定します。 0 以上の値を指定する必要があります。 両方 <span class="codeph"> policy.licenseCaching.duration</span> および <span class="codeph"> policy.licenseCaching.endDate</span> 同時に使用することはできません。 </p> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">注意</b>：このポリシー設定は、ディスク上のライセンスキャッシュにのみ適用されます。 メモリキャッシュライセンス期間は制御されません。 ポリシーで指定された期間がゼロであっても、ライセンスをメモリにキャッシュできます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.licenseCaching.endDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスをキャッシュできない日付。 両方 <span class="codeph"> policy.licenseCaching.duration</span> および <span class="codeph"> policy.licenseCaching.endDate</span> 同時に使用することはできません。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.anonymous</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">匿名ライセンスの取得を許可するかどうかを示します。 指定しない場合、デフォルトは「false」です（ユーザー名/パスワード認証が必要です）。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.authNamespace</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ユーザー名/パスワード認証が必要な場合、このプロパティはユーザー名の名前修飾子をオプションで指定します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.customProp.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスの取得時にサーバーで使用されるカスタムの名前と値のペア。 プロパティを指定するには、次の形式を使用します。 <span class="+ topic/ph pr-d/codeph codeph">policy.customProp.n</span>=<span class="+ topic/ph pr-d/codeph codeph">名前</span>=<span class="+ topic/ph pr-d/codeph codeph">値</span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.playbackWindow</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">再生ウィンドウ（分単位）を指定します。このウィンドウは、保護されたコンテンツの再生に初めて使用された後、ライセンスが有効である期間です。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.outputProtection.digital</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">出力保護の制約。 値は、次のいずれかである必要があります。 </p> <p class="- topic/p "><i class="+ topic/ph hi-d/i ">NO_PROTECTION, USE_IF_AVAILABLE, REQUIRED, NO_PLAYBACK</i> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.drmMinSecurityLevel</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">DRM モジュールは、保護されたコンテンツにアクセスするために、指定された最小セキュリティレベル以上である必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.runtimeMinSecurityLevel</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツにアクセスするには、アプリケーションランタイムモジュールのセキュリティレベルが、指定された最小レベル以上である必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.allowedAIRApplication.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Adobe AIRまたはiOSアプリケーションの許可リストで、保護されたコンテンツを再生できます。 プロパティでは次の形式を使用する必要があります。 <span class="+ topic/ph pr-d/codeph codeph">pubId</span>[:<span class="+ topic/ph pr-d/codeph codeph">appId</span>[:[<span class="+ topic/ph pr-d/codeph codeph">分</span>]:[<span class="+ topic/ph pr-d/codeph codeph">最大</span>]] </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.allowedSWFApplication.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツを再生できるSWFアプリケーションの許可リスト。 次の形式を使用します。 </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph">URL</span> または file=<span class="+ topic/ph pr-d/codeph codeph">swf_file</span>,time=<i class="+ topic/ph hi-d/i ">max_time_to_verify</i> <i class="+ topic/ph hi-d/i ">swf_file</i> は、SWFを計算するハッシュファイルで、 <i class="+ topic/ph hi-d/i ">max_time_to_verify</i> は、SWFのダウンロードと検証が完了するまでの最大時間（秒）です。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.license.customProp.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ユーザーに発行されるライセンスに含めるカスタムの名前と値のペア。 次の形式を使用します。 </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph">policy.license.customProp.n</span>=<span class="+ topic/ph pr-d/codeph codeph">名前</span>=<span class="+ topic/ph pr-d/codeph codeph">値</span> </p> <p class="- topic/p ">このオプションは、複数のカスタムプロパティに対して複数回定義できます。 </p> </td> 
  </tr> 
 </tbody> 
</table>
