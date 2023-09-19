---
keywords: ハードストップ
title: 設定プロパティ
description: 設定プロパティ
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1217'
ht-degree: 0%

---

# 設定プロパティ {#configuration-properties}

<!--<a id="section_20A96CDCC5C340DEAF455C6E300E5712"></a>-->

>[!NOTE]
>
>次を含むプロパティ名の場合： `.n`、 `n` は、プロパティの各インスタンスに対して 1 から始まり増加する整数を表します。 例： `policy.license.customProp.n`.

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
   <td colname="2" class="- topic/entry "> 人間が読み取り可能な DRM ポリシー名。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.requireKeyServer</span> <p class="- topic/p "><span class="codeph"> -keyServer</span> <i class="+ topic/ph hi-d/i ">ブール型</i> </p> </td> 
   <td colname="2" class="- topic/entry ">次の条件が当てはまります。 
    <ul id="ul_AF4EBD6C19DC4DFAAB4756EF24BAC57D"> 
     <li id="li_6CC48ABF78EC426E9FC51458BD946BC9">true の場合、iOSへのキー配信には HTTPS キーサーバーが必要です。 </li> 
     <li id="li_63046A4ED7354C1E9E823B475E4AEFF7">指定しない場合、デフォルトは false です。 </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.enforceJailbreak</span> <p class="- topic/p "><span class="codeph"> -enforceJailbreak</span> <i class="+ topic/ph hi-d/i ">ブール型</i> </p> </td> 
   <td colname="2" class="- topic/entry "> jailbreak 検出をサポートするデバイスの場合、true の場合は、jailbreak が検出されたときの再生を許可しません。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.critical</span> <p class="- topic/p "><span class="codeph"> 重要な</span> <i class="+ topic/ph hi-d/i ">ブール型</i> </p> </td> 
   <td colname="2" class="- topic/entry ">DRM ポリシーの重要度を設定します。 
    <ul id="ul_63F1994798894233A67AC4F8220AB642"> 
     <li id="li_D05DD9AD70464D6B9DB9DFF95846E589">true の場合、サーバーは DRM ポリシーのすべての部分（デフォルトの動作を表す）を理解する必要があります。 </li> 
     <li id="li_0211473DAF1F426787CC4A68F47643C6">false の場合、サーバーは認識されない DRM ポリシー属性を無視できます。 </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.chaining.asymmetric.certfile</span> </td> 
   <td colname="2" class="- topic/entry ">公開鍵を使用してのルート暗号化キーを暗号化するライセンスサーバー証明書 <a href="https://help.adobe.com/en_US/primetime/drm/5.3/protecting_content/index.html#DRM-concept-Enhanced_License_Chaining" class="- topic/xref " format="http" scope="external"> 拡張ライセンスチェーニング</a>. このプロパティは、証明書のみを含むファイルを指定します。 <p>注意： PEM 形式と DER 形式の両方がサポートされます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.chaining.rootKey</span> <p class="- topic/p "><span class="codeph"> -rootKey</span> <i class="+ topic/ph hi-d/i ">root-key</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p>のルート暗号化キーを指定します。 <a href="https://help.adobe.com/en_US/primetime/drm/5.3/protecting_content/index.html#DRM-concept-Enhanced_License_Chaining" class="- topic/xref " format="http" scope="external"> 拡張ライセンスチェーニング</a>. キーが指定されておらず、拡張ライセンスチェーニングが有効になっている場合、ランダムキーが自動的に生成されます。 </p> <p>キーの長さは 16 バイトで、16 進数値で指定する必要があります。 16 進数値の間の空白はオプションです。 更新の場合、コマンドラインオプションは使用できず、プロパティは無視されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.domain.url</span> <p class="- topic/p "><span class="codeph"> -domainURL</span> <i class="+ topic/ph hi-d/i ">url</i> </p> </td> 
   <td colname="2" class="- topic/entry ">ドメイン登録が必要な場合は、 <i>url</i> ドメインサーバーの URL を指定します。 更新の場合、コマンドラインオプションは使用できず、プロパティは無視されます。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.domain.anonymous</span> <p class="- topic/p "><span class="codeph"> -domainAnon</span> </p> </td> 
   <td colname="2" class="- topic/entry ">匿名ドメイン登録を許可するかどうかを指定します。 プロパティを true に設定するか、このコマンドラインオプションを含めて匿名アクセスを許可します。 <p>注意：このオプションは、 <span class="codeph"> -domainAuthNS</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.domain.authNamespace</span> <p class="- topic/p "><span class="codeph"> -domainAuthNS</span> <i class="+ topic/ph hi-d/i ">名前空間</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p>ドメイン登録用の認証名前空間。 指定した場合、クライアントは、指定した権限が発行したユーザー名とパスワードを使用して認証する必要があります。 </p> <p>更新の場合、コマンドラインオプションは使用できず、プロパティは無視されます。 </p> <p>注意：このオプションは、 <span class="codeph"> -domainAnon</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.outputProtection.analog</span> <p class="- topic/p "><span class="codeph"> -opAnalog</span> <i class="+ topic/ph hi-d/i ">AnalogOption</i> </p> </td> 
   <td colname="2" class="- topic/entry ">アナログ出力保護の制約と、次の値がサポートされます。 
    <ul class="- topic/ul " id="ul_h4x_54y_n4"> 
     <li class="- topic/li " id="li_F920EC01159C4231AFBE579D487C8770"><span class="+ topic/ph pr-d/codeph codeph"> NO_PROTECTION</span> </li> 
     <li class="- topic/li " id="li_2DE0494AF8C446EB9E4567915F5E97C3"><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE</span> </li> 
     <li class="- topic/li " id="li_207D2D6256D6423FBDABA7A8627A9B7D"><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE_ACP</span> </li> 
     <li class="- topic/li " id="li_E17D944BED5F403FAE94708EE6AE4BBE"><span class="+ topic/ph pr-d/codeph codeph"> USE_IF_AVAILABLE_CGMSA</span> </li> 
     <li class="- topic/li " id="li_66D5A0C8FE154445A522D91EFB05B7ED"><span class="+ topic/ph pr-d/codeph codeph"> 必須</span> </li> 
     <li class="- topic/li " id="li_AF2024F212A249ED99AEECCF3E844A11"><span class="+ topic/ph pr-d/codeph codeph"> 必須_ACP</span> </li> 
     <li class="- topic/li " id="li_FFF9B7DAE77740EE895EC35D1606A527"><span class="+ topic/ph pr-d/codeph codeph"> REQUIRED_CGMSA</span> </li> 
     <li class="- topic/li " id="li_52DED572F3AE495EB6A6450C611B440E"><span class="+ topic/ph pr-d/codeph codeph"> NO_PLAYBACK</span> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.drmVersionBlacklist.n</span> <p class="- topic/p "><span class="codeph"> -drmBlacklist</span> <i class="+ topic/ph hi-d/i ">名前と値のペア</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p>保護されたコンテンツへのアクセスが制限されている DRM クライアント。 このオプションは、使用できない DRM モジュールのバージョンのリストを指定します (ブロックリスト)。 </p> <p>値はコンマ区切りで構成されます。 <span class="codeph"> name=value</span> のペアは次の形式で指定します。 </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> os|release|arch|model|vendor|env|screen=value</span> </p> <p class="- topic/p ">追加の名前と値のペアは、コンマで区切る必要があります。 例： <span class="codeph"> os=Win,release=2.0,arch=32</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.runtimeVersionBlacklist.n</span> <p class="- topic/p "><span class="codeph"> -runtimeBlacklist</span> <i class="+ topic/ph hi-d/i ">名前と値のペア</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p>アプリケーションのランタイムは、保護されたコンテンツへのアクセスを制限されます。 このオプションは、使用できないランタイムモジュールのバージョンのリストを指定します (ブロックリスト)。 </p> <p>値はコンマ区切りで構成されます。 <span class="codeph"> name=value</span> のペアは次の形式で指定します。 </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> os|release|application|arch|model|vendor|env|screen=value</span> </p> <p class="- topic/p ">追加の名前と値のペアは、コンマで区切る必要があります。 例： <span class="codeph"> os=Win,application=AIR</span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.v1DeviceCapabilities</span> <p class="- topic/p "><span class="codeph"> -devCapabilitiesV1</span> <i class="+ topic/ph hi-d/i ">名前と値のペア</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツへのアクセスに必要なデバイス機能を指定します。 値はコンマ区切りで構成されます。 <span class="codeph"> name=value</span> のペアは次の形式で指定します。 </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> nonUserAccessibleBus|hardwareRootOfTrust=true|false</span> </p> <p class="- topic/p ">例： <span class="codeph"> nonUserAccessibleBus=false,hardwareRootOfTrust=true</span>. </p> <p>更新中に、 <span class="codeph"> -devCapabilitiesV1</span> デバイス機能の制限を削除する残りの引数がない </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.syncFrequency</span> <p class="- topic/p "><span class="codeph"> -sync</span> <i class="+ topic/ph hi-d/i ">名前と値のペア</i> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">クライアントが同期メッセージをサーバーに送信する際に必要な頻度を指定します。 </p> <p>プロパティが設定されていない場合、DRM ポリシーで保護されたコンテンツを再生する際に、クライアントは同期メッセージを送信しません。 値はコンマ区切りで構成されます。 <span class="codeph"> name=value</span> のペアは次の形式で指定します。 </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph"> start|force=numberValue</span> </p> <p class="- topic/p ">次のリストに、オプションに関する追加情報を示します。 
     <ul id="ul_a5j_q4t_44"> 
      <li id="li_FD2C0C6DA19E455AA1917A56E09A7F84">（必須） <span class="codeph"> 開始</span> は、最後の同期以降、指定した分以内にクライアントがサーバーとの同期を開始する必要があることを指定します。 </li> 
      <li id="li_9DEBC57385A442C3929AE3D0E3FA8992">（オプション） <span class="codeph"> 強制</span> は、再生中にクライアントが同期メッセージを強制する必要がある確率 (0 ～ 100) です。 </li> 
     </ul>更新時に、 <span class="codeph"> -sync</span> 同期要件を削除する残りの引数がない場合。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.useRootLicense</span> </td> 
   <td colname="2" class="- topic/entry ">この DRM ポリシーにルートライセンスがあるかどうかを示します。 <p>詳しくは、 <a href="https://help.adobe.com/en_US/primetime/drm/5.3/protecting_content/index.html#DRM-concept-Enhanced_License_Chaining" class="- topic/xref " format="http" scope="external"> 拡張ライセンスチェーニング</a>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.startDate</span> </td> 
   <td colname="2" class="- topic/entry ">コンテンツが有効になる日付。 次のいずれかの形式を適用できます。 
    <ul id="ul_6610B44D0C16485098F6F45DE3F151D7"> 
     <li id="li_986707D4C6164C44B3CCBE2EEB4C09B6"><span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd</span> <p>例： <span class="codeph"> 2009-01-31</span> は、1 月 31 日の午前 0 時を表します。 </p> </li> 
     <li id="li_E15B782716124F6EAEFB04D16E5280DB"><span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd-h24:min:秒</span> <p>例： <span class="codeph"> 2009-01-31-14:30:00</span> は、1 月 31 日の午後 2 時半を表します。 </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.expiration.endDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コンテンツの前の日付が無効になります。 </p> <p>注意： <span class="codeph"> policy.expiration.endDate</span> および <span class="codeph"> policy.expiration.duration</span> 同時に </p> <p>例： 2009-01-31-14:30:00 の場合、コンテンツの有効期限は 1 月 31 日の午後 2 時 30 分になります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.expiration.duration</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コンテンツが無効になるまでの時間（分単位）です。 時間は、コンテンツをパッケージ化する際に始まります。 </p> <p>注意： <span class="codeph"> policy.expiration.endDate</span> および <span class="codeph"> policy.expiration.duration</span> 同時に </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.licenseCaching.duration</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">クライアント上でライセンスをキャッシュできる時間（分）。 このプロパティを 0 に設定すると、ライセンスのキャッシュを防ぐことができます。 0 以上の値を指定する必要があります。 </p> <p>注意： <span class="codeph"> policy.licenseCaching.duration</span> および <span class="codeph"> policy.licenseCaching.endDate</span> 同時に </p> <p class="- topic/p ">この DRM ポリシー設定は、ディスク上のライセンスキャッシュにのみ適用され、メモリキャッシュライセンス期間は制御されません。 期間が 0 の DRM ポリシーを指定しない場合でも、ライセンスをメモリにキャッシュできます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.licenseCaching.endDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスをキャッシュできなくなる日付。 </p> <p>注意： <span class="codeph"> policy.licenseCaching.duration</span> および <span class="codeph"> policy.licenseCaching.endDate</span> 同時に </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.anonymous</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">匿名ライセンスの取得を許可するかどうかを示します。 デフォルトはに設定されています。 <span class="codeph"> false</span>：ユーザー名とパスワードが必要です。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.authNamespace</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ユーザー名とパスワードが必要な場合、このプロパティはユーザー名の名前修飾子（オプション）を指定します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.customProp.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ライセンスの取得時にサーバーで使用されるカスタムの名前と値のペア。 次の形式を適用して、プロパティを指定できます。 <span class="+ topic/ph pr-d/codeph codeph">policy.customProp.n</span>=<span class="+ topic/ph pr-d/codeph codeph">名前</span>=<span class="+ topic/ph pr-d/codeph codeph">値</span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.playbackWindow </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">再生ウィンドウを分単位で指定します。 この値は、保護されたコンテンツが初めて再生された後にライセンスが有効である期間を表します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.outputProtection.digital</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">出力保護制約。次の値のいずれかにする必要があります。 
     <ul id="ul_wsb_kfp_fs"> 
      <li id="li_FE012306F22F4F3FB981FE167C7A8B94"><span class="codeph"> NO_PROTECTION</span> </li> 
      <li id="li_A5591DC8983848FE9823C2A261BF7713"><span class="codeph"> USE_IF_AVAILABLE</span> </li> 
      <li id="li_74102C36ADE841C4B9ED71156E0A4C2C"><span class="codeph"> 必須</span> </li> 
      <li id="li_769E15C85B4E4DD48213DBD019D60BA7"><span class="codeph"> NO_PLAYBACK</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.outputProtection.ota</span> </td> 
   <td colname="2" class="- topic/entry ">許可リストに表示する空気 (OTA) 接続タイプを指定します。 有効な接続タイプは次のとおりです。 
    <ul id="ul_iz5_4fp_fs"> 
     <li id="li_FB07519EFEFE4B95B3B1F5BFD4DE6591"><span class="codeph"> 奇跡</span> </li> 
     <li id="li_51E7DE83679F4630B01264407DAD0E84"><span class="codeph"> 飛行機</span> </li> 
     <li id="li_D499A0487AAC409CB2CEA6164265D3CF"><span class="codeph"> DLNA</span> </li> 
     <li id="li_4FCC0EC4A0FC48F99A13EC8A1B78D6A1"><span class="codeph"> 幅</span> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.outputProtection.resolution</span> </td> 
   <td colname="2" class="- topic/entry "> 解像度に基づく制約を定義する設定ファイルを指定します。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.drmMinSecurityLevel</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">DRM モジュールが保護されたコンテンツにアクセスできる最小のセキュリティレベルを指定します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> policy.runtimeMinSecurityLevel</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツにアクセスするには、アプリケーションランタイムモジュールに少なくとも指定された最小セキュリティレベルが必要です。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.allowedAIRApplication.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">Flash以外のアプリケーションの許可リスト(Adobe AIR、iOS、Android など ) 保護されたコンテンツの再生が許可されている プロパティでは次の形式を使用する必要があります。 <span class="+ topic/ph pr-d/codeph codeph">pubId</span>[:<span class="+ topic/ph pr-d/codeph codeph">appId</span>[:[<span class="+ topic/ph pr-d/codeph codeph">分</span>]:[<span class="+ topic/ph pr-d/codeph codeph">最大</span>]] </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.allowedSWFApplication.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保護されたコンテンツの再生が許可されるSWFアプリケーションの許可リスト。 プロパティでは次の形式を使用する必要があります。 </p> <p class="- topic/p "> 
     <ul id="ul_EC20F52AD95C4BE3B7F703048A43CDF0"> 
      <li id="li_3E4A47D925C24834A2C25BC5943279D4"><span class="+ topic/ph pr-d/codeph codeph">URL</span> </li> 
      <li id="li_9A7CAF081C5F488FB5CDA6D38C5552F6"><span class="+ topic/ph pr-d/codeph codeph">file=swf_file</span> </li> 
      <li id="li_E10EA4223137489CBE4015DE999F7154"><span class="codeph">time=max_time_to_verify</span> </li> 
     </ul> <i class="+ topic/ph hi-d/i ">swf_file</i> は、SWFの計算に使用されるハッシュファイルで、 <i class="+ topic/ph hi-d/i ">max_time_to_verify</i> は、SWFのダウンロードと検証が完了するまでに許可される最大時間（秒）です。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">policy.license.customProp.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ユーザーにライセンスが発行される際にライセンスに含める必要があるカスタムの名前と値のペア。 次の形式を指定する必要があります。 </p> <p class="- topic/p "><span class="+ topic/ph pr-d/codeph codeph">policy.license.customProp.n=name</span> </p> <p class="- topic/p ">このオプションは、複数のカスタムプロパティに対して複数回定義できます。 </p> </td> 
  </tr> 
 </tbody> 
</table>
