---
seo-title: 設定ファイルのプロパティ
title: 設定ファイルのプロパティ
uuid: aec5fee7-4d77-4299-8d85-3e9042b2bbd1
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '1121'
ht-degree: 0%

---


# 設定ファイルのプロパティ {#configuration-file-properties}

設定ファイルでは、次のプロパティを指定します。 を含むプロパティ名の場合、 `n`は、1から始まり、プロパティの各インスタンスの増加する整数を `n` 表します。

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
   <td colname="2" class="- topic/entry "> 人間が読み取り可能なポリシー名です。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.requireKeyServer</span> <p class="- topic/p "><span class="codeph"> -keyServer</span> <i class="+ topic/ph hi-d/i ">boolean</i> </p> </td> 
   <td colname="2" class="- topic/entry "> trueの場合、iOSへのキーの配信にはHTTPSキーサーバーが必要です。 指定しない場合の初期設定はfalseです。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.enforceJailbreak</span> <p class="- topic/p "><span class="codeph"> -enforceJailbreak</span> <i class="+ topic/ph hi-d/i ">boolean</i> </p> </td> 
   <td colname="2" class="- topic/entry "> trueの場合、jailbreak検出をサポートするデバイスで、jailbreakが検出された場合は再生を許可しません。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.critical</span> <p class="- topic/p "><span class="codeph"> -critical</span> <i class="+ topic/ph hi-d/i ">boolean</i> </p> </td> 
   <td colname="2" class="- topic/entry "> ポリシーの重要度を設定します。 trueの場合、サーバーはポリシーのすべての部分を理解する必要があります（これがデフォルトの動作です）。 falseの場合、サーバーは、理解できないポリシー属性を無視する可能性があります。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.chaining.asymmetric.certfile</span> </td> 
   <td colname="2" class="- topic/entry ">拡張ライセンスチェーンのルート暗号化キーの暗号化に公開鍵が使用されるライセンスサーバー証明書 <a href="../../../aaxs-protecting-content/content-introduction/content-usage-rules/content-other-policy-options/content-enhanced-license-chaining.md" format="dita" scope="local"></a>このプロパティでは、証明書のみを含むファイルを指定します（PEM形式またはDER形式が使用できます）。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.chaining.rootKey</span> <p class="- topic/p "><span class="codeph"> -rootKey</span> <i class="+ topic/ph hi-d/i ">root-key</i> </p> </td> 
   <td colname="2" class="- topic/entry "> 拡張ライセンスチェーンのルート暗号化キーを指定します。 キーが指定されておらず、拡張ライセンスチェーンが有効な場合は、ランダムキーが生成されます。 キーは16バイトの長さで、16進数値で指定する必要があります。 16進数値の間に空白文字を入力することは省略可能です。 更新の場合、コマンドラインオプションは許可されず、プロパティは無視されます。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.domain.url</span> <p class="- topic/p "><span class="codeph"> -domainURL</span> <i class="+ topic/ph hi-d/i ">url</i> </p> </td> 
   <td colname="2" class="- topic/entry "> ドメイン登録が必要な場合の、ドメインサーバーのURL。 更新の場合、コマンドラインオプションは許可されず、プロパティは無視されます。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.domain.anonymous</span> <p class="- topic/p "><span class="codeph"> -domainAnon</span> </p> </td> 
   <td colname="2" class="- topic/entry "> 匿名ドメインの登録を許可するかどうかを指定します。 このプロパティをtrueに設定するか、このコマンドラインオプションを含めて匿名アクセスを許可します。 このオプションは —domainAuthNSでは使用できません。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.domain.authNamespace</span> <p class="- topic/p "><span class="codeph"> -domainAuthNS</span><i class="+ topic/ph hi-d/i ">名前空間</i> </p> </td> 
   <td colname="2" class="- topic/entry "> ドメイン登録の認証名前空間。 指定する場合、クライアントは、指定した機関が発行したユーザー名とパスワードを使用して認証を受ける必要があります。 更新の場合、コマンドラインオプションは許可されず、プロパティは無視されます。 このオプションは —domainAnonと共に使用することはできません。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.outputProtection.analog</span> <p class="- topic/p "><span class="codeph"> -opAnalog</span><i class="+ topic/ph hi-d/i ">AnalogOption</i> </p> </td> 
   <td colname="2" class="- topic/entry ">アナログ出力保護の制約。 次の値がサポートされています。 
    <ul class="- topic/ul " id="ul_h4x_54y_n4"> 
     <li class="- topic/li " id="li_5BC8F39B61894E83A7B27570FF848F09"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> NO_PROTECTION</span> </p> </li> 
     <li class="- topic/li " id="li_FF14594A0714480496793A82C3FA1610"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE</span> </p> </li> 
     <li class="- topic/li " id="li_721FCC4DC1F34AE398EFAE4C0D3F50F5"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE_ACP</span> </p> </li> 
     <li class="- topic/li " id="li_D588BB278BEE4CEAB034BD48550EBCDC"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE_CGMSA</span> </p> </li> 
     <li class="- topic/li " id="li_7E5F006D2F114502BA6D0A9C4173004E"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> 必須</span> </p> </li> 
     <li class="- topic/li " id="li_9EBFAA4AACF249C2A94432D88E12C3B9"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> REQUIRED_ACP</span> </p> </li> 
     <li class="- topic/li " id="li_6720C6A085864BEB957C0BF2C38551C9"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> REQUIRED_CGMSA</span> </p> </li> 
     <li class="- topic/li " id="li_6FD98473ECDB4A66AC4B506FB9B3B360"> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> NO_PLAYBACK</span> </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.drmVersionBlacklist.n</span> <p class="- topic/p "><span class="codeph"> -drmBlacklist</span><i class="+ topic/ph hi-d/i ">名/値のペア</i> </p> </td> 
   <td colname="2" class="- topic/entry ">DRMクライアントは保護されたコンテンツへのアクセスを制限されています。 このオプションは、使用できないDRMモジュールのリスト(ブロックリスト)を指定します。 値は、次の形式で名前=値のペアをカンマで区切って構成します。 <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> os|release|arch|model|vendor|env|screen=value</span> </p> <p class="- topic/p ">追加の名前と値のペアは、コンマで区切る必要があります。 次に例を示します。 <span class="codeph"> os=Win,release=2.0,arch=32</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.runtimeVersionBlacklist.n</span> <p class="- topic/p "><span class="codeph"> -runtimeBlacklist</span> <i class="+ topic/ph hi-d/i ">name/value-pairs</i> </p> </td> 
   <td colname="2" class="- topic/entry ">保護されたコンテンツへのアクセスが制限されたアプリケーション実行時。 このオプションは、使用できないランタイムモジュールのリスト(ブロックリスト)を指定します。 値は、次の形式で名前=値のペアをカンマで区切って構成します。 <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> os|release|application|arch|model|vendor|env|screen=value</span> </p> <p class="- topic/p ">追加の名前と値のペアは、コンマで区切る必要があります。 例えば、 <span class="codeph"> os=Win,application=AIR</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.v1DeviceCapabilities</span> <p class="- topic/p "><span class="codeph"> -devCapabilitiesV1</span><i class="+ topic/ph hi-d/i ">名前/値のペア</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツへのアクセスに必要なデバイス機能を指定します。 値は、次の形式で名前=値のペアをカンマで区切って構成します。 </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> nonUserAccessibleBus|hardwareRootOfTrust=true|false</span> </p> <p class="- topic/p ">例えば、 <span class="codeph"> nonUserAccessibleBus=false,hardwareRootOfTrust=true</span>. 更新時に、 <span class="codeph"> -devCapabilitiesV1</span> を使用し、残りの引数を指定しないで、デバイス機能の制限を解除します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.syncFrequency</span> <p class="- topic/p "><span class="codeph"> -sync</span> <i class="+ topic/ph hi-d/i ">name/value-pairs</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">同期メッセージをサーバーに送信するためにクライアントが必要とする頻度を指定します。 設定されていない場合、クライアントは、このポリシーで保護されたコンテンツを再生する際に同期メッセージを送信しません。 値は、次の形式を使用した <span class="codeph"> name=value</span> ペアのカンマ区切りで構成されます。 </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> 開始|force|hardStop=numberValue</span> </p> <p class="- topic/p "> 
     <ul id="ul_a5j_q4t_44"> 
      <li id="li_25CAF96C27F34848A95B2E3693847C71"><span class="codeph"> 開始</span> （必須） -開始間隔は、最後の同期から数分間、クライアントが開始とサーバと同期する必要があることを指定します。 </li> 
      <li id="li_CC9068CFE75645029C947C9E1B53351F"><span class="codeph"> force</span> （オプション） — 強制同期の確率は、クライアントが再生中に強制的に同期メッセージを送信する確率(0 ～ 100)です。 </li> 
      <li id="li_C31A6250F19348FBB8B7569D00C6314E"><span class="codeph"> hardStop</span> （オプション） — ハードストップ間隔は、同期できない場合にクライアントの再生が失敗するまでの時間（分単位）です。 設定する場合は、開始間隔より大きい値を指定する必要があります。 </li> 
     </ul>更新時に、残りの引数を指定しないで <span class="codeph"> -sync</span> を使用し、同期要件を削除します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.useRootLicense</span> </td> 
   <td colname="2" class="- topic/entry ">このポリシーにルートライセンスがあるかどうかを示します(「Adobe Accessを使用したコンテンツの保護 <i class="+ topic/ph hi-d/i ">」の「</i> 拡張ライセンスチェーン <i class="+ topic/ph hi-d/i ">」を参照</i>)。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.startDate</span> </td> 
   <td colname="2" class="- topic/entry ">コンテンツが有効になる日付です。 形式 <span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd</span> (例えば、2009-01-31 <span class="codeph"> は1月31日の午前12:00)または</span> yyyy-mm-dd-h24:min:sec <span class="+ topic/ph pr-d/codeph codeph">(例：</span><span class="codeph"></span> 2009-01-31-14:3)を使用します。0:00は、1月31日午後2時30分を表します)。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.expiration.endDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コンテンツが有効な日付の前。 policy.expiration.endDate <span class="codeph"></span> とpolicy.expiration.durationの両方を同時に指定することはできません。 形式 <span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd</span> または <span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd-h24:min:sec</span> （例えば、2009-01-31-14:30:00は1月31日の午後2:30を表します）を使用します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.expiration.duration</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コンテンツがパッケージ化されてから開始する、コンテンツが有効な時間（分）。 policy.expiration.endDate <span class="codeph"> と</span> policy.expiration.durationの両方を同時に指定することはできません <span class="codeph"></span> 。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.licenseCaching.duration</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスがクライアント上でキャッシュされる時間（分）。 このプロパティを0に設定すると、ライセンスのキャッシュが許可されません。 値は0以上に設定する必要があります。 policy.licenseCaching.duration <span class="codeph"> とpolicy.licenseCaching.endDateの両方を同時に使用することはできません</span><span class="codeph"></span> 。 </p> <p class="- topic/p "><b class="+ topic/ph hi-d/b ">注意</b>: このポリシー設定は、ディスク上のライセンスキャッシュにのみ適用されます。 メモリキャッシュライセンスの期間は制御されません。 ポリシーで指定された期間が0の場合でも、ライセンスはメモリにキャッシュできます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.licenseCaching.endDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">この日を過ぎると、ライセンスがキャッシュされない場合があります。 policy.licenseCaching.duration <span class="codeph"> とpolicy.licenseCaching.endDateの両方を同時に使用することはできません</span><span class="codeph"></span> 。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.anonymous</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">匿名ライセンスの取得を許可するかどうかを示します。 指定しない場合、デフォルトは「false」です（ユーザー名とパスワードの認証が必要です）。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.authNamespace</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ユーザー名/パスワード認証が必要な場合、このプロパティでは、ユーザー名の名前修飾子（オプション）を指定します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.customProp.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">サーバーがライセンスの取得時に使用するカスタムの名前と値のペア。 プロパティの指定には、次の形式を使用します。 <span class="+ topic/ph pr-d/codeph codeph">policy.customProp.n</span>=<span class="+ topic/ph pr-d/codeph codeph">name</span>=<span class="+ topic/ph pr-d/codeph codeph">value</span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.playbackWindow</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツの再生に初めて使用された後、ライセンスが有効となる時間を分単位で指定します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.outputProtection.digital</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">出力保護の制約。 値は、次のいずれかである必要があります。 </p> <p class="- topic/p "><i class="+ topic/ph hi-d/i ">NO_PROTECTION、USE_IF_AVAILABLE、REQUIRED、NO_PLAYBACK</i> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.drmMinSecurityLevel</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">DRMモジュールは、保護されたコンテンツにアクセスするために、指定した最小セキュリティレベル以上にする必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.runtimeMinSecurityLevel</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツにアクセスするには、アプリケーションランタイムモジュールのセキュリティレベルが最小限かそれ以上に設定されている必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.allowedAIRApplication.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツの再生が許可されるAdobe AIRまたはiOSアプリケーションの許可リスト。 このプロパティは次の形式を使用する必要があります。 <span class="+ topic/ph pr-d/codeph codeph">pubId</span>[:<span class="+ topic/ph pr-d/codeph codeph">appId</span>[:[<span class="+ topic/ph pr-d/codeph codeph">min</span>]:[<span class="+ topic/ph pr-d/codeph codeph">max</span>]]] </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.allowedSWFApplication.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツの再生が許可されるSWFアプリケーションの許可リストです。 次の形式を使用します。 </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph">URL</span> file=<span class="+ topic/ph pr-d/codeph codeph">swf_file</span>,time=<i class="+ topic/ph hi-d/i ">max_time_to_verify</i> swf_file <i class="+ topic/ph hi-d/i "></i><i class="+ topic/ph hi-d/i "></i> は、SWFのダウンロードと検証を完了する（秒単位）ハッシュ値と最大値を計算するSWFファイルです。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.license.customProp.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ユーザーに発行されるライセンスに含めるカスタム名と値のペア。 次の形式を使用します。 </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph">policy.license.customProp.n</span>=<span class="+ topic/ph pr-d/codeph codeph">name</span>=<span class="+ topic/ph pr-d/codeph codeph">value</span> </p> <p class="- topic/p ">このオプションは、複数のカスタムプロパティに対して複数回定義できます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

