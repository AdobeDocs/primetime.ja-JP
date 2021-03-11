---
title: NATIVE_ERROR通知の詳細
description: NATIVE_ERROR通知の詳細
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '6888'
ht-degree: 2%

---


# NATIVE_ERROR通知{#details-for-the-native-error-notification}の詳細

TVSDKは、ネイティブエラーを処理すると、以下のメタデータキーの値の一部またはすべてを文字列として返します。

<table id="table_7F713B7A56024D8DA3C84E449D09CC91"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"><b>メタデータキー名</b></th> 
   <th colname="col2" class="entry"><b>メタデータ値</b></th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> NATIVE_ERROR_CODE</span> </td> 
   <td colname="col2"> <p>AVEのネイティブエラーコードです。 </p> <p>これらのコードは、次を表します。 
     <ul id="ul_1F33D523DDFE4CE8B4F0DC279FF7E4F8"> 
      <li id="li_07A2D9BEE6364935A61EF3BD4AB6DE27">DRMエラー（コード3300 ～ 3367）。 これらは、同等のFlash Playerエラーコードと同じです </li> 
      <li id="li_433BA22DE3504AEEB623598BB4F939FA">ビデオ再生エラー(-1 ～ 89) </li> 
      <li id="li_B347CB151DB94DE0A1DDEB1B33D2DABA">暗号化エラー(300 ～ 307) </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> NATIVE_ERROR</span> </td> 
   <td colname="col2">通知の短い説明（例：<span class="codeph"> AAXS_InvalidVoucher</span>、<span class="codeph"> DECODER_FAILED</span>）。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> 説明</span> </td> 
   <td colname="col2"> 通知の詳細な説明（広告解決操作が失敗したなど）。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> PSDK_ERROR_CODE</span> </td> 
   <td colname="col2"><span class="codeph"> com.adobe.mediacore.</span> PSDKErrorCodenumeric値（例：「13」）。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> PSDK_ERROR</span> </td> 
   <td colname="col2"><span class="codeph"> com.adobe.mediacore.</span> PSDKErrorCodeasを文字列( <span class="codeph"> kECNetworkError</span>など)で返します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> 警告</span> </td> 
   <td colname="col2"> 警告の説明です。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ERROR</span> </td> 
   <td colname="col2"> エラーの説明。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>DRM</b> </td> 
   <td colname="col2"></td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> NATIVE_SUBERROR_CODE</span> </td> 
   <td colname="col2"> DRMモジュールからのマイナーエラー。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> DRM_ERROR_STRING</span> </td> 
   <td colname="col2"> エラーの説明。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> DRM_ERROR_SERVER_URL</span> </td> 
   <td colname="col2"> TVSDKが話し合おうとしたDRMサーバーのURL。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>広告マニフェストの読み込み失敗</b> </td> 
   <td colname="col2"></td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AD_URL</span> </td> 
   <td colname="col2"> 読み込めなかったコンテンツのURL。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AD_TYPE</span> </td> 
   <td colname="col2">広告のタイプ（<span class="codeph"> MediaResource.Type</span> enumの定数）。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AD_DURATION</span> </td> 
   <td colname="col2"> 広告の時間（ミリ秒）。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AD_ID</span> </td> 
   <td colname="col2"> 広告に割り当てられたID。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>ファイルエラー</b> </td> 
   <td colname="col2"></td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> DOWNLOAD_ERROR</span> </td> 
   <td colname="col2"> メディアファイルのダウンロード中のエラーの説明。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> URL</span> </td> 
   <td colname="col2"> ダウンロード中のファイルのURL。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> MANIFEST_ERROR</span> </td> 
   <td colname="col2"> マニフェストファイルのダウンロード中のエラーの説明。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> CONTENT_ERROR</span> </td> 
   <td colname="col2">フラグメント（<span class="codeph"> ts</span>など）のダウンロード中のエラーの説明。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>オーディオトラックのエラー</b> </td> 
   <td colname="col2"></td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AUDIO_TRACK_NAME</span> </td> 
   <td colname="col2"> マニフェストで指定されている、読み込みに失敗したオーディオトラックの名前。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AUDIO_TRACK_LANGUAGE</span> </td> 
   <td colname="col2"> マニフェストで指定されている、オーディオトラックの言語。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>シークエラー</b> </td> 
   <td colname="col2"></td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> DESIRED_SEEK_PERIOD</span> </td> 
   <td colname="col2"> 期間（整数）のID。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> DESIRED_SEEK_POSITION</span> </td> 
   <td colname="col2"> <p>要求された位置（ミリ秒）(重複)。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>その他</b> </td> 
   <td colname="col2"></td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AUDITUDE_ERROR_CODE</span> </td> 
   <td colname="col2"> Auditudeエラーコード（数値）。 </td> 
  </tr> 
 </tbody> 
</table>

## NATIVE_ERROR:DRM値{#section_D240082B93D34902A18C3923C1C717B3}

AdobeビデオエンジンのVideo Encoderインターフェイスは、以下のDRM通知を`NATIVE_ERROR`メタデータオブジェクトに返します。

レポートのDRMエラーをAdobeに送信する場合は、トラブルシューティングの支援を得るために`NATIVE_SUBERROR_CODE`と`DRM_ERROR_STRING`を必ず含めてください。

>[!TIP]
>
>このリストは、TVSDK固有のエラー情報を提供します。 詳しくは、「[ActionScript実行時エラーActionScriptリファレンス」のAdobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/runtimeErrors.html#3300)を参照してください。

<table id="table_CD59A859865F4FFDBAA249C89C74770A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"><b>NATIVE_- ERROR_CODEメタデータキーの値</b></th> 
   <th colname="col2" class="entry"><b>NATIVE_ERROR_NAMEメタデータキーの値</b></th> 
   <th colname="col3" class="entry"><b>意味</b></th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> 3300 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InvalidVoucher</span> </td> 
   <td colname="col3"> 
    <ul id="ul_516E4CB32D624B22892DDB9266CB04CA"> 
     <li id="li_348FC0F38B11417994119B61C9244076">ディストリビュータのソフトウェアが実行すべきこと： 
      <ul id="ul_7AFD45CF92454BA4927783FAA628FBC4"> 
       <li id="li_0D9CCE61612643648C12DCDDD252E52A">Google Chromeを使用していて、匿名モードで、Flash Playerのバージョンが11.6未満の場合は、このエラーが発生する可能性があります。 <p>プレイヤーはブラウザーのバージョン番号を確認し、匿名モードを終了するようにユーザーに勧めることをお勧めします。 </p> </li> 
       <li id="li_1DC6B755BD0840D48BEC92568FD330BA">ライセンスを再度要求します。 <p>リクエストが正常に完了した場合は、ログに記録したりエスカレーションを行ったりする必要はありません。 要求が失敗した場合は、エラーの原因となった内容を記録します。 <span class="codeph"> subErrorIdは、行</span> エラー（存在する場合）を含みます。 </p> </li> 
      </ul> </li> 
     <li id="li_060B5D60C9BB419CBFA7B062FBCF2632">ディストリビュータが行うべきこと： 
      <ul id="ul_FADB29DBF0DA4A0E8E54134AEB7DCD8A"> 
       <li id="li_FC5B1C04D21E4AECB0EBD9ADD3198504">Chrome以外のFlashーでバージョン11.6より前の再試行が発生した場合は、パッケージ化でエラーが発生した可能性があります。 </li> 
       <li id="li_A720ECE591254021879B335B81B1F76D">問題が特定のコンテンツに固有のものであるかどうかを確認し、再パッケージ化します。 </li> 
      </ul> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3301 </td> 
   <td colname="col2"><span class="codeph"> AAXS_AuthenticationFailed</span> </td> 
   <td colname="col3"> <p>サーバーがクライアントを認証または承認できませんでした。 </p> 
    <ul id="ul_BE77AC1848FB4C09B6318359ACF1B8EE"> 
     <li id="li_6FB37D317D174E8488C5070D20CD241C">配布者のソフトウェアは、ユーザーの資格情報を再確立したり、ユーザーにコンテンツへのアクセスを取得させるために必要なアクションを実行する必要があります。 </li> 
     <li id="li_BE071D59805B42D38E3E7650BC936417">ディストリビュータは、ディストリビュータの承認と認証メカニズムが正しく動作していることを確認する必要があります。 <p>配布者が認証機能や認証機能の使用を計画していない場合は、問題のあるコンテンツのポリシーで認証が必要かどうかを確認し、ポリシーとライセンスの不一致の診断を参照してください。 </p> </li> 
    </ul> <p>このエラーコードについて詳しくは、<a href="https://forums.adobe.com/thread/1277149" format="https" scope="external"> DRMエラー3301の原因と解決</a>を参照してください。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3302 </td> 
   <td colname="col2"><span class="codeph"> AAXS_RequireSSL</span> </td> 
   <td colname="col3"> <p>Access 4.0以降では、リモートキーURLがスキームとしてHTTPSを使用していない場合に、iOSでこのエラーがスローされます。 HTTPSが必要です。 </p> 
    <ul id="ul_3D47777BBCA14B67B107FBBE3E37E40C"> 
     <li id="li_7F7BBB27AE754CC39ABAAF9269739C49">ディストリビュータがAccess v4より古いバージョン、または4以上のバージョンを使用しているが、プラットフォームがiOSではない場合、ディストリビュータのソフトウェアはエラーをログに記録する必要があります。 <p>このエラーはiOSでのみスローされます。 </p> </li> 
     <li id="li_D83C427D2A0D47408F723EF7195070B6">ディストリビュータのソフトウェアがAdobeアクセスバージョン4以上で、プラットフォームがiOSの場合、ディストリビュータは、使用するリモートキーサーバのURLをHTTPSに変更する必要があります。 <p>HTTPのみを使用している場合は、ディストリビューターがHTTPSサーバーを設定する必要がある場合があります。 それ以外の場合は、配布者はログに記録された情報をAdobeに送信し、問題をエスカレーションする必要があります。 </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3303 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ContentExpired</span> </td> 
   <td colname="col3"> <p>表示中のコンテンツは、コンテンツプロバイダーによって設定されたルールに従って有効期限が切れています。 subErrorIdには、クライアント固有のエラーまたは行エラーが含まれます。 </p> <p> 
     <ul id="ul_1E4B3B8AE87A4E79997553BB2A0E52B9"> 
      <li id="li_EE3F2EEBF73743B9A38E4FCB7531E275">ディストリビュータのソフトウェアは、新しい期限切れでないライセンスが使用可能かどうかを判断するために、サーバからライセンスを1回再取得しようとします。 <p>使用可能なライセンスがない場合、またはライセンスの有効期限が切れた場合は、新しいライセンスを取得するか、コンテンツを視聴できないことをユーザーに通知します。有効期限が切れたポリシーでコンテンツがパッケージ化された場合は、<span class="codeph"> PolicyEvaluationException</span>が記録されます。 サーバーのログファイルを確認してください。 </p> <p>可能であれば、パッケージ化の際に使用したポリシーを確認して、有効期限が切れているかどうかを確認する必要があります。 Javaコマンドラインツールは次のとおりです。<code> java&nbsp;-jar&nbsp;libs/AdobePolicyManager.jar&nbsp;&nbsp;&nbsp;detail&nbsp;demo.pol</code> </p> </li> 
      <li id="li_50DBE680D8F04E7DA3E29C65A93188E7">ディストリビュータは、ライセンスの有効期限が意図したとおりに設定されているかどうかを確認する必要があります。 </li> 
     </ul> </p> <p>このエラーコードについて詳しくは、「ライブストリームを使用するAMS/FMSでの<a href="https://forums.adobe.com/thread/1300813" format="https" scope="external"> 3303 (Content Expired)」を参照してください。</a> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3304 </td> 
   <td colname="col2"><span class="codeph"> AAXS_AuthorizationFailed</span> </td> 
   <td colname="col3">このエラーコードについて詳しくは、<a href="https://forums.adobe.com/thread/1277149" format="https" scope="external"> DRMエラー3301の原因と解決</a>を参照してください。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3305 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ServerConnectionFailed</span> </td> 
   <td colname="col3"> <p>ネットワークの遅延またはクライアントがオフラインのため、ライセンスサーバーまたはドメインサーバーへの接続がタイムアウトしました。 通常、subErrorIdにはHTTPリターンコードが含まれます。 </p> 
    <ul id="ul_938C7D8F07F64B4FA71A09DDF37E2E64"> 
     <li id="li_6648EA0049094E369BD9AE9CCA6B148D">ディストリビュータのソフトウェアは、既知の正常なサーバへのネットワーク接続を試みる必要があります。 <p>試行が失敗した場合は、ネットワークに再接続するようにユーザーに促します。 試行が成功した場合は、ログに記録します。 </p> </li> 
     <li id="li_2ECA2C04BA08449DA3AD79A52EFAA229">ディストリビュータは、使用中のライセンスサーバーとドメインサーバーがオンラインで、クライアントのネットワークから見えることを確認する必要があります。 </li> 
    </ul> <p>このエラーコードについて詳しくは、<a href="https://forums.adobe.com/thread/1284947" format="https" scope="external"> DRM 3305 [ServerConnectionFailed] causes and resolution</a>を参照してください。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3306 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ClientUpdateRequire</span> </td> 
   <td colname="col3"> 新しいバージョンのAndroid向けTVSDKを使用します。 <p>現在のクライアントは要求された操作を完了できませんが、更新されたクライアントは要求を完了できる可能性があります。 </p> <p>これには、次のような原因が考えられます。 
     <ul id="ul_2EC4D42D5273439FA1AFDA1A2578B3D6"> 
      <li id="li_FCA926F5FAED4E7190BE855545AB6ACF">このクライアントで使用できない共有ドメインが使用されました。 Chromeで再生が動作する場合はこのような状況が発生する可能性がありますが、他のブラウザーでは動作しない場合と、他のブラウザーで再生が動作する場合は同じ状況が発生します。 <p> <p>ヒント：Chromeでは、他のブラウザーとは異なるPHDS/PHLSキーが使用されます。 詳しくは、<a href="https://adobeprimetime.zendesk.com/agent/tickets/2891" format="https" scope="external"> https://adobeprimetime.zendesk.com/agent/tickets/2891</a>を参照してください。 </p> </p> </li> 
      <li id="li_3B633FB699234DCEA136E9BE3CC3386D">5.0より前のバージョンのiOSで実行している場合、アプリケーションが複数のDRMSessionを追加しようとしています。 </li> 
      <li id="li_F7ED993AF0B941A7A27216B4D587A999">バージョン2のみがサポートされている場合、メタデータのバージョンは3以上です。 </li> 
     </ul> </p> 
     <ul id="ul_EE4AE6AD4F1745A5B5623E53B599DB62"> 
      <li id="li_7A83869D4262443DA35FA1DF8D3097DD">ディストリビュータのソフトウェアは、ユーザーに警告を出し、操作を中止する必要があります。 <p>ソフトウェアでアップグレードが利用可能かどうかを判断する方法がある場合は、プラットフォームに適した方法でそのアップグレードにユーザーを誘導します。 </p> </li> 
      <li id="li_AF9C2711FDE54DA196EB9D2864632000">共有ドメインが原因で問題が発生した場合、ディストリビュータは、更新されたランタイムまたはライブラリについてAdobeと確認する必要があります。 <p>Flashランタイムの場合、ディストリビューターは、アプリケーション内で直接アップグレードを強制できます。 ライブラリの場合、ディストリビューターは、更新されたライブラリを取得し、アプリケーションを再構築してユーザーに展開する必要があります。 </p> <p>複数のDRMSessionが原因で問題が発生した場合、ディストリビューターは、複数のDRMSessionを追加する前に、iOSのバージョン番号を確認するようにアプリケーションを更新する必要があります。 また、iOS v5以降にアプリケーションの配布を制限することもできます。 </p> <p>メタデータのバージョンがバージョン2よりも高いことが原因で問題が発生した場合は、メタデータが破損している可能性があります。 メタデータを再構築し、結果を調べることができます。 引き続き問題が表示される場合は、問題をログに記録し、Adobeにエスカレーションします。 </p> </li> 
     </ul> <p>このエラーコードの詳細については、<a href="https://forums.adobe.com/thread/1266675" format="https" scope="external"> 「3306 DRMErrorEventエラーコードを修正する方法</a>」を参照してください。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3307 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InternalFailure</span> </td> 
   <td colname="col3"> <p>これは通常、Adobeアクセスコードのバグを表し、以下のような既知のバグがない限り予期しないものです。 subErrorIdには、クライアント固有のエラーまたは行エラーが含まれます。 </p> 
    <ul id="ul_79F4A9655A2148519B1E9509C41F78C3"> 
     <li id="li_0E093AB4D6BD489B852279E6C1525A15">ブラウザーがWindows版Chromeで、Flashーのバージョンが11.6（SWFバージョン19以降）の場合、配布者のソフトウェアでは、ユーザーが情報バー上で<span class="uicontrol">拒否</span>を押したと想定し、3368と同じ扱いを行う必要があります。 </li> 
     <li id="li_0215D1089B344861A2C0A73E1067CFEF">ブラウザーがChromeでない場合やFlashーのバージョンが11.6でない場合、3307が発生した場合は、ディストリビューターはAdobeにエスカレーションする必要があります。 </li> 
    </ul> <p>重要：<span class="codeph"> 3307:1107296344 (FailedToGetBrokerHandle)</span>は、Chromeブラウザーのバージョン24 ～ 28で発生する可能性があります。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3308 </td> 
   <td colname="col2"><span class="codeph"> AAXS_WrongLicenseKey</span> </td> 
   <td colname="col3"> <p>このエラーは、使用中のライセンスに、コンテンツの復号化に使用する誤ったキーが含まれている場合にスローされます。 subErrorIdには、クライアント固有のエラーまたは行エラーが含まれます。 </p> <p>このバグを生成する方法は2つしかないようです。 
    <ul id="ul_1C955BD74C7843809D1B5A0CDCA5ED7B"> 
     <li id="li_18F0A7FDA6584887AD9DB3EDE54080D8">お客様は、ライセンス生成用の標準Adobeツール（例えば、ライセンサーサーバーのJavaフレームワーク）を変更しました。 <p>この場合、ライセンスに不正なキーが含まれているので、どのコンテンツにも対応していない可能性があります。 </p> </li> 
     <li id="li_21D04ED1F1FA464785BC297D385766FF">お客様が、同じライセンスIDを持つ複数のライセンスを発行しました。 <p>この場合、クライアント上で使用可能な複数のライセンスがコンテンツのメタデータと一致し、Accessコードで誤ったライセンスが使用用に選択されています。 </p> </li> 
    </ul> </p> 
    <ul id="ul_64AEE62BE36946F290067CF475A36ECA"> 
     <li id="li_9EEB2B11A4DA41E78C5840D8FAA81F0D">ディストリビュータのソフトウェアは、サーバからライセンスを再取得しようとします。 
      <ul id="ul_ACADC5518B054D0A853AEED2B675DB23"> 
       <li id="li_394835C8731048A5BF7D9370AC12448C">使用可能なライセンスがない場合やライセンスの有効期限が切れている場合は、ユーザーが新しいライセンスを取得できるようにワークフローを提供するか、コンテンツを視聴できないことをユーザーに通知して問題をログに記録します。 </li> 
       <li id="li_3FE50518BE53405F9563FA620F7EAD5F">これが（AIRの）ドメインバウンドコンテンツの場合は、ユーザーがドメインに参加する手段を提供します。 </li> 
      </ul> </li> 
     <li id="li_C80B353C1AEA4E9398241420CB491E84">ディストリビュータは、次の条件を満たす必要があります。 
      <ul id="ul_B5C50009374C4EED9B2B050B48F5F0F6"> 
       <li id="li_D5E6B760E0BC4B5C949ED1544B398838">Access License Serverのライセンス発行部分がカスタマイズされていないことを確認します。 </li> 
       <li id="li_AA8F4E4B6DDD40BA8807C0920A92186B">すべてのライセンスに対して一意のライセンスIDが発行されていることを確認します。 </li> 
       <li id="li_A2C53FE779AC4FDDB65E00A2C4F43EC4">Adobeを含む問題の承認申請を行います。 </li> 
      </ul> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3309 </td> 
   <td colname="col2"><span class="codeph"> AAXS_CorruptedAdditionalHeader  </span> </td> 
   <td colname="col3"> <p>これは、ヘッダーが65536バイトを超える場合に発生します。 </p> 
    <ul id="ul_82C0F688519B4F43A764D59A891F1903"> 
     <li id="li_E66AC9149A0649E88A79C5289C12C395">ディストリビューターのソフトウェアは、エラーの原因となったコンテンツの部分をログに記録する必要があります。 </li> 
     <li id="li_1C5916A33E7B4DC9968105B9BD20A727">配布者は、エラーが特定のコンテンツで再現できることを確認する必要があります。 壊れたコンテンツを再パッケージ化します。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3310 </td> 
   <td colname="col2"><span class="codeph"> AAXS_AppIDMismatch  </span> </td> 
   <td colname="col3">Androidアプリケーションが、使用中のAndroidアプリケーションと一致しません。 <p>正しいAIRアプリケーションまたはFlashSWFが使用されていません。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3311 </td> 
   <td colname="col2"><span class="codeph"> AAXS_AppVersionMismatch  </span> </td> 
   <td colname="col3"> 使用中ではありません。 この問題は、AIRのバージョン1.xスタックでも引き続き発生する可能性があります。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3312 </td> 
   <td colname="col2"><span class="codeph"> AAXS_LicenseIntegrity  </span> </td> 
   <td colname="col3"> この問題を修正するには、サーバーからライセンスを再度ダウンロードします。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3313 </td> 
   <td colname="col2"><span class="codeph"> AAXS_WriteMicrosafeFailed  </span> </td> 
   <td colname="col3"> <p>この問題は、システムがファイルシステムに書き込めない場合に発生します。 <span class="codeph"> subErrorIdには、クライアント固有のエラーまたは行エラーが含まれます。</span>  </p> <p>Microsoft Windowsでは、暗号化されたコンテンツにlicenseIDまたはpolicyIDが長すぎる場合、Active XまたはNPAPIプラグフラッシュプレーヤーによってエラー3313が発生する可能性があります。 これは、Windowsでのパスの長さの最大値が原因です。 （Pepperプラグインにはこの問題はありません）。 </p> <p>「ワトソン3549660」を参照してください。 </p> 
    <ul id="ul_DFD527D1E1224A439766DF7BED878E3B"> 
     <li id="li_FAF8FD98A4E8478CA7A92F770676ADFC">ディストリビュータのソフトウェアは、ユーザー・ディレクトリがロックされていないか、またはフル・ボリュームまたはロックされているボリューム上にないかを確認するように要求する必要があります。 </li> 
     <li id="li_6D1136EA750A459BBECEEE5F73F527BB">ディストリビュータがFlashではなくAIRを使用している場合は、パスの長さの制限が原因の可能性があります。 <p>配布者は、AIRアプリケーションの名前を妥当な名前に短縮する必要があります。 また、<span class="codeph"> licenseID</span>と<span class="codeph"> policyID</span>を短くして、コンテンツを再公開します。 </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3314 </td> 
   <td colname="col2"><span class="codeph"> AAXS_CorruptedDRMMetadata  </span> </td> 
   <td colname="col3"> <p>このエラーは、多くの場合、コンテンツがテストPKI証明書でパッケージ化され、プレイヤーが実稼働用PKIで構築されているか、その逆であることを示します。 subErrorIdには、クライアント固有のエラーまたは行エラーが含まれます。 </p> 
    <ul id="ul_A122EF304CAF48A8B4DA1E3F4413E29B"> 
     <li id="li_A9A1A5B23E884C22A71E2DE7535FEB3B">ディストリビューターのソフトウェアは、エラーの原因となったコンテンツの部分をログに記録する必要があります。 </li> 
     <li id="li_7AD7F13A4B1B4998A7E49664E7645815">配布者は、エラーが特定のコンテンツで再現できることを確認する必要があります。 <p>破損したコンテンツを再パッケージ化する必要がある場合があります。 </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3315 </td> 
   <td colname="col2"><span class="codeph"> AAXS_PermissionDenied  </span> </td> 
   <td colname="col3"> <p>3305を意図した場合にこのエラーコードがスローされる既知のバグがあります。 詳しくは、<a href="https://forums.adobe.com/thread/1284947" format="https" scope="external"> DRM 3305 [ServerConnectionFailed] causes and resolution</a>を参照してください。 </p> <p>AIRによって読み込まれたリモートSWFは、Flash Access機能にアクセスできません。 このエラーコードは、ネットワークアクセス中にセキュリティエラーが発生した場合にもスローされます。 例えば、crossdomain.xmlを使用して接続するクライアントが宛先サーバーにない、またはcrossdomain.xmlに到達できないなどです。 </p> <p>詳しくは、<a href="https://forums.adobe.com/thread/1266592" format="https" scope="external"> DRMエラー3315考えられる根本原因と解決</a>を参照してください。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3316 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NOTUSED_MOVED  </span> </td> 
   <td colname="col3"> 以前は<span class="codeph"> ADOBECPSHIM_MinorErr_MissingAdobeCPModule</span>でした。 Flashエラーコードと競合するため、3344に移動されました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3317 </td> 
   <td colname="col2"><span class="codeph"> AAXS_LoadAdobeCPFailed  </span> </td> 
   <td colname="col3"> <p>重要： これはまれなエラーで、通常は実稼働環境では発生しません。 </p> <p>エラーが発生した場合は、次のいずれかを実行できます。 
     <ul id="ul_BC435E61623444BB98A86216531DC892"> 
      <li id="li_FA433D0758B642D2AFDCF04906B3FE18">AIRを使用している場合は、再インストールします。 </li> 
      <li id="li_F08D9AAFF46244F8842DEE5FD9CBBE0A">Flash Playerを使用している場合は、<span class="codeph"> AdobeCP</span>モジュールを再度ダウンロードします。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3318 </td> 
   <td colname="col2"><span class="codeph"> AAXS_IncompatibleAdobeCPVersion  </span> </td> 
   <td colname="col3"> Androidは該当しません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3319 </td> 
   <td colname="col2"><span class="codeph"> AAXS_MissingAdobeCPGetAPI  </span> </td> 
   <td colname="col3"> Androidは該当しません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3320 </td> 
   <td colname="col2"><span class="codeph"> AAXS_HostAuthenticateFailed  </span> </td> 
   <td colname="col3"> Androidは該当しません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3321 </td> 
   <td colname="col2"><span class="codeph"> AAXS_I15nFailed  </span> </td> 
   <td colname="col3"> <p>キーを使用したクライアントのプロビジョニング処理に失敗しました。 subErrorIdには、クライアント固有、サーバー固有、または行エラーが含まれます。 </p> 
    <ul id="ul_98D919B9060A441AACB6106F6D8E8DA7"> 
     <li id="li_DCAB00A8AC4A426CBBD377374B3F71AE">ディストリビュータのソフトウェアは、少なくとも1回は操作を再試行する必要があります。 <p>WindowsでGoogle Chromeを使用している場合は、サンドボックス内にないプラグインへのアクセスを許可する方法について説明します。 詳しくは、「<a href="https://helpx.adobe.com/adobe-access/kb/error-3321.html" format="html" scope="external"> Google Chromeのunsandboxへのアクセスが拒否されました</a>」を参照してください。 </p> </li> 
     <li id="li_7FB7681FE32D444BB1BDBA3E5953A2C3">ディストリビュータは、次のいずれかのタスクを完了する必要があります。 
      <ul id="ul_486B64F187C44AE3B4775953A6142836"> 
       <li id="li_095B1D4CD051427CB2BFA7082B454056">エラーが複数のプラットフォームで一貫している場合は、Adobeと共に問題をエスカレーションする必要があります。 </li> 
       <li id="li_0C6EB7B912FA41E59657216498DA3515">Windows上のChromeにエラーが限定されている場合は、セキュリティで保護されていないプラグインへのアクセスを許可するようユーザーに指示します。 </li> 
      </ul> <p>配布者はSWFをバージョン19以降に更新する必要があります。Chrome固有の3321エラーが発生すると、3368エラーが発生します。 エラー3368は、ディストリビュータのソフトウェアによってより具体的に処理される可能性があります。 この変更は、Chrome Stableチャネルバージョン26.0.1410.43で導入されました。 </p> <p>ヒント：エラー<span class="codeph"> 3321:1090519056</span>は、Flash Playerバージョン11.1 ～ 11.6で発生する可能性があります。最新のFlash Playerバージョンにアップグレードすることをお勧めします。 </p> </li> 
    </ul> <p>詳しくは、<a href="https://forums.adobe.com/thread/1277138" format="https" scope="external"> DRMエラー3321原因と解決</a>を参照してください。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>グローバルストアの破損エラー</b> </td> 
   <td colname="col2"> </td> 
   <td colname="col3"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3322 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DeviceBindingFailed  </span> </td> 
   <td colname="col3"> <p>デバイスが、初期化時に存在した構成と一致していないようです。 subErrorIdには、クライアント固有または行エラーが含まれます。 </p> <p>ディストリビュータのソフトウェアは、次のタスクのいずれかを完了する必要があります。 
     <ul id="ul_444401051A2E407B95BC44491E9BB71C"> 
      <li id="li_93493EA05DB44CB1AEC368663F1ABA8D"> <p>デバイスがFlash Playerを使用せず、AIR、iOSなどを使用している場合は、<span class="codeph"> DRMManager.resetDRMVouchers()</span>を呼び出します。 </p> <p>この問題が開発段階のiOSで発生する場合は、開発者に、サードパーティ製のプレリリース配布システム（HockeyAppなど）からダウンロードしたビルドとXcodeからローカルビルドを切り替えた場合に、この問題が発生するかどうかを確認してください。 HockeyAppから配布されたビルドとXcodeからのビルドを切り替えた場合、以前のインストールの属性が完全に上書きされるわけではありません。 この状況では、3322エラーがトリガーする可能性があります。 </p> <p>この問題を解決するには、開発者は新しいビルドをインストールする前に、デバイスから古いビルドを削除する必要があります。 </p> </li> 
      <li id="li_A5C9633F11584C788A2D9A23CC18FA6D">Flash Playerを使用していて、3322または3346のエラーコードで使用できない場合は、Adobeの説明を参照して、<a href="https://forums.adobe.com/message/5535907#5535907" format="https" scope="external"> DRM Error 3322/3346/3368 on Chrome (Info-Bar Problems)</a>. </li> 
     </ul> </p> <p>このエラーは頻繁に発生するとは想定されていません。 ローミングプロファイルを使用する企業環境では、ユーザがDRMで保護されたコンテンツを表示している場合、ユーザが別のマシンからログインするとエラー3322が発生する可能性が高くなります。 可能な場合、ディストリビュータは、この情報をユーザから取得しようとします。 </p> <p>エラーが頻繁に発生する場合は、Adobeにエスカレーションします。 ライセンスストアをリセットした場合に問題が解決したかどうかをAdobeに通知し、エラーが発生しているブラウザをAdobeに通知する必要があります。 </p> <p>詳しくは、次の記事を参照してください。 
     <ul id="ul_C468409D1EA046178CA7F54DCDCB84EA"> 
      <li id="li_20C8CA3853574CE486F21E7A3667DAB9"><a href="https://forums.adobe.com/message/5520902" format="https" scope="external"> https://forums.adobe.com/message/5520902</a> </li> 
      <li id="li_6E6F1BD6FE7843449B3E2F06F342EFF7"><a href="https://forums.adobe.com/message/5535911" format="https" scope="external"> https://forums.adobe.com/message/5535911</a> </li> 
      <li id="li_2BE40E513A0C4BAD900C7B69FEF5D690"><a href="https://forums.adobe.com/message/5748618" format="https" scope="external"> https://forums.adobe.com/message/5748618</a> </li> 
      <li id="li_9C2BD122E3874E2893DD43E082A877E0"><a href="https://forums.adobe.com/message/6061165" format="https" scope="external"> https://forums.adobe.com/message/6061165</a> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3323 </td> 
   <td colname="col2"><span class="codeph"> AAXS_CorruptGlobalStateStore  </span> </td> 
   <td colname="col3"> <p>DRMクライアントが使用するファイルが予期せず変更されました。 subErrorIdには、クライアント固有または行エラーが含まれます。 </p> 
    <ul id="ul_96EA771046CA4B2B9FAE24D493F43FF2"> 
     <li id="li_D2693CD8EFEF46108828BA17E3F54FF6">ディストリビュータのソフトウェアは、3322と同じ方法でユーザをリセットするように指示する必要があります。 </li> 
     <li id="li_0149B82436B64E28AC2B8C9B0EB09898">GlobalStoreが、ユーザーベースのハードドライブの予想される故障率を超える速度で失敗する場合は、問題をAdobeにエスカレートします。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3324 </td> 
   <td colname="col2"><span class="codeph"> AAXS_MachineTokenInvalid  </span> </td> 
   <td colname="col3"> このアプリケーションのDRMローカルストレージをリセットします。 DRMManager.resetDRMを呼び出します。 <p>ライセンスサーバーが証明書失効リスト(CRL)サーバーに接続してCRLファイルを更新できない場合や、クライアントコンピューターがライセンスサーバーによって失効されたライセンス/認証を要求している場合があります。 </p> <p>サーバーログでは、エラーコード111がMachineTokenInvalidです。 ただし、クライアントレベルでは、エラーコード111はエラーコード3324に変換される。 </p> <p>DRMライセンスサーバーの管理者は、お客様のライセンスサーバーがAdobeCRLファイルを取得できたかどうかを確認する必要があります。 お客様がTomcatを使用している場合は、<span class="filepath"> tomcat/temp/</span>ディレクトリを調べて、4つのCRLファイルがあるかどうかを確認できます。 </p> 
    <ul id="ul_23B7F1A104AF49E79EA87DB8E15E337E"> 
      <li id="li_855D87F251184FE688A8D5FA0F6C9EF5">ファイルがこのディレクトリにある場合は、WindowsエクスプローラーおよびCRLビューアアプリケーションで重複キーを押しながらファイルをクリックし、いずれかのファイルの有効期限が切れているかどうかを確認します。 </li> 
      <li id="li_58EC4EDA2B5146188A0FF7B33C91E2FD">tomcat/temp/にファイルがない場合、このライセンスサーバーは、ファイアウォール/ルーティングの問題により、AdobeCRLサーバーに到達できなかったと考えられます。 詳しくは、「<a href="https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_secure_deployment_guidelines.pdf" format="http" scope="external">ファイアウォール規則」を参照してください。</a></li>
    </ul> </p> <p>CRLファイルが使用できない場合、または有効期限が切れている場合は、ライセンスサーバーに接続できるかどうかを確認する必要があります。 お客様のライセンスサーバーでネットワークスニファーを開き、サーバーを再起動し、クライアントにサーバーからのライセンスの要求を試みさせます。 ネットワークトラフィックを観察して、次のURLエンドポイントへの呼び出しが成功したかどうかを確認できます。 <p>ヒント： また、次のCRL URLをブラウザーに入力して、各ファイルを手動でダウンロードできるかどうかを確認することもできます。 </p> 
    <ul id="ul_9B65C7ABBDEC4AC9BF3755FFD3587971"> 
      <li id="li_6867A9050E8D421C9138AC853D1784C9"><a href="https://crl2.adobe.com/Adobe/FlashAccessIndividualizationCA.crl" format="http" scope="external"> crl2.adobe.com/Adobe/FlashAccessIndividualizationCA.crl</a> </li> 
      <li id="li_6431689260554EAFAFDA2EC31798DCB5"><a href="https://crl2.adobe.com/Adobe/FlashAccessIntermediateCA.crl" format="http" scope="external"> crl2.adobe.com/Adobe/FlashAccessIntermediateCA.crl</a> </li> 
      <li id="li_2939674D0F854ADEB67E45FD216288A2"><a href="https://crl2.adobe.com/Adobe/FlashAccessRootCA.crl" format="http" scope="external"> crl2.adobe.com/Adobe/FlashAccessRootCA.crl</a> </li> 
      <li id="li_96386E00BE9D4CB99D100057A5F7C6DD">crl3.adobe.com/AdobeSystemsIncorporated FlashAccessRuntime/LatestCRL.crl</li> 
    </ul> </p> <p>ファイアウォール規則が開いていて、現在の3324エラーがない場合は、一時的なネットワークの問題が発生した可能性があります。 お客様のサーバーログ（おそらく<span class="codeph"> /tomcat/logs/</span>ディレクトリにある）を調べ、ライセンスサーバーが証明書失効リストを取得しようとしたときにエラーが発生したかどうかを確認します。 <p>重要： CRLファイルを更新する際に、大量のクライアント数（またはバースト）がネットワークの一時的な問題として3324エラーを報告した場合に、エラーが発生する場合があります。 ネットワークの問題が解決すると、3324問題も解決しました。 </p> </p> <p>CRLファイルの4つすべてが<span class="filepath"> tomcat/temp/</span>ディレクトリに存在し、クライアントで3324エラーコードが引き続き取得される場合は、CRLファイルへのファイルアクセスに問題がある可能性があります。 この問題を解決するには、ログを確認し、既存のCRLファイルを削除します。 </p> <p>サーバーの問題がない場合は、3322の説明に従って、ユーザーにリセットを促します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>サーバーストアの破損エラー</b> </td> 
   <td colname="col2"> </td> 
   <td colname="col3"> </td> 
</tr> 
  <tr> 
   <td colname="col1"> 3325 </td> 
   <td colname="col2"><span class="codeph"> AAXS_CorruptServerStateStore  </span> </td> 
   <td colname="col3"> <p>DRMクライアントが使用するファイルが予期せず変更されました。 <span class="codeph"> subErrorIdには、クライアント固有のエラーまたは行エラーが含まれます。</span>  </p> 
    <ul id="ul_860D2402DA61460AB0D938F1116F6D64"> 
     <li id="li_CF368C43452B4265B62ADA3E223894BA">ディストリビューターのソフトウェアは、AdobeCPが問題のあるサーバーストアを内部的に削除したので、操作を再試行する必要があります。その場合、再試行は成功します。 再試行が失敗した場合は、問題をログに記録します。 </li> 
     <li id="li_51A5803A1F754970BB4EBD6494F5DC96">再試行が、ユーザーベースのハードドライブの予想される障害率を超える速度で障害が発生した場合は、Adobeに問題をエスカレートします。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3326 </td> 
   <td colname="col2"><span class="codeph"> AAXS_StoreTamperingDetected  </span> </td> 
   <td colname="col3"> <span class="codeph"> DRMManager.resetDRM</span>を呼び出します。 <p>ライセンスストアは改ざんされているか破損しているため、使用できなくなりました。 </p> <p>ディストリビュータのソフトウェアは、3322で説明されているのと同じ方法でユーザをリセットするように指示する必要があります。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3327 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ClockTamperingDetected  </span> </td> 
   <td colname="col3"> クロックを修正するか、または<span class="codeph"> Authn/Lic/Domain</span>ライセンスを再取得します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>認証/ライセンス/ドメインサーバーのエラー</b> </td> 
   <td colname="col2"> </td> 
   <td colname="col3"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3328 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ServerErrorTryAgain  </span> </td> 
   <td colname="col3"> <p>これは、サーバーがクライアントからの要求を完了できなかった、サーバー側のエラーです。 このエラーは、例えば、サーバーがビジー状態、HTTP/500、サーバーが要求の復号化に必要なキーを持っていない場合などに発生します。 </p> <p>クライアント側では、何が問題を起こしたかを判断する方法はありません。 お客様は、Adobeアクセスサーバーログ（通常は<span class="codeph"> AdobeFlashAccess.log</span>と呼ばれます）を確認して、何が問題が発生したかを判断する必要があります。 問題を示す説明的なスタックトレースがログに常に記録されます。 <span class="codeph"> subErrorIdには、サーバー固有のエラーまたは行エラーが含まれます。</span>  </p> <p>ディストリビュータは、サーバーログを調べて、このエラーを送信しているサーバーを特定する必要があります。 サブエラーコード101がある3328個のエラーの場合、サーバーは要求を復号化できません。 お客様は、ライセンスサーバーにインストールされているライセンス/トランスポートサーバー証明書が、パッケージ化の際に使用される証明書と一致していることを検証する必要があります。 </p> <p>また、リファレンスの実装を使用している場合は、プライマリ証明書と追加の証明書が指定されている<span class="codeph"> flashaccess-refimpl.properties</span>ファイルに入力ミスがないことを確認する必要があります。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3329 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ApplicationSpecificError  </span> </td> 
   <td colname="col3"> <p>アプリケーション固有のサブエラーコードがFlash Accessに認識されません。 <span class="codeph"> subErrorIdは、パブリッシャーがカスタマイズしたライセンスサーバーのサーバー固有のエラーを格納します。</span> サーバーが、アプリケーション固有の名前空間でエラーを返しました。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3330 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NeedAuthentication  </span> </td> 
   <td colname="col3"> <p>このエラーは、ライセンスを取得する前にクライアントに認証を求めるようにコンテンツが設定されている場合に発生します。 </p> 
    <ul id="ul_712D29B8B5A6401FB014C4A283918E32"> 
     <li id="li_2D56905EB50D4FDEAD69CA8EAE38AD1A">ディストリビュータのソフトウェアがユーザを認証し、ライセンスを再取得する必要があります。 <p>サービスで認証を使用しない場合は、このエラーの原因となっているコンテンツの識別情報を記録します。 </p> </li> 
     <li id="li_B3BCF899B8BE41C7A4F7CF84B0503483">コンテンツが認証を必要とするように設定されていない場合を除き、このエラーでエスカレーションが必要ではありません。 <p>この場合、問題のあるコンテンツを適切なポリシーで再パッケージ化します。 コンテンツが正しくパッケージ化されている場合は、ポリシーの診断とライセンスの不一致を参照してください。 </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>上記に記載されていないライセンスの適用のエラー</b> </td> 
   <td colname="col2"> </td> 
   <td colname="col3"> </td> 
</tr> 
  <tr> 
   <td colname="col1"> 3331 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ContentNotYetValid  </span> </td> 
   <td colname="col3"> <p>取得したライセンスはまだ有効ではありません。 この問題を解決するには、クライアントの時計が正しく設定されていないかどうかを確認します。 クライアント時計を設定するには、コンテンツを再パッケージ化するか、ライセンスサーバーの設定を変更します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3332 </td> 
   <td colname="col2"><span class="codeph"> AAXS_CachedLicenseExpired  </span> </td> 
   <td colname="col3"> サーバーからライセンスを再取得します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3333 </td> 
   <td colname="col2"><span class="codeph"> AAXS_PlaybackWindowExpired  </span> </td> 
   <td colname="col3"> <p>ポリシーの期限が切れるまで、ユーザーにこのコンテンツを再生できないことを通知する必要があります。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3334 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InvalidDRMPlatform  </span> </td> 
   <td colname="col3"> <p>例えば、コンテンツプロバイダーがAdobeへのアクセスを拒否するようにAdobeアクセスを設定したか、別のパーティション用の共有ドメイントークンに共有ドメインバインドライセンスがバインドされているなど、このプラットフォームではコンテンツの再生は許可されません。 </p> <p>適切な（CDM機能ゲーテッド）パッケージャーの認証を使用してコンテンツがパッケージ化されない場合、CDMはこのエラーをスローします。 </p> <p>コンテンツが正しくないPHDS/PHLS証明書でパッケージ化されている場合、Chromeでは動作するが他のブラウザーでは動作しない可能性があります（逆の場合も同じ）。 <p>ヒント： これは、Chromeで使用されるPHDS/PHLS証明書が異なるためです。 </p>使用されている証明書を確認するには、コンテンツメタデータの詳細をダンプし、<i>受信者証明書</i>を探します。 詳しくは、<a href="https://adobeprimetime.zendesk.com/agent/tickets/2891" format="https" scope="external"> https://adobeprimetime.zendesk.com/agent/tickets/2891</a>を参照してください。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3335 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InvalidDRMVersion  </span> </td> 
   <td colname="col3"> Android向けTVSDKの最新バージョンにアップグレードします。 <p>この問題を解決するには、次のいずれかのタスクを実行します。 
     <ul id="ul_BF1742948BC9461CB8686DE70124D3CD"> 
      <li id="li_690D440C94CC45A0AE55EC319B1C4C23">AIRのアップグレード </li> 
      <li id="li_CDD20251C881466E88BE7BBB53D61EBC">Flash Playerのために、AdobeCPモジュールをアップグレードし、再生を再試行してください。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3336 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InvalidRuntimePlatform  </span> </td> 
   <td colname="col3"> <p>例えば、コンテンツプロバイダーがプラットフォーム上のFP/AIRに対するコンテンツを拒否するようにAccessを設定しているので、このプラットフォームではコンテンツの再生は許可されません。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3337 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InvalidRuntimeVersion  </span> </td> 
   <td colname="col3"> Android向けTVSDKの最新バージョンにアップグレードします。 <p>これは、コンテンツまたはサーバーが、FlashまたはAIRランタイムの特定のバージョンに対する再生を拒否するように設定されている場合に発生します。 </p> 
    <ul id="ul_B0732D941256483CABBDD30C9BF43249"> 
     <li id="li_72782B1D638F48C0B87084689FB9C798">ユーザーが、Flashをアップグレードできるオペレーティングシステム上にある場合、ディストリビュータのソフトウェアは、Flashをアップグレードするようにユーザーに促し、もう一度やり直す必要があります。 それ以外の場合は、別のマシンを使用するようにユーザーに通知します。 </li> 
     <li id="li_1E3FD93CE39E43F2B7D961299B1211DA">エラー3337が疑われる場合は、特定のコンテンツで発生しているかどうかを識別し、そのコンテンツを再パッケージ化します。 コンテンツが正しくパッケージ化されている場合は、ポリシーの診断とライセンスの不一致を参照してください。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3338 </td> 
   <td colname="col2"><span class="codeph"> AAXS_UnknownConnectionType  </span> </td> 
   <td colname="col3"> <p>接続の種類を検出できません。このポリシーでは、[出力の保護]をオンにする必要があります。 この問題は、デジタルまたはアナログの出力保護が必要なコンテンツがパッケージ化されている場合にのみ発生します。 </p> <p>バージョン11.8.800.168より前のFlash Playerのバージョンの問題により、ポリシーでコンテンツ保護が<span class="codeph"> USE IF AVAILABLE</span>であると示されたコンテンツで、エラー3338がときどき発生していました。 この問題は、バージョン11.8.800.168以降で修正されています。 </p> 
    <ul id="ul_4B6CA26A53F84838B5B95400925464D4"> 
     <li id="li_CBD890F467E449EBB5116E1561252058">ディストリビューターのソフトウェアは、出力保護を必要としないコンテンツのバリエーション（例えば、HDストリームのSDバリエーション）を選択します。 <p><span class="codeph"> USE_IF_AVAILABLE </span>コンテンツでエラー3338が発生している場合は、プレイヤーのバージョン番号を確認してください。 プレイヤーのバージョンが11.8.800.168未満の場合は、Flash Playerのアップグレードをユーザーに通知します。 11.8.800.168を超えるバージョンでエラー3338が発生している場合は、どのコンテンツがエラーの原因となったかをログに記録します。 </p> </li> 
     <li id="li_62886C1D96264B129928A7E29E6C70E1">配布者は、このエラーの原因となっているコンテンツを確認し、コンテンツのポリシーが<span class="codeph"> NO_PROTECTION</span>または<span class="codeph"> USE_IF_AVAILABLE</span>をアナログおよびデジタル出力用に設定していることを検証する必要があります。 <p>コンテンツが誤って<span class="codeph"> NO_OUTPUT</span>または<span class="codeph"> REQUIRED</span>でパッケージ化された場合は、コンテンツを再パッケージ化します。 コンテンツが正しくパッケージ化されている場合は、ポリシーの診断とライセンスの不一致を参照してください。 それ以外の場合は、Adobeにエスカレーションします。 </p> </li> 
    </ul> <p>詳しくは、<a href="https://forums.adobe.com/message/5518688" format="https" scope="external"> DRMポリシーがUSE_IF_AVAILABLE?</a>に設定されている場合に、予期しない3338エラーが発生するを参照してください。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3339 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoAnalogPlaybackAllowed  </span> </td> 
   <td colname="col3"> アナログデバイスで再生できません。 この問題を解決するには、デジタルデバイスに接続します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3340 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoAnalogProtectionAvail  </span> </td> 
   <td colname="col3"> 接続されているアナログ外部ディスプレイ機器（モニター/TV）に正しい機能がないため、コンテンツを再生できません（例えば、デバイスにMacrovisionやACPがないなど）。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3341 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoDigitalPlaybackAllowed  </span> </td> 
   <td colname="col3"> デジタルデバイスでコンテンツを再生できません。 <p>重要： この問題は、実稼働環境では発生しません。コンテンツ発行者は、デジタル再生を許可しないでください。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3342 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoDigitalProtectionAvail  </span> </td> 
   <td colname="col3"> 接続されているデジタル外部ディスプレイデバイス（モニター/TV）に正しい機能がありません。 例えば、デバイスにHDCPがないとします。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3343 </td> 
   <td colname="col2"><span class="codeph"> AAXS_IntegrityVerificationFailed  </span> </td> 
   <td colname="col3"> <p>Androidは該当しません。 </p> <p>このエラーは、現在、新しいバージョンのFlashがリリースされた後に最初に発生することがわかっています。 これは、Flashが開いている間にFlashがアップグレードされ、ブラウザーが再起動されるまでFlashが正しくない状態になることが原因で発生します。 </p> 
    <ul id="ul_A0AC4A77550E40409A04BD33748EA987"> 
     <li id="li_F41C1ABD838D41ABB0DF65093E664A29">ディストリビュータのソフトウェアは、次のタスクを完了する必要があります。 
      <ul id="ul_79B2AB1372074D448F129851AA24F985"> 
       <li id="li_B93EDD263D78434FAF198A01938D3508">ユーザーがすべてのブラウザーを閉じるか終了し、再度開くことをお勧めします。 </li> 
       <li id="li_ADFBCFA66AD849E18DB390455458528E">Flashのバージョンが最新であるかどうかを確認します。 <p>バージョンが最新でない場合は、アップグレードをお客様に通知し、ブラウザーのすべてのタブを閉じてから再度開きます。 </p> </li> 
      </ul> </li> 
     <li id="li_281B54582B5949AEA7D166246917EE41">ブラウザーの再起動が成功した後にエラーが発生する場合は、Adobeにエスカレートします。 <p>新しいバージョンがリリースされた場合は、Adobeサポートに問い合わせて、バックグラウンド更新の問題が修正されたかどうかを確認することをお勧めします。 </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3344 </td> 
   <td colname="col2"><span class="codeph"> AAXS_MissingAdobeCPModule  </span> </td> 
   <td colname="col3"> Androidは該当しません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3345 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DRMNoAccessError  </span> </td> 
   <td colname="col3"> <p>Androidは該当しません。 </p> <p>このエラーは、Flashの一部またはAIRが正しくインストールされていない場合に発生します。 </p> <p>ディストリビュータのソフトウェアは、次のいずれかを行う必要があります。 
     <ul id="ul_D1188E2D4FDF4BD89A04F5629D75D981"> 
      <li id="li_B33FBCA5D4534D668B86A5E93DB3A809">AIRをアンインストールして再インストールするようにユーザーに依頼します。 </li> 
      <li id="li_B7D2388E9FA84C26AF1C87B48AF9EF16">Flash Playerの場合は、<span class="codeph"> System.update</span>を呼び出します。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3346 </td> 
   <td colname="col2"><span class="codeph"> AAXS_MigrationFailed  </span> </td> 
   <td colname="col3"> 
    <ul id="ul_518AD4931CC64EB3A962DD451E6C5067"> 
     <li id="li_3C44F0740B08490E9C62D89C40B57DC2">ディストリビュータのソフトウェアは、次のいずれかを行う必要があります。 
      <ul id="ul_7D90526684BF4EB2BBADCF598AA13086"> 
       <li id="li_D15B4BEDAF7340F6B9BC886DF6E346EC">AIRの場合、<span class="codeph"> DRMManager.resetDRMVouchers()</span>を呼び出します。 </li> 
       <li id="li_40A51D35408249CFA28DBC49FDA3408B">エラー3322または3346のエラーコードが原因でFlashが使用できない場合は、<a href="https://forums.adobe.com/message/5535907#5535907" format="http" scope="external"> https://forums.adobe.com/message/5535907#5535907</a>に移動し、Adobe記事の指示に従ってDRMライセンスストアをプログラム的にリセットする必要があります。 </li> 
      </ul> </li> 
     <li id="li_0464471E4A094C80BF2986694341921A">このエラーが頻繁に発生する場合は、ディストリビュータは周波数プレイヤーのバージョンとブラウザーのバージョンに関する詳細をAdobeに提供する必要があります。 </li> 
    </ul> <p>詳しくは、次のフォーラム記事を参照してください。 
     <ul id="ul_44E0077FEAA749CC9549BF3846065304"> 
      <li id="li_2BE3B2443380415DA73B7AA3B6547B31"><a href="https://forums.adobe.com/message/5520902" format="https" scope="external"> ChromeでのDRMエラー3322/3346/3368（情報バーの問題）</a> </li> 
      <li id="li_4E5C7414756644E1AB78BE7B8112228C"><a href="https://forums.adobe.com/message/5535911" format="https" scope="external"> 3322または3346エラー（ハードウェア変更後）</a> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3347 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InsufficientDeviceCapabilites  </span> </td> 
   <td colname="col3"> <p>このエラーの主な意味は、ライセンスに制約があり、クライアントのDRM証明書では満たせないことが示されることです。 クライアントのDRM証明書を発行する際に、次の「ハードウェア機能」が定義されます。 
     <ul id="ul_1EB6F1469C244CF0BA52C212495C053D"> 
      <li id="li_646043CE045C4DE2BBC939E1F4963DFE"><b>ユーザーアクセス不可のバス</b>。<b>true</b>の場合、復号化されたメディアは、バスを経由したり、アプリケーションがアクセスできるメインメモリに流れ込んだりすることはありません。 <p><b>false</b>の場合は、復号化後にアプリケーションからコンテンツにアクセスできる可能性があります。 </p> </li> 
      <li id="li_02AAECAF4D35447BA10554541B46DE67"><b>ハードウェア信頼のルート</b>。<b>true</b>の場合、デバイスの起動時に読み込まれるすべてのソフトウェアが、ハードウェアでのみ使用可能なキーまたはダイジェストに対して検証されました。 <p>クライアントのDRM証明書に対してライセンスが開かれ、失敗が直ちに発生する場合は、これらの両方の制約がクライアント側でチェックされます。 これらの制約は、ライセンスを発行する前に、サーバー側でチェックすることもできます。 </p> </li> 
     </ul> </p> <p>このエラーの2つ目の意味は、ライセンスに「Jailbreak Enforcement」ポリシーが設定され、デバイスでjailbreakが検出されたことです。 このチェックは、クライアント側で定期的に行われ、サーバー側ではチェックできません。 </p> <p>配布者はポリシーを更新し、制限を削除できます。 デバイス機能ポリシーの場合は、<span class="codeph"> -devCapabilitiesV1</span>フラグを指定し、引数を指定しないで、policy updateコマンドを発行します。 JAILBREAKの強制の場合は、<span class="codeph"> policy.enforceJailbreak=false</span>を設定します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3348 </td> 
   <td colname="col2"><span class="codeph"> AAXS_HardStopIntervalExpired  </span> </td> 
   <td colname="col3"> ハードストップ間隔の有効期限が切れました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3349 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ServerVersionTooHigh  </span> </td> 
   <td colname="col3"> サーバーが、クライアントでサポートされている最新バージョンよりも新しいバージョンで実行されています。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3350 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ServerVersionTooLow  </span> </td> 
   <td colname="col3"> サーバーが、クライアントがサポートする最小バージョンより低いバージョンで実行されています。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3351 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DomainTokenInvalid  </span> </td> 
   <td colname="col3"> ドメイントークンが無効でした。 この問題を解決するには、ドメインに再度登録します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3352 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DomainTokenTooOld  </span> </td> 
   <td colname="col3"> ドメイントークンが、ライセンスで必要なトークンより古い。 この問題を解決するには、ドメインに再度登録します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3353 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DomainTokenTooNew  </span> </td> 
   <td colname="col3"> ドメイントークンが、ライセンスで必要なトークンより新しい。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3354 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DomainTokenExpired  </span> </td> 
   <td colname="col3"> ドメイントークンの有効期限が切れました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3355 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DomainJoinFailed  </span> </td> 
   <td colname="col3"> ドメインの結合に失敗しました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3356 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoCorrespondingRoot  </span> </td> 
   <td colname="col3"> V3リーフライセンスのルートライセンスが見つかりませんでした。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3357 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoValidEmbeddedLicense  </span> </td> 
   <td colname="col3"> 有効な埋め込みライセンスが見つかりませんでした。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3358 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoACPProtectionAvail  </span> </td> 
   <td colname="col3"> 接続されているアナログデバイスにACP保護がないため、再生できません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3359 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoCGMSAProtectionAvail  </span> </td> 
   <td colname="col3"> 接続されているアナログデバイスにCGMS-A保護がないため、再生できません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3360 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DomainRegistrationRequired  </span> </td> 
   <td colname="col3"> コンテンツはドメイン登録が必要です。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3361 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NotRegisteredToDomain  </span> </td> 
   <td colname="col3"> 指定したメタデータのドメインにコンピュータが登録されていません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3362 </td> 
   <td colname="col2"><span class="codeph"> AAXS_OperationTimeoutError  </span> </td> 
   <td colname="col3"> 非同期操作に<span class="codeph"> maxOperationTimeout</span>より長い時間がかかりました。 iOS DRMNativeフレームワークからのみ返されます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3363 </td> 
   <td colname="col2"><span class="codeph"> AAXS_UnsupportedIOSPlaylistError  </span> </td> 
   <td colname="col3"> 渡されたM3U8プレイリストがコンテンツをサポートしていませんでした。 iOS DRMNativeフレームワークからのみ返されます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3364 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoDeviceId  </span> </td> 
   <td colname="col3"> <p>フレームワークはデバイスIDを要求しましたが、返された値が空でした。 </p> <p>ユーザーは、Chrome設定の「保護されたコンテンツ</span>の識別子を許可」チェックボックスを選択しないでください。<span class="uicontrol"> </span></p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3365 </td> 
   <td colname="col2"><span class="codeph"> AAXS_IncognitoModeNotAllowed  </span> </td> 
   <td colname="col3"> <p>このブラウザーとプラットフォームの組み合わせでは、匿名モードでのDRM保護された再生は許可されません。 </p> <p>ディストリビューターのソフトウェアは、匿名モードを終了するか、別のブラウザーを使用するようにユーザーに通知する必要があります。 詳しくは、<a href="https://forums.adobe.com/thread/1266622" format="https" scope="external"> DRMエラー3365 cause and resolution</a>を参照してください。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3366 </td> 
   <td colname="col2"><span class="codeph"> AAXS_BadParameter  </span> </td> 
   <td colname="col3"> <p>ホストランタイムは、不正なパラメーターを指定してAccessライブラリを呼び出しました。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3367 </td> 
   <td colname="col2"><span class="codeph"> AAXS_BadSignature  </span> </td> 
   <td colname="col3"> m3u8マニフェストの署名に失敗しました。 iOS DRMNativeフレームワークまたはAVEからのみ返されます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3368 </td> 
   <td colname="col2"><span class="codeph"> AAXS_UserSettingsNoAccess</span> </td> 
   <td colname="col3"> <p>ユーザーが操作を取り消したか、システムへのアクセスを許可しない設定を入力しました。 </p> <p>このエラーは、SWFバージョンが19以降の場合にのみスローされます。 下位互換性を確保するため、SWFがバージョン18以前の場合は3321がスローされます。 </p> <p>配布者のソフトウェアは、セキュリティで保護されていないプラグインへのアクセスを許可する方法の説明をユーザーに示す必要があります。 詳しくは、「<a href="https://helpx.adobe.com/adobe-access/kb/error-3321.html" format="html" scope="external"> Google Chrome unsandbox access denied</a>」および「<a href="https://forums.adobe.com/message/5520902" format="https" scope="external"> DRMエラー3322/3346/3368 in Chrome (Info-Bar Problems)</a>」を参照してください。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3369 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InterfaceNotAvailable</span> </td> 
   <td colname="col3"> <p>必要なブラウザーインターフェイスを使用できません。 この問題はPepperでのみ発生します。 Flashプラグインとブラウザーのバージョンが一致しない可能性があります。 </p> <p>配布者のソフトウェアは、ユーザーに対して、ブラウザーの最新バージョンがインストールされていることを確認するように指示する必要があります。 </p> <p> このエラーが発生する頻度が高く、リリースされるブラウザーの更新に対応する場合は、Adobeにエスカレートします。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3370 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ContentIdSettingsNoAccess</span> </td> 
   <td colname="col3"> <p>ユーザーが「<span class="uicontrol">保護されたコンテンツ</span>の識別子を許可する」設定を無効にしました。 </p> <p>ヒント： このエラーは、Pepperバージョン13.0.0.x以降で発生していました。 </p> <p>配布者のソフトウェアは、ユーザーに対して、保護されたコンテンツ</span>の<span class="uicontrol">識別子を許可する設定を有効にするように指示する必要があります。 </span></p> <p>配布者のオペレーションチームは、ユーザーに対して、保護されたコンテンツ</span>の<span class="uicontrol">識別子を許可する設定を有効にするよう指示する必要があります。 </span></p> <p>詳しくは、<a href="https://forums.adobe.com/message/6518323#6518323" format="https" scope="external"> https://forums.adobe.com/message/6518323#6518323</a>を参照してください。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3371 </td> 
   <td colname="col2"><span class="codeph"> AAXS_</span><span class="codeph"> NoOPConstraintInPixelConstraints</span> </td> 
   <td colname="col3"> <p>ライセンスの出力保護の制約に基づいて、解像度の形式が正しくありません。 </p> <p>ディストリビュータのソフトウェアは、エラーメッセージを表示する必要があります。 ユーザーに、コンテンツタイトルを付けて、ディストリビューターに問題を報告するように依頼します。 </p> <p>ディストリビュータは、有効なポリシーでコンテンツを再パッケージ化する必要があります。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3372 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ResolutionLargerThanMaxResolution</span> </td> 
   <td colname="col3"> <p>コンテンツの解像度が、出力保護制約に指定された最大解像度を超えています。 </p> <p>ディストリビューターのオペレーションチームは、ログにこのエラーが表示された場合、解決ベースの出力保護ポリシーを確認し、必要に応じてコンテンツを再パッケージ化する必要があります。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3373 </td> 
   <td colname="col2"><span class="codeph"> AAXS_MinorErr_DisplayResolutionLargerThanConstraint</span> </td> 
   <td colname="col3"> <p>コンテンツの解像度が、現在アクティブな出力保護制約で指定されている解像度よりも大きくなっています。 </p> <p>ディストリビューターのオペレーションチームは、ログにこのエラーが表示された場合、解決ベースの出力保護ポリシーを確認し、必要に応じてコンテンツを再パッケージ化する必要があります。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3374 </td> 
   <td colname="col2"><span class="codeph"> AAXS_MinorErr_ClientCommProcessFailed</span> </td> 
   <td colname="col3"> <p>クライアント側の通信処理（リクエストの生成、応答の処理、不正な認証トークンなど）中に失敗しました。 </p> <p>ディストリビューターのオペレーションチームは、ログにこのエラーが表示された場合、解決ベースの出力保護ポリシーを確認し、必要に応じてコンテンツを再パッケージ化する必要があります。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## NATIVE_ERROR:ビデオ再生値{#section_7079501250C2487499639F92EC774525}

AVEのVideo Encoderインターフェイスは、以下のビデオ再生通知を`NATIVE_ERROR`メタデータオブジェクトに返します。

<table id="table_5EEB1F60E5854452A8B0BABBE9B32651"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"><b>NATIVE_ERROR_CODEメタデータキーの値</b></th> 
   <th colname="col2" class="entry"><b>NATIVE_ERROR_NAMEメタデータキーの値</b></th> 
   <th colname="col3" class="entry"><b>説明</b></th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> -1 </td> 
   <td colname="col2"><span class="codeph"> END_OF_PERIOD</span> </td> 
   <td colname="col3"> 期間の終了。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 0 </td> 
   <td colname="col2"><span class="codeph"> SUCCESS</span> </td> 
   <td colname="col3"> 操作が成功しました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3 </td> 
   <td colname="col2"> <span class="codeph"> ASYNC_OPERATION_IN_PROGRESS</span> </td> 
   <td colname="col3"> 非同期操作。 操作の要求が行われました。 成功/失敗に関する情報は、後で入手できます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 2 </td> 
   <td colname="col2"><span class="codeph"> EOF</span> </td> 
   <td colname="col3"> ファイルの終了(EOF)条件が原因で、操作を実行できません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3 </td> 
   <td colname="col2"><span class="codeph"> DECODER_FAILED</span> </td> 
   <td colname="col3"> デコーダーが実行時に失敗しました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 4 </td> 
   <td colname="col2"><span class="codeph"> DEVICE_OPEN_ERROR</span> </td> 
   <td colname="col3"> ハードウェアデコーダーを開けませんでした。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 5 </td> 
   <td colname="col2"><span class="codeph"> FILE_NOT_FOUND  </span> </td> 
   <td colname="col3"> リソースが見つかりません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 6 </td> 
   <td colname="col2"><span class="codeph"> GENERIC_ERROR  </span> </td> 
   <td colname="col3"> 一般的なエラー。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 7 </td> 
   <td colname="col2"><span class="codeph"> IRRECOVERABLE_ERROR  </span> </td> 
   <td colname="col3"> ビデオエンジンが回復できないエラー状態です。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 8 </td> 
   <td colname="col2"><span class="codeph"> LOST_CONNECTION_RECOVERABLE  </span> </td> 
   <td colname="col3"> ネットワークエラー。回復を試みています。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 9 </td> 
   <td colname="col2"><span class="codeph"> NO_FIXED_SIZE  </span> </td> 
   <td colname="col3"> リソースのサイズを特定できません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 10 </td> 
   <td colname="col2"><span class="codeph"> NOT_IMPLEMENTED  </span> </td> 
   <td colname="col3"> 機能が実装されていません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 11 </td> 
   <td colname="col2"><span class="codeph"> OUT_OF_MEMORY  </span> </td> 
   <td colname="col3"> メモリ不足です。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 12 </td> 
   <td colname="col2"><span class="codeph"> PARSE_ERROR  </span> </td> 
   <td colname="col3"> メディアファイルの解析中にエラーが発生しました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 13 </td> 
   <td colname="col2"><span class="codeph"> SIZE_UNKNOWN  </span> </td> 
   <td colname="col3"> リソースのサイズは不明です。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 14 </td> 
   <td colname="col2"><span class="codeph"> UNDER_FLOW  </span> </td> 
   <td colname="col3"> アンダーフロー条件。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 15 </td> 
   <td colname="col2"><span class="codeph"> UNSUPPORTED_CONFIG  </span> </td> 
   <td colname="col3"> 構成はサポートされていません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 16 </td> 
   <td colname="col2"><span class="codeph"> UNSUPPORTED_OPERATION  </span> </td> 
   <td colname="col3"> 操作がサポートされていません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 17 </td> 
   <td colname="col2"><span class="codeph"> WAITING_FOR_INIT  </span> </td> 
   <td colname="col3"> まだ初期化されていません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 18 </td> 
   <td colname="col2"><span class="codeph"> INVALID_PARAMETER  </span> </td> 
   <td colname="col3"> 無効なパラメータです。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 19 </td> 
   <td colname="col2"><span class="codeph"> INVALID_OPERATION</span> </td> 
   <td colname="col3"> 操作が許可されていません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 20 </td> 
   <td colname="col2"><span class="codeph"> OP_ONLY_ALLOWED_IN_PAUSED_STATE</span> </td> 
   <td colname="col3"> 操作は一時停止中にのみ許可されます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 21 </td> 
   <td colname="col2"><span class="codeph"> OP_INVALID_WITH_AUDIO_ONLY_FILE</span> </td> 
   <td colname="col3"> 操作は、オーディオ専用ファイルには使用できません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 22 </td> 
   <td colname="col2"><span class="codeph"> PREVIOUS_STEP_SEEK_IN_PROGRESS</span> </td> 
   <td colname="col3"> 前のシーク操作がまだ進行中です。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 23 </td> 
   <td colname="col2"><span class="codeph"> SOURCE_NOT_SPECIFIED  </span> </td> 
   <td colname="col3"> リソースが指定されていません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 24 </td> 
   <td colname="col2"><span class="codeph"> RANGE_ERROR</span> </td> 
   <td colname="col3"> 指定した値は範囲外です。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 25 </td> 
   <td colname="col2"><span class="codeph"> INVALID_SEEK_TIME</span> </td> 
   <td colname="col3"> 無効なシーク時間です。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 26 </td> 
   <td colname="col2"><span class="codeph"> FILE_STRUCTURE_INVALID</span> </td> 
   <td colname="col3"> 指定したファイルは、予期された構文に従っていません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 27 </td> 
   <td colname="col2"><span class="codeph"> COMPONENT_CREATION_FAILURE</span> </td> 
   <td colname="col3"> 必須コンポーネントを作成できませんでした。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 28 </td> 
   <td colname="col2"><span class="codeph"> DRM_INIT_ERROR</span> </td> 
   <td colname="col3"> DRMコンテキストを作成できませんでした。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 29 </td> 
   <td colname="col2"><span class="codeph"> コンテナ_NOT_SUPPORTED  </span> </td> 
   <td colname="col3"> コンテナの種類がサポートされていません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 30 </td> 
   <td colname="col2"><span class="codeph"> SEEK_FAILED</span> </td> 
   <td colname="col3"> シークに失敗しました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 31 </td> 
   <td colname="col2"><span class="codeph"> CODEC_NOT_SUPPORTED</span> </td> 
   <td colname="col3"> サポートされていないコーデック。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 32 </td> 
   <td colname="col2"><span class="codeph"> NETWORK_UNAVAILABLE</span> </td> 
   <td colname="col3"> ネットワークが利用できません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 33 </td> 
   <td colname="col2"><span class="codeph"> NETWORK_ERROR</span> </td> 
   <td colname="col3"> ネットワークからのデータ取得中にエラーが発生しました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 34 </td> 
   <td colname="col2"><span class="codeph"> OVERFLOW</span> </td> 
   <td colname="col3"> オーバーフロー。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 35 </td> 
   <td colname="col2"><span class="codeph"> VIDEO_プロファイル_NOT_SUPPORTED</span> </td> 
   <td colname="col3"> サポートされていないビデオプロファイル。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 36 </td> 
   <td colname="col2"><span class="codeph"> PERIOD_NOT_LOADED</span> </td> 
   <td colname="col3"> 保留期間またはまだ読み込まれていない期間に操作が試行されました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 37 </td> 
   <td colname="col2"><span class="codeph"> INVALID_REPLACE_DURATION</span> </td> 
   <td colname="col3"> 指定した置き換え期間が無効か、ストリームの終わりを超えています。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 38 </td> 
   <td colname="col2"><span class="codeph"> CALLED_FROM_WRONG_THREAD</span> </td> 
   <td colname="col3"> APIを間違ったスレッドから呼び出すことはできません。 ほとんどの場合、APIエレメントはメインスレッドからのみ呼び出す必要があります。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 39 </td> 
   <td colname="col2"><span class="codeph"> FRAGMENT_READ_ERROR</span> </td> 
   <td colname="col3"> フラグメント読み取りエラー。 フェールオーバーが存在しません。 エンジンは次のフラグメントの読み取りを試みます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 40 </td> 
   <td colname="col2"><span class="codeph"> ABORTED</span> </td> 
   <td colname="col3"> 明示的なAbortまたはDestroyの呼び出しによって、操作が中止されました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 41 </td> 
   <td colname="col2"><span class="codeph"> UNSUPPORTED_HLS_VERSION</span> </td> 
   <td colname="col3"> このバージョンのHLSメディアは再生できません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 42 </td> 
   <td colname="col2"><span class="codeph"> CANNOT_FAIL_OVER</span> </td> 
   <td colname="col3"> フェイルオーバーできません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 43 </td> 
   <td colname="col2"><span class="codeph"> HTTP_TIME_OUT</span> </td> 
   <td colname="col3"> HTTPダウンロードがタイムアウトしました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 44 </td> 
   <td colname="col2"><span class="codeph"> NETWORK_DOWN  </span> </td> 
   <td colname="col3"> ユーザーのネットワーク接続がダウンしています。 いつでも再生が停止する可能性があり、接続が利用可能になると再開します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 45 </td> 
   <td colname="col2"><span class="codeph"> NO_USABLE_BITRATE_プロファイル</span> </td> 
   <td colname="col3"> 使用可能なビットレートプロファイルがストリームに見つかりません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 46 </td> 
   <td colname="col2"><span class="codeph"> BAD_MANIFEST_SIGNATURE</span> </td> 
   <td colname="col3"> マニフェストに不正な署名があります。 マニフェストの署名テストに失敗しました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 47 </td> 
   <td colname="col2"><span class="codeph"> CANNOT_LOAD_PLAYLIST</span> </td> 
   <td colname="col3"> プレイリストを読み込めません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 48 </td> 
   <td colname="col2"><span class="codeph"> REPLACEMENT_FAILED</span> </td> 
   <td colname="col3"> 挿入APIで指定された置き換えに失敗しました。 これは、挿入に成功したが置き換えに失敗したことを意味します。 置き換えるマニフェストがタイムラインから削除されていると、置き換えに失敗する可能性があります。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 49 </td> 
   <td colname="col2"><span class="codeph"> SWITCH_TO_ASYMMETRIC_プロファイル</span> </td> 
   <td colname="col3"> DRMが非対称プロファイルに切り替わっています。 すべてのプロファイルは期間内に整列する必要があります。 そうでない場合は、この警告がスローされ、再生が飛ぶことがあります。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 50 </td> 
   <td colname="col2"><span class="codeph"> LIVE_WINDOW_MOVED_BACKWARD</span> </td> 
   <td colname="col3"> ライブウィンドウは次に進むだけでよいと想定されています。 そうでない場合は、この警告がスローされ、ウィンドウは読み取られません。 そのため、再生が飛ぶ（または停止/長い一時停止）場合があります。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 51 </td> 
   <td colname="col2"><span class="codeph"> CURRENT_PERIOD_EXPIRED</span> </td> 
   <td colname="col3"> ライブウィンドウが現在の期間を超えました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 52 </td> 
   <td colname="col2"><span class="codeph"> CONTENT_LENGTH_MISMATCH</span> </td> 
   <td colname="col3"> HTTPサーバーから報告されるコンテンツの長さが、実際のメディアサイズと一致しませんでした。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 53 </td> 
   <td colname="col2"><span class="codeph"> PERIOD_HOLD</span> </td> 
   <td colname="col3"> setHoldAt APIで設定された時間に達したので、メディアリーダーはこれ以上読み取れません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 54 </td> 
   <td colname="col2"><span class="codeph"> LIVE_HOLD  </span> </td> 
   <td colname="col3">ライブウィンドウの終わりに達したので、メディアリーダーはセグメントを読み込めません。 サーバーがライブウィンドウに新しいメディアを広告すると、セグメントの読み込みが再開されます。 この状態は、通常、次の場合に達します。 
    <ul id="ul_FCFF658EDA4144E59970B317D6DEB624"> 
     <li id="li_2F6EEEB782D54CD999BC7CC7C0B78B48"><span class="codeph"> bufferTime</span>が高すぎます（ライブ時間の長さ以上）。 </li> 
     <li id="li_25CE97115ED64E44AA89977FB5F0DCF7">1つ以上の挿入/消去APIの組み合わせにより、追加されたメディアより多くのメディアが置き換えられました。 </li> 
     <li id="li_1B14716B2157492AB1859306D1250523">次の期間は、メディアの置き換えが保留中のライブ期間です（InsertBy APIの呼び出しが原因）。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 55 </td> 
   <td colname="col2"><span class="codeph"> BAD_MEDIA_INTERLEAVING  </span> </td> 
   <td colname="col3"> メディアのオーディオとビデオが正しくインターリーブされません。 これはパッケージ化エラーです。 この警告は、差が2秒を超えると発行されます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 56 </td> 
   <td colname="col2"><span class="codeph"> DRM_NOT_AVAILABLE</span> </td> 
   <td colname="col3"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 57 </td> 
   <td colname="col2"><span class="codeph"> PLAYBACK_NOT_AUTHORIZED</span> </td> 
   <td colname="col3"> Flash PlayerでHLS再生が有効になっていません。 AuthorizedFeatures.enableHLSPlaybackを参照してください。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 78 </td> 
   <td colname="col2"><span class="codeph"> BAD_MEDIA_SAMPLE_FOUND</span> </td> 
   <td colname="col3"> デコーダーが、デコードできない不正なサンプルを受け取りました。 通常、これは致命的なエラーではありませんが、オーディオ/ビデオに問題がある可能性を示しています。 このエラーのインスタンスが多すぎる場合は、不正なエンコードまたは不正なファイルを示しています。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 59 </td> 
   <td colname="col2"><span class="codeph"> RANGE_SPANS_READ_HEAD</span> </td> 
   <td colname="col3"> 再生が開始した後は、挿入/置換範囲に読み取りヘッドが含まれていてはなりません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 60 </td> 
   <td colname="col2"><span class="codeph"> POSTROLL_WITH_LIVE_NOT_ALLOWED</span> </td> 
   <td colname="col3"> ポストロール挿入は、ライブメディアでは使用できません。 ただし、サーバーがメディアを完了とマークした後でも使用できます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 61 </td> 
   <td colname="col2"><span class="codeph"> INTERNAL_ERROR</span> </td> 
   <td colname="col3"> 非常にまれな問題であり、常に発生しないはずです。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 62 </td> 
   <td colname="col2"><span class="codeph"> SPS_PPS_FOUND_OUTSIDE_AVCC</span> </td> 
   <td colname="col3"> ストリームが、パッケージ化の推奨に従わず、常にH264 SPS/PPSをAVCCに含める。 シーク/再生に関する問題が表示される場合があります。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 63 </td> 
   <td colname="col2"><span class="codeph"> PARTIAL_REPLACEMENT</span> </td> 
   <td colname="col3"> 挿入APIで指定された置き換えは部分的にしか行われませんでした。 replaceDurationがタイムライン期間に及んでいる場合に発生します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 64 </td> 
   <td colname="col2"><span class="codeph"> RENDITION_M3U8_ERROR</span> </td> 
   <td colname="col3"> レンディションプレイリストで読み込み中にエラーが発生しました。 これはAVEに対してのみ有効で、FlashPlayerには適用されません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 65 </td> 
   <td colname="col2"><span class="codeph"> NULL_OPERATION</span> </td> 
   <td colname="col3"> 操作は何も実行しません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 66 </td> 
   <td colname="col2"><span class="codeph"> SEGMENT_SKIPPED_ON_FAILURE</span> </td> 
   <td colname="col3"> セグメントは再生できず、失敗した場合はスキップされます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 67 </td> 
   <td colname="col2"><span class="codeph"> INCOMPATIBLE_RENDER_MODE</span> </td> 
   <td colname="col3"> 非互換のレンダリングモード。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 68 </td> 
   <td colname="col2"><span class="codeph"> PROTOCOL_NOT_SUPPORTED  </span> </td> 
   <td colname="col3"> URLで使用されるWebプロトコルはサポートされていません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 69 </td> 
   <td colname="col2"><span class="codeph"> PARSE_ERROR_INCOMPATIBLE_VERSION</span> </td> 
   <td colname="col3"> メディアファイルの解析中にエラーが発生しました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 70 </td> 
   <td colname="col2"><span class="codeph"> MANIFEST_FILE_UNEXPECTEDLY_CHANGED</span> </td> 
   <td colname="col3"> マニフェストファイルが予期しない方法で変更されました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 71 </td> 
   <td colname="col2"><span class="codeph"> CANNOT_SPLIT_TIMELINE</span> </td> 
   <td colname="col3"> 分割操作をタイムラインで実行できません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 72 </td> 
   <td colname="col2"><span class="codeph"> CANNOT_ERASE_TIMELINE</span> </td> 
   <td colname="col3"> 消去操作をタイムラインで実行できません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 73 </td> 
   <td colname="col2"><span class="codeph"> DID_NOT_GET_NEXT_FRAGMENT</span> </td> 
   <td colname="col3"> 次のフラグメントを取得しませんでした。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 74 </td> 
   <td colname="col2"><span class="codeph"> NO_TIMELINE</span> </td> 
   <td colname="col3"> 内部データ構造にタイムラインがありません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 75 </td> 
   <td colname="col2"><span class="codeph"> LISTENER_NOT_FOUND</span> </td> 
   <td colname="col3"> 内部データ構造にリスナーが見つかりません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 76 </td> 
   <td colname="col2"><span class="codeph"> AUDIO_開始_ERROR</span> </td> 
   <td colname="col3"> オーディオを開始できません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 77 </td> 
   <td colname="col2"><span class="codeph"> NO_AUDIO_SINK</span> </td> 
   <td colname="col3"> 内部データ構造にオーディオシンクがありません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 78 </td> 
   <td colname="col2"><span class="codeph"> FILE_OPEN_ERROR</span> </td> 
   <td colname="col3"> ファイルを開けません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 79 </td> 
   <td colname="col2"><span class="codeph"> FILE_WRITE_ERROR</span> </td> 
   <td colname="col3"> ファイルに書き込めません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 80 </td> 
   <td colname="col2"><span class="codeph"> FILE_READ_ERROR</span> </td> 
   <td colname="col3"> ファイルから読み取れません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 81 </td> 
   <td colname="col2"><span class="codeph"> ID3PARSE_ERROR</span> </td> 
   <td colname="col3"> ID3データの解析中にエラーが発生しました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 82 </td> 
   <td colname="col2"><span class="codeph"> SECURITY_ERROR  </span> </td> 
   <td colname="col3"> セキュリティ上の制約により、コンテンツの読み込みに失敗しました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 83 </td> 
   <td colname="col2"><span class="codeph"> TIMELINE_TOO_SHORT</span> </td> 
   <td colname="col3"> タイムラインの時間が短すぎます。 これがライブストリームの場合、バッファリングが頻繁に発生する可能性があります。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 84 </td> 
   <td colname="col2"><span class="codeph"> AUDIO_ONLY_STREAM_開始</span> </td> 
   <td colname="col3"> ストリームがオーディオ専用ストリームに切り替えられました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 85 </td> 
   <td colname="col2"><span class="codeph"> AUDIO_ONLY_STREAM_END</span> </td> 
   <td colname="col3"> ストリームがオーディオ専用からビデオ付きストリームに切り替えられました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 87 </td> 
   <td colname="col2"><span class="codeph"> KEY_NOT_FOUND  </span> </td> 
   <td colname="col3"> キーが見つかりません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 88 </td> 
   <td colname="col2"><span class="codeph"> INVALID_KEY</span> </td> 
   <td colname="col3"> キーが無効です。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 89 </td> 
   <td colname="col2"> <span class="codeph"> KEY_SERVER_NOT_FOUND</span> </td> 
   <td colname="col3"> キーサーバーはキーを返しません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 90 </td> 
   <td colname="col2"> <span class="codeph"> MAIN_MANIFEST_UPDATE_TO_BE_HANDLED</span> </td> 
   <td colname="col3"> メインマニフェストの更新を処理できません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 91 </td> 
   <td colname="col2"> <span class="codeph"> UNREPORTED_TIME_DISCONTINUITY_FOUND</span> </td> 
   <td colname="col3"> 報告されない時間(PTS)不連続が見つかりました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 92 </td> 
   <td colname="col2"> <span class="codeph"> UNMATCHED_AV_DISCONTINUITY_FOUND</span> </td> 
   <td colname="col3"> 一致しないオーディオとビデオの不連続性が見つかりました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 93 </td> 
   <td colname="col2"><span class="codeph"> TRICKPLAY_ENDED_DUE_TO_ERROR</span> </td> 
   <td colname="col3"><i>トリック再生</i>モードでメディアを再生中にエラーが発生しました。 トリック再生モードが終了し、ストリームが一時停止します。 <span class="codeph"> Play()</span>を呼び出して、メディアを通常モードで再生します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 95 </td> 
   <td colname="col2"><span class="codeph"> LIVE_WINDOW_MOVED_AHEAD</span> </td> 
   <td colname="col3"> プレイヤーはライブウィンドウから外れており、追いつくために前方にシークする必要があります。 </td> 
  </tr> 
 </tbody> 
</table>

## NATIVE_ERROR:暗号化値{#section_39365E545CAC49B9A4D4678657BB2155}

Adobeビデオエンジンの暗号化モジュールは、`NATIVE_ERROR`メタデータオブジェクトに以下の通知を返します。

| **NATIVE_ERROR_CODEメタデータキーの値** | **NATIVE_ERROR_NAMEメタデータキーの値** | **意味** |
|---|---|---|
| 300 | `CRYPTO_ALGORITHM_NOT_SUPPORTED` | 使用中のアルゴリズムはサポートされていません。 |
| 301 | `CRYPTO_ERROR_CORRUPTED_DATA` | データが破損しています。 |
| 302 | `CRYPTO_ERROR_BUFFER_TOO_SMALL` | バッファが小さすぎます。 |
| 303 | `CRYPTO_ERROR_BAD_CERTIFICATE` | 不正な証明書。 |
| 304 | `CRYPTO_ERROR_DIGEST_UPDATE` | ダイジェストの更新。 |
| 305 | `CRYPTO_ERROR_DIGEST_FINISH` | ダイジェストの終了。 |
| 306 | `CRYPTO_ERROR_BAD_PARAMETER` | 無効なパラメータです。 |
