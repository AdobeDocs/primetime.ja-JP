---
description: 'null'
keywords: hard stop
seo-description: 'null'
seo-title: 設定プロパティ
title: 設定プロパティ
uuid: 216921d1-a9c1-4650-9dce-c025836986e5
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# 設定プロパティ{#configuration-properties}

<!--<a id="section_20A96CDCC5C340DEAF455C6E300E5712"></a>-->

>[!NOTE]
>
>を含むプロパティ名の場 `.n`合、は1 `n` で始まり、プロパティの各インスタンスで増加する整数を表します。 For example: `policy.license.customProp.n`.

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
   <td colname="2" class="- topic/entry "> 人間が読み取り可能なDRMポリシー名です。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.requireKeyServer</span> <p class="- topic/p "><span class="codeph"> -keyServer</span> <i class="+ topic/ph hi-d/i ">boolean</i> </p> </td> 
   <td colname="2" class="- topic/entry ">次の条件が適用されます。 
    <ul id="ul_AF4EBD6C19DC4DFAAB4756EF24BAC57D"> 
     <li id="li_6CC48ABF78EC426E9FC51458BD946BC9">trueの場合、iOSへのキー配信にはHTTPSキーサーバーが必要です。 </li> 
     <li id="li_63046A4ED7354C1E9E823B475E4AEFF7">指定しなかった場合、デフォルトはfalseです。 </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.enforceJailbreak</span> <p class="- topic/p "><span class="codeph"> -enforceJailbreak</span> <i class="+ topic/ph hi-d/i ">boolean</i> </p> </td> 
   <td colname="2" class="- topic/entry "> jailbreak検出をサポートするデバイスの場合、trueの場合、jailbreakが検出されたときの再生を許可しません。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.critical</span> <p class="- topic/p "><span class="codeph"> -critical</span> <i class="+ topic/ph hi-d/i ">boolean</i> </p> </td> 
   <td colname="2" class="- topic/entry ">DRMポリシーの重要度を設定します。 
    <ul id="ul_63F1994798894233A67AC4F8220AB642"> 
     <li id="li_D05DD9AD70464D6B9DB9DFF95846E589">trueの場合、サーバーはDRMポリシーのすべての部分（デフォルトの動作を表す）を理解する必要があります。 </li> 
     <li id="li_0211473DAF1F426787CC4A68F47643C6">falseの場合、サーバーは認識されないDRMポリシー属性を無視できます。 </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.chaining.asymmetric.certfile</span> </td> 
   <td colname="2" class="- topic/entry ">拡張ライセンスチェーンのルート暗号化キーの暗号化に公開鍵が使用されるライセンスサーバー <a href="https://help.adobe.com/en_US/primetime/drm/5.3/protecting_content/index.html#DRM-concept-Enhanced_License_Chaining" class="- topic/xref " format="http" scope="external"> 証明書です</a>。 このプロパティは、証明書のみを含むファイルを指定します。 <p>注意： PEM形式とDER形式の両方がサポートされています。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.chaining.rootKey</span> <p class="- topic/p "><span class="codeph"> -rootKey</span> <i class="+ topic/ph hi-d/i ">root-key</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p>拡張ライセンスチェーンのルート暗号 <a href="https://help.adobe.com/en_US/primetime/drm/5.3/protecting_content/index.html#DRM-concept-Enhanced_License_Chaining" class="- topic/xref " format="http" scope="external"> 化キーを指定します</a>。 キーが指定されておらず、拡張ライセンスチェーンが有効な場合、ランダムキーが自動的に生成されます。 </p> <p>キーは16バイトで、16進数値で指定する必要があります。 16進値の間の空白はオプションです。 更新の場合、コマンドラインオプションは使用できず、プロパティは無視されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.domain.url</span> <p class="- topic/p "><span class="codeph"> -domainURL</span> <i class="+ topic/ph hi-d/i ">url</i> </p> </td> 
   <td colname="2" class="- topic/entry ">ドメイン登録が必要な場合、 <i>url</i> はドメインサーバーのURLを指定します。 更新の場合、コマンドラインオプションは使用できず、プロパティは無視されます。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.domain.anonymous</span> <p class="- topic/p "><span class="codeph"> -domainAnon</span> </p> </td> 
   <td colname="2" class="- topic/entry ">匿名ドメインの登録を許可するかどうかを指定します。 プロパティをtrueに設定するか、匿名アクセスを許可するこのコマンドラインオプションを含めます。 <p>注意：このオプションは —domainAuthNSと共に使 <span class="codeph"> 用できません</span>。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.domain.authNamespace</span> <p class="- topic/p "><span class="codeph"> -domainAuthNS名前空</span><i class="+ topic/ph hi-d/i ">間</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p>ドメイン登録用の認証名前空間。 指定した場合、クライアントは、指定した権限によって発行されたユーザー名とパスワードを使用して認証を受ける必要があります。 </p> <p>更新の場合、コマンドラインオプションは使用できず、プロパティは無視されます。 </p> <p>注意：このオプションは —domainAnonと共に使用するこ <span class="codeph"> とはできません</span>。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.outputProtection.analog</span> <p class="- topic/p "><span class="codeph"> -opAnalog</span><i class="+ topic/ph hi-d/i ">AnalogOption</i> </p> </td> 
   <td colname="2" class="- topic/entry ">アナログ出力の保護の制約と、次の値がサポートされます。 
    <ul class="- topic/ul " id="ul_h4x_54y_n4"> 
     <li class="- topic/li " id="li_F920EC01159C4231AFBE579D487C8770"><span class="+ topic/ph pr-d/codeph codeph"> NO_PROTECTION</span> </li> 
     <li class="- topic/li " id="li_2DE0494AF8C446EB9E4567915F5E97C3"><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE</span> </li> 
     <li class="- topic/li " id="li_207D2D6256D6423FBDABA7A8627A9B7D"><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE_ACP</span> </li> 
     <li class="- topic/li " id="li_E17D944BED5F403FAE94708EE6AE4BBE"><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE_CGMSA</span> </li> 
     <li class="- topic/li " id="li_66D5A0C8FE154445A522D91EFB05B7ED"><span class="+ topic/ph pr-d/codeph codeph"> 必須</span> </li> 
     <li class="- topic/li " id="li_AF2024F212A249ED99AEECCF3E844A11"><span class="+ topic/ph pr-d/codeph codeph"> REQUIRED_ACP</span> </li> 
     <li class="- topic/li " id="li_FFF9B7DAE77740EE895EC35D1606A527"><span class="+ topic/ph pr-d/codeph codeph"> REQUIRED_CGMSA</span> </li> 
     <li class="- topic/li " id="li_52DED572F3AE495EB6A6450C611B440E"><span class="+ topic/ph pr-d/codeph codeph"> NO_PLAYBACK</span> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.drmVersionBlacklist.n</span> <p class="- topic/p "><span class="codeph"> -drmBlacklist</span><i class="+ topic/ph hi-d/i ">名前/値のペア</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p>保護されたコンテンツへのアクセスが制限されているDRMクライアント。 このオプションは、使用できないDRMモジュールのバージョンのリストを指定します（ブラックリスト）。 </p> <p>値は、次の形式のコンマ区切り <span class="codeph"> のname=value</span> 、ペアで構成されます。 </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> os|release|arch|model|vendor|env|screen=value</span> </p> <p class="- topic/p ">追加の名前と値のペアは、コンマで区切る必要があります。 例えば、 <span class="codeph"> os=Win,release=2.0,arch=32のようになります</span>。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.runtimeVersionBlacklist.n</span> <p class="- topic/p "><span class="codeph"> -runtimeBlacklist</span><i class="+ topic/ph hi-d/i ">名/値のペア</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p>アプリケーションの実行時に、保護されたコンテンツにアクセスできるように制限されています。 このオプションは、使用できないランタイムモジュールのバージョンのリスト（ブラックリスト）を指定します。 </p> <p>値は、次の形式のコンマ区切り <span class="codeph"> のname=value</span> 、ペアで構成されます。 </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> os|release|application|arch|model|vendor|env|screen=value</span> </p> <p class="- topic/p ">追加の名前と値のペアは、コンマで区切る必要があります。 例えば、 <span class="codeph"> os=Win,application=AIRとします</span>。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.v1DeviceCapabilities</span> <p class="- topic/p "><span class="codeph"> -devCapabilitiesV1</span> <i class="+ topic/ph hi-d/i ">name/value-pairs</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツにアクセスするために必要なデバイス機能を指定します。 値は、次の形式のコンマ区切り <span class="codeph"> のname=value</span> 、ペアで構成されます。 </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> nonUserAccessibleBus|hardwareRootOfTrust=true|false</span> </p> <p class="- topic/p ">例えば、 <span class="codeph"> nonUserAccessibleBus=false,hardwareRootOfTrust=trueとします</span>。 </p> <p>更新中に、デバイス機能の制限を解除する残りの引数を <span class="codeph"> 指定せずに</span> 、-devCapabilitiesV1を適用する必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.syncFrequency</span> <p class="- topic/p "><span class="codeph"> -sync</span> <i class="+ topic/ph hi-d/i ">name/value-pairs</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">クライアントが同期メッセージをサーバーに送信する必要がある頻度を指定します。 </p> <p>プロパティが設定されていない場合、クライアントはDRMポリシーで保護されたコンテンツを再生する際に同期メッセージを送信しません。 値は、次の形式のコンマ区切り <span class="codeph"> のname=value</span> 、ペアで構成されます。 </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> start|force=numberValue</span> </p> <p class="- topic/p ">オプションに関する追加情報を次に示します。 
     <ul id="ul_a5j_q4t_44"> 
      <li id="li_FD2C0C6DA19E455AA1917A56E09A7F84">（必須） <span class="codeph"> startは</span> 、最後の同期から指定された分以内にクライアントがサーバーとの同期を開始する必要があることを指定します。 </li> 
      <li id="li_9DEBC57385A442C3929AE3D0E3FA8992">（オプション） <span class="codeph"> force</span> は、再生中にクライアントが強制的に同期メッセージを送信する必要がある確率(0 ～ 100)です。 </li> 
     </ul>更新時に、残りの引数を <span class="codeph"> 指定せずに</span> -syncを使用して、同期要件を削除します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.useRootLicense</span> </td> 
   <td colname="2" class="- topic/entry ">このDRMポリシーにルートライセンスがあるかどうかを示します。 <p>詳しくは、拡張ライセンスチェーン <a href="https://help.adobe.com/en_US/primetime/drm/5.3/protecting_content/index.html#DRM-concept-Enhanced_License_Chaining" class="- topic/xref " format="http" scope="external"> を参照してください</a>。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.startDate</span> </td> 
   <td colname="2" class="- topic/entry ">コンテンツが有効になる日付。 次のいずれかの形式を適用できます。 
    <ul id="ul_6610B44D0C16485098F6F45DE3F151D7"> 
     <li id="li_986707D4C6164C44B3CCBE2EEB4C09B6"><span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd</span> <p>例えば、 <span class="codeph"> 2009-01-31は</span> 、1月31日の午前12:00を意味します。 </p> </li> 
     <li id="li_E15B782716124F6EAEFB04D16E5280DB"><span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd-h24:min:sec</span> <p>例えば、 <span class="codeph"> 2009-01-31-14:30:00は</span> 、1月31日の午後2時30分を意味します。 </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.expiration.endDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コンテンツが無効になる前の日付。 </p> <p>注意：policy.expiration.endDateと <span class="codeph"> policy.expiration.durationを同時に指定すること</span> はできません <span class="codeph"></span> 。 </p> <p>例えば、2009-01-31-14:30:00と指定すると、コンテンツの有効期限は1月31日の午後2時半に切れます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.expiration.duration</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コンテンツが無効になるまでの時間（分単位）。 時間は、コンテンツをパッケージ化する時点から始まります。 </p> <p>注意：policy.expiration.endDateと <span class="codeph"> policy.expiration.durationを同時に指定すること</span> はできません <span class="codeph"></span> 。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.licenseCaching.duration</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスがクライアント上でキャッシュされる時間（分単位）です。 このプロパティを0に設定すると、ライセンスのキャッシュを禁止できます。 0以上の値を指定する必要があります。 </p> <p>注意：policy.licenseCaching.durationと <span class="codeph"> policy.licenseCaching</span> .endDateを同時に指定することはできません <span class="codeph"></span> 。 </p> <p class="- topic/p ">このDRMポリシー設定は、ディスク上のライセンスキャッシュにのみ適用され、メモリキャッシュライセンスの期間は制御されません。 期間が0のDRMポリシーを指定しない場合でも、ライセンスはメモリ内にキャッシュできます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.licenseCaching.endDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">その日以降、ライセンスをキャッシュできなくなります。 </p> <p>注意：policy.licenseCaching.durationと <span class="codeph"> policy.licenseCaching</span> .endDateを同時に指定することはできません <span class="codeph"></span> 。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.anonymous</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">匿名ライセンスの取得を許可するかどうかを示します。 デフォルト値は <span class="codeph"> false</span>で、ユーザー名とパスワードが必要です。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.authNamespace</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ユーザー名とパスワードが必要な場合、このプロパティでは、ユーザー名の名前修飾子（オプション）を指定します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.customProp.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスの取得時にサーバーで使用されるカスタムの名前と値のペア。 次の形式を適用して、プロパティを指定できます。 <span class="+ topic/ph pr-d/codeph codeph">policy.customProp.n</span>=<span class="+ topic/ph pr-d/codeph codeph">name</span>=<span class="+ topic/ph pr-d/codeph codeph">value</span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.playbackWindow </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">再生ウィンドウを分単位で指定します。 この値は、保護されたコンテンツが最初に再生された後にライセンスが有効になる期間を表します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.outputProtection.digital</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">出力保護制約。次の値のいずれかである必要があります。 
     <ul id="ul_wsb_kfp_fs"> 
      <li id="li_FE012306F22F4F3FB981FE167C7A8B94"><span class="codeph"> NO_PROTECTION</span> </li> 
      <li id="li_A5591DC8983848FE9823C2A261BF7713"><span class="codeph"> USE_IF_AVAILABLE</span> </li> 
      <li id="li_74102C36ADE841C4B9ED71156E0A4C2C"><span class="codeph"> 必須</span> </li> 
      <li id="li_769E15C85B4E4DD48213DBD019D60BA7"><span class="codeph"> NO_PLAYBACK</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.outputProtection.ota</span> </td> 
   <td colname="2" class="- topic/entry ">ホワイトリストに登録する必要のあるOTA （空中）接続タイプを指定します。 有効な接続タイプは次のとおりです。 
    <ul id="ul_iz5_4fp_fs"> 
     <li id="li_FB07519EFEFE4B95B3B1F5BFD4DE6591"><span class="codeph"> 奇跡</span> </li> 
     <li id="li_51E7DE83679F4630B01264407DAD0E84"><span class="codeph"> 飛行</span> </li> 
     <li id="li_D499A0487AAC409CB2CEA6164265D3CF"><span class="codeph"> DLNA</span> </li> 
     <li id="li_4FCC0EC4A0FC48F99A13EC8A1B78D6A1"><span class="codeph"> WIDI</span> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.outputProtection.resolution</span> </td> 
   <td colname="2" class="- topic/entry "> 解像度ベースの制約を定義する設定ファイルを指定します。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.drmMinSecurityLevel</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">DRMモジュールが保護されたコンテンツにアクセスできるようにする最小のセキュリティレベルを指定します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.runtimeMinSecurityLevel</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">アプリケーションランタイムモジュールは、保護されたコンテンツにアクセスするために、少なくとも指定された最小セキュリティレベルを持つ必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.allowedAIRApplication.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Flash以外のアプリケーション（Adobe AIR、iOS、Androidなど）のホワイトリスト保護されたコンテンツの再生が許可されます。 このプロパティは次の形式を使用する必要があります。 <span class="+ topic/ph pr-d/codeph codeph">pubId</span>[:<span class="+ topic/ph pr-d/codeph codeph">appId</span>[:[<span class="+ topic/ph pr-d/codeph codeph">min</span>]:[<span class="+ topic/ph pr-d/codeph codeph"></span>maxId]] </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.allowedSWFApplication.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツの再生が許可されるSWFアプリケーションのホワイトリストです。 このプロパティは次の形式を使用する必要があります。 </p> <p class="- topic/p "> 
     <ul id="ul_EC20F52AD95C4BE3B7F703048A43CDF0"> 
      <li id="li_3E4A47D925C24834A2C25BC5943279D4"><span class="+ topic/ph pr-d/codeph codeph">URL</span> </li> 
      <li id="li_9A7CAF081C5F488FB5CDA6D38C5552F6"><span class="+ topic/ph pr-d/codeph codeph">file=swf_file</span> </li> 
      <li id="li_E10EA4223137489CBE4015DE999F7154"><span class="codeph">time=max_time_to_verify</span> </li> 
     </ul> <i class="+ topic/ph hi-d/i ">swf_fileは</i> 、ハッシュの計算に使用されるSWFファイルで、 <i class="+ topic/ph hi-d/i "></i> max_time_to_verifyは、SWFのダウンロードと検証が完了するまでの最大時間（秒）です。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.license.customProp.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスがユーザーに発行される際にライセンスに含める必要がある、カスタムの名前と値のペア。 次の形式を指定する必要があります。 </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph">policy.license.customProp.n=name</span> </p> <p class="- topic/p ">このオプションは、複数のカスタムプロパティに対して複数回定義できます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

