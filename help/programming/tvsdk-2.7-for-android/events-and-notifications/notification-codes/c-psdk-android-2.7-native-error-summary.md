---
title: NATIVE_ERROR 通知の詳細
description: NATIVE_ERROR 通知の詳細
copied-description: true
exl-id: 51c75349-0fa8-405d-9e09-b51b425fe21b
source-git-commit: 1bc2f6c230c262babf2958c32fee31afcad04c2f
workflow-type: tm+mt
source-wordcount: '6868'
ht-degree: 2%

---

# NATIVE_ERROR 通知の詳細 {#details-for-the-native-error-notification}

TVSDK は、ネイティブエラーを処理すると、以下のメタデータキー値の一部またはすべてを文字列として返します。

<table id="table_7F713B7A56024D8DA3C84E449D09CC91"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> メタデータキー名 </th> 
   <th colname="col2" class="entry"> メタデータ値 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> NATIVE_ERROR_CODE</span> </td> 
   <td colname="col2"> <p>AVE からのネイティブエラーコードです。 </p> <p>これらのコードは、次を表します。 
     <ul id="ul_1F33D523DDFE4CE8B4F0DC279FF7E4F8"> 
      <li id="li_07A2D9BEE6364935A61EF3BD4AB6DE27">DRM エラー（コード 3300 ～ 3367）。 これらは、同等のFlash Playerエラーコードと同じです </li> 
      <li id="li_433BA22DE3504AEEB623598BB4F939FA">ビデオ再生エラー (-1 ～ 89) </li> 
      <li id="li_B347CB151DB94DE0A1DDEB1B33D2DABA">暗号化エラー (300 ～ 307) </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> NATIVE_ERROR</span> </td> 
   <td colname="col2">通知の短い説明 ( 例： <span class="codeph"> AAXS_InvalidVoucher</span> または <span class="codeph"> DECODER_FAILED</span>) をクリックします。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> 説明</span> </td> 
   <td colname="col2"> 通知の詳細な説明（広告解決操作が失敗したなど）。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> PSDK_ERROR_CODE</span> </td> 
   <td colname="col2"><span class="codeph"> com.adobe.mediacore.PSDKErrorCode</span> 数値を文字列として使用します（例：「13」）。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> PSDK_ERROR</span> </td> 
   <td colname="col2"><span class="codeph"> com.adobe.mediacore.PSDKErrorCode</span> 文字列として ( 例えば、 <span class="codeph"> kECNetworkError</span>) をクリックします。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> 警告</span> </td> 
   <td colname="col2"> 警告の説明。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> エラー</span> </td> 
   <td colname="col2"> エラーの説明。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>DRM</b> </td> 
   <td colname="col2"></td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> NATIVE_SUBERROR_CODE</span> </td> 
   <td colname="col2"> DRM モジュールからの軽微なエラー。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> DRM_ERROR_STRING</span> </td> 
   <td colname="col2"> エラーの説明。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> DRM_ERROR_SERVER_URL</span> </td> 
   <td colname="col2"> TVSDK が通信を試みた DRM サーバーの URL。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>広告マニフェストの読み込みに失敗しました</b> </td> 
   <td colname="col2"></td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AD_URL</span> </td> 
   <td colname="col2"> 読み込めなかったコンテンツの URL。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AD_TYPE</span> </td> 
   <td colname="col2">広告のタイプ ( <span class="codeph"> MediaResource.Type</span> enum)。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AD_DURATION</span> </td> 
   <td colname="col2"> 広告の時間（ミリ秒）。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AD_ID</span> </td> 
   <td colname="col2"> 広告に割り当てられた ID。 </td> 
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
   <td colname="col2"> ダウンロードされるファイルの URL。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> MANIFEST_ERROR</span> </td> 
   <td colname="col2"> マニフェストファイルのダウンロード中のエラーの説明。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> CONTENT_ERROR</span> </td> 
   <td colname="col2">フラグメント中のエラーの説明 ( 例： <span class="codeph"> ts</span>) をダウンロードします。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>オーディオトラックエラー</b> </td> 
   <td colname="col2"></td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AUDIO_TRACK_NAME</span> </td> 
   <td colname="col2"> マニフェストで指定されている、読み込みに失敗したオーディオトラックの名前。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AUDIO_TRACK_LANGUAGE</span> </td> 
   <td colname="col2"> マニフェストで指定されているオーディオトラックの言語。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>シークエラー</b> </td> 
   <td colname="col2"></td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> DESIRED_SEEK_PERIOD</span> </td> 
   <td colname="col2"> 期間の ID （整数）。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> DESIRED_SEEK_POSITION</span> </td> 
   <td colname="col2"> <p>位置（ミリ秒単位）が必要です（倍）。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>その他</b> </td> 
   <td colname="col2"></td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> Auditude_エラーコード</span> </td> 
   <td colname="col2"> Auditudeエラーコード（数値）。 </td> 
  </tr> 
 </tbody> 
</table>

## NATIVE_ERROR:DRM 値 {#section_D240082B93D34902A18C3923C1C717B3}

Adobeビデオエンジンの Video Encoder インターフェイスは、 `NATIVE_ERROR` メタデータオブジェクト。

DRM エラーをAdobeに報告する場合は、 `NATIVE_SUBERROR_CODE` および `DRM_ERROR_STRING` トラブルシューティングのサポートが必要です。

>[!TIP]
>
>このリストは、TVSDK 固有のエラーに関する情報を提供します。 詳しい説明については、 [Adobe Flash PlatformのActionScriptランタイムエラーActionScriptリファレンス](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/runtimeErrors.html#3300).

<table id="table_CD59A859865F4FFDBAA249C89C74770A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> NATIVE_- ERROR_CODE メタデータ・キーの値 </th> 
   <th colname="col2" class="entry"> NATIVE_ERROR_NAME メタデータキーの値 </th> 
   <th colname="col3" class="entry"> 意味 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> 3300 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InvalidVoucher</span> </td> 
   <td colname="col3"> 
    <ul id="ul_516E4CB32D624B22892DDB9266CB04CA"> 
     <li id="li_348FC0F38B11417994119B61C9244076">ディストリビュータのソフトウェアが行うべきこと： 
      <ul id="ul_7AFD45CF92454BA4927783FAA628FBC4"> 
       <li id="li_0D9CCE61612643648C12DCDDD252E52A">Google Chrome を使用していて、匿名モードで、Flash Playerのバージョンが 11.6 未満の場合は、このエラーが発生する可能性があります。 <p>プレーヤーはブラウザーのバージョン番号を確認し、ユーザーに匿名モードを終了するように通知することをお勧めします。 </p> </li> 
       <li id="li_1DC6B755BD0840D48BEC92568FD330BA">ライセンスを再度リクエストします。 <p>リクエストが成功した場合、ログまたはエスカレーションする必要はありません。 リクエストが失敗した場合は、エラーの原因となったコンテンツを記録します。 <span class="codeph"> subErrorId</span> には、存在する場合に行エラーが含まれます。 </p> </li> 
      </ul> </li> 
     <li id="li_060B5D60C9BB419CBFA7B062FBCF2632">ディストリビューターが実行すべきこと： 
      <ul id="ul_FADB29DBF0DA4A0E8E54134AEB7DCD8A"> 
       <li id="li_FC5B1C04D21E4AECB0EBD9ADD3198504">バージョン 11.6 より前の Chrome 以外のFlashで再試行が失敗した場合は、パッケージでエラーが発生している可能性があります。 </li> 
       <li id="li_A720ECE591254021879B335B81B1F76D">問題が特定のコンテンツに固有かどうかを確認し、再パッケージ化します。 </li> 
      </ul> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3301 </td> 
   <td colname="col2"><span class="codeph"> AAXS_AuthenticationFailed</span> </td> 
   <td colname="col3"> <p>サーバーがクライアントの認証または認証に失敗しました。 </p> 
    <ul id="ul_BE77AC1848FB4C09B6318359ACF1B8EE"> 
     <li id="li_6FB37D317D174E8488C5070D20CD241C">配布者のソフトウェアは、ユーザーの資格情報を再確立するために必要なアクションを実行するか、ユーザーがコンテンツへのアクセスを取得するように指示する必要があります。 </li> 
     <li id="li_BE071D59805B42D38E3E7650BC936417">ディストリビュータは、ディストリビュータの承認と認証のメカニズムが正しく機能していることを確認する必要があります。 <p>ディストリビューターが認証機能や認証機能を使用する予定がない場合は、問題のあるコンテンツのポリシーに認証が必要かどうかを確認し、ポリシー/ライセンスの不一致の診断を参照してください。 </p> </li> 
    </ul> <p>このエラーコードについて詳しくは、 <a href="https://forums.adobe.com/thread/1277149" format="https" scope="external"> DRM エラー 3301 の原因と解決</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3302 </td> 
   <td colname="col2"><span class="codeph"> AAXS_RequireSSL</span> </td> 
   <td colname="col3"> <p>Access 4.0 以降では、リモートキー URL がスキームとして HTTPS を使用していない場合に、このエラーがiOSでスローされます。 HTTPS が必要です。 </p> 
    <ul id="ul_3D47777BBCA14B67B107FBBE3E37E40C"> 
     <li id="li_7F7BBB27AE754CC39ABAAF9269739C49">ディストリビューターが Access v4 より古いバージョンを使用している場合、または少なくとも 4 つのバージョンを使用しているが、プラットフォームがiOSでない場合、ディストリビューターのソフトウェアはエラーをログに記録する必要があります。 <p>エラーはiOSでのみスローされます。 </p> </li> 
     <li id="li_D83C427D2A0D47408F723EF7195070B6">ディストリビュータのソフトウェアが少なくともAdobeアクセスバージョン 4 で、プラットフォームがiOSの場合、ディストリビュータは、HTTPS に使用するリモートキーサーバー URL を変更する必要があります。 <p>HTTP のみを使用している場合は、ディストリビューターが HTTPS サーバーを設定する必要がある場合があります。 それ以外の場合は、ディストリビューターは、ログに記録された情報をAdobeに送信し、問題をエスカレーションする必要があります。 </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3303 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ContentExpired</span> </td> 
   <td colname="col3"> <p>表示中のコンテンツは、コンテンツプロバイダーが設定したルールに従って期限切れになっています。 subErrorId には、クライアント固有のエラーまたは行エラーが含まれます。 </p> <p> 
     <ul id="ul_1E4B3B8AE87A4E79997553BB2A0E52B9"> 
      <li id="li_EE3F2EEBF73743B9A38E4FCB7531E275">ディストリビュータのソフトウェアは、期限切れでない新しいライセンスが使用可能かどうかを確認するために、サーバからライセンスを 1 回取得しようとします。 <p>使用可能なライセンスがない場合、またはライセンスが期限切れの場合は、ユーザーが新しいライセンスを取得するか、コンテンツを視聴できないことをユーザーに通知します。有効期限/終了日が切れたポリシーでパッケージ化された場合、 <span class="codeph"> PolicyEvaluationException</span> ポリシー終了日が過ぎたことを示すメッセージが表示されます（サーバーエラーコード 303）。 確認するサーバーのログファイルを確認します。 </p> <p>可能な場合は、パッケージ化中に使用したポリシーをチェックして、期限切れかどうかを確認する必要があります。 Java コマンドラインツールは次のとおりです。 
        <code>
         java&nbsp;-jar&nbsp;libs/AdobePolicyManager.jar&nbsp;&nbsp;&nbsp;detail&nbsp;demo.pol
        </code> </p> </li> 
      <li id="li_50DBE680D8F04E7DA3E29C65A93188E7">配布者は、ライセンスの有効期限が意図したとおりに設定されているかどうかを確認する必要があります。 </li> 
     </ul> </p> <p>このエラーコードについて詳しくは、 <a href="https://forums.adobe.com/thread/1300813" format="https" scope="external"> ライブストリームを使用する AMS/FMS での 3303（コンテンツ期限切れ）</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3304 </td> 
   <td colname="col2"><span class="codeph"> AAXS_AuthorizationFailed</span> </td> 
   <td colname="col3">このエラーコードについて詳しくは、 <a href="https://forums.adobe.com/thread/1277149" format="https" scope="external"> DRM エラー 3301 の原因と解決</a>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3305 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ServerConnectionFailed</span> </td> 
   <td colname="col3"> <p>ネットワーク遅延またはクライアントがオフラインのため、ライセンスまたはドメインサーバーへの接続がタイムアウトしました。 通常、subErrorId には HTTP リターンコードが含まれます。 </p> 
    <ul id="ul_938C7D8F07F64B4FA71A09DDF37E2E64"> 
     <li id="li_6648EA0049094E369BD9AE9CCA6B148D">ディストリビュータのソフトウェアは、正常なサーバへのネットワーク接続を試みる必要があります。 <p>試行に失敗した場合は、ネットワークに再接続するように促します。 成功した場合は、ログに記録します。 </p> </li> 
     <li id="li_2ECA2C04BA08449DA3AD79A52EFAA229">ディストリビュータは、使用中のライセンスとドメインサーバがオンラインで、クライアントのネットワークから見えることを確認する必要があります。 </li> 
    </ul> <p>このエラーコードについて詳しくは、 <a href="https://forums.adobe.com/thread/1284947" format="https" scope="external"> DRM 3305 [ServerConnectionFailed] の原因と解決</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3306 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ClientUpdateRequire</span> </td> 
   <td colname="col3"> Android 向け TVSDK の新しいバージョンを使用します。 <p>現在のクライアントは要求された操作を完了できませんが、更新されたクライアントが要求を完了できる可能性があります。 </p> <p>これには、次のような複数の原因が考えられます。 
     <ul id="ul_2EC4D42D5273439FA1AFDA1A2578B3D6"> 
      <li id="li_FCA926F5FAED4E7190BE855545AB6ACF">このクライアントで使用できない共有ドメインが使用されました。 これは、Chrome で再生が動作する場合に起こりますが、他のブラウザーでは動作しない場合に起こります（逆の場合も同様です）。 <p> <p>ヒント：Chrome では、他のブラウザーとは異なる PHDS/PHLS キーを使用します。 詳しくは、 <a href="https://adobeprimetime.zendesk.com/agent/tickets/2891" format="https" scope="external"> https://adobeprimetime.zendesk.com/agent/tickets/2891</a>. </p> </p> </li> 
      <li id="li_3B633FB699234DCEA136E9BE3CC3386D">5.0 より前のバージョンのiOSで実行している場合、アプリケーションは複数の DRMSessions を追加しようとしています。 </li> 
      <li id="li_F7ED993AF0B941A7A27216B4D587A999">バージョン 2 のみがサポートされている場合、メタデータのバージョンは 3 以降です。 </li> 
     </ul> </p> 
    <ul id="ul_EE4AE6AD4F1745A5B5623E53B599DB62"> 
     <li id="li_7A83869D4262443DA35FA1DF8D3097DD">ディストリビュータのソフトウェアは、ユーザに警告し、操作を中止する必要があります。 <p>ソフトウェアがアップグレードが使用可能かどうかを判断する方法を持っている場合は、ユーザーに対して、プラットフォームに適した方法でそのアップグレードを指示します。 </p> </li> 
     <li id="li_AF9C2711FDE54DA196EB9D2864632000">共有ドメインが原因で問題が発生した場合、ディストリビューターは、更新されたランタイムまたはライブラリをAdobeで確認する必要があります。 <p>Flashランタイムの場合、ディストリビューターは、アプリケーションで直接アップグレードを強制できます。 ライブラリの場合、ディストリビューターは、更新されたライブラリを取得し、アプリケーションを再構築して、ユーザーにデプロイする必要があります。 </p> <p>複数の DRMSessions が原因で問題が発生した場合、ディストリビューターは、複数の DRMSession を追加する前に、アプリケーションを更新してiOSのバージョン番号を確認する必要があります。 または、アプリケーションの配布をiOS v5 以降に制限することもできます。 </p> <p>メタデータのバージョンがバージョン 2 よりも高いために問題が発生した場合は、問題が破損しているメタデータである可能性があります。 メタデータを再構築して結果を確認することができます。 問題が解決しない場合は、問題をログに記録し、Adobeにエスカレーションします。 </p> </li> 
    </ul> <p>このエラーコードについて詳しくは、 <a href="https://forums.adobe.com/thread/1266675" format="https" scope="external"> 3306 DRMErrorEvent エラーコードの修正方法</a> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3307 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InternalFailure</span> </td> 
   <td colname="col3"> <p>これは通常、Adobeアクセスコードのバグを表し、以下に示す既知のバグがない限り、予期しないバグです。 subErrorId には、クライアント固有のエラーまたは行エラーが含まれます。 </p> 
    <ul id="ul_79F4A9655A2148519B1E9509C41F78C3"> 
     <li id="li_0E093AB4D6BD489B852279E6C1525A15">ブラウザーが Windows 上で Chrome で、Flashのバージョンが 11.6 (SWFのバージョン 19 以降 ) の場合、ディストリビューターのソフトウェアは、ユーザーが <span class="uicontrol"> 拒否</span> infobar 上では 3368 と同じように扱います。 </li> 
     <li id="li_0215D1089B344861A2C0A73E1067CFEF">ブラウザーが Chrome でない場合、またはFlashのバージョンが 11.6 でない場合に 3307 が発生すると、ディストリビューターはAdobeにエスカレーションする必要があります。 </li> 
    </ul> <p>重要： <span class="codeph"> 3307:1107296344 (FailedToGetBrokerHandle)</span> は、Chrome ブラウザーバージョン 24 ～ 28 で発生する可能性があります。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3308 </td> 
   <td colname="col2"><span class="codeph"> AAXS_WrongLicenseKey</span> </td> 
   <td colname="col3"> <p>このエラーは、使用中のライセンスに、コンテンツを復号化するための誤ったキーが含まれている場合にスローされます。 subErrorId には、クライアント固有のエラーまたは行エラーが含まれます。 </p> <p>このバグを生成する方法は 2 つだけのようです。 
     <ul id="ul_1C955BD74C7843809D1B5A0CDCA5ED7B"> 
      <li id="li_18F0A7FDA6584887AD9DB3EDE54080D8">お客様は、ライセンスを生成するための標準Adobeツール（例えば、ライセンサーサーバー Java フレームワーク）を変更しました。 <p>この場合、ライセンスに無効なキーが含まれており、どのコンテンツにも対応していない可能性があります。 </p> </li> 
      <li id="li_21D04ED1F1FA464785BC297D385766FF">お客様が同じライセンス ID の複数のライセンスを発行している。 <p>この場合、クライアント上で使用可能なライセンスがコンテンツメタデータに一致し、アクセスコードによって誤ったライセンスが選択されて使用されます。 </p> </li> 
     </ul> </p> 
    <ul id="ul_64AEE62BE36946F290067CF475A36ECA"> 
     <li id="li_9EEB2B11A4DA41E78C5840D8FAA81F0D">ディストリビュータのソフトウェアは、サーバからライセンスを取得しようとします。 
      <ul id="ul_ACADC5518B054D0A853AEED2B675DB23"> 
       <li id="li_394835C8731048A5BF7D9370AC12448C">使用可能なライセンスがない場合や、ライセンス期限が切れている場合は、新しいライセンスを取得するためのワークフローを提供するか、コンテンツを視聴できないことをユーザーに通知して問題をログに記録します。 </li> 
       <li id="li_3FE50518BE53405F9563FA620F7EAD5F">これが (AIRの ) ドメインバインドコンテンツの場合、ユーザーがドメインに参加する方法を提供します。 </li> 
      </ul> </li> 
     <li id="li_C80B353C1AEA4E9398241420CB491E84">配布者は、次の事項を行う必要があります。 
      <ul id="ul_B5C50009374C4EED9B2B050B48F5F0F6"> 
       <li id="li_D5E6B760E0BC4B5C949ED1544B398838">Access License Server のライセンス発行部分がカスタマイズされていないことを確認します。 </li> 
       <li id="li_AA8F4E4B6DDD40BA8807C0920A92186B">すべてのライセンスに対して一意のライセンス ID を発行していることを確認します。 </li> 
       <li id="li_A2C53FE779AC4FDDB65E00A2C4F43EC4">問題のエスカレーションとAdobe。 </li> 
      </ul> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3309 </td> 
   <td colname="col2"><span class="codeph"> AAXS_CorruptedAdditionalHeader </span> </td> 
   <td colname="col3"> <p>ヘッダーが65536バイトを超える場合に発生します。 </p> 
    <ul id="ul_82C0F688519B4F43A764D59A891F1903"> 
     <li id="li_E66AC9149A0649E88A79C5289C12C395">ディストリビュータのソフトウェアは、エラーを発生させたコンテンツの一部をログに記録する必要があります。 </li> 
     <li id="li_1C5916A33E7B4DC9968105B9BD20A727">ディストリビューターは、特定のコンテンツでエラーが再現できることを確認する必要があります。 壊れたコンテンツを再パッケージ化します。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3310 </td> 
   <td colname="col2"><span class="codeph"> AAXS_AppIDMismatch </span> </td> 
   <td colname="col3">Android アプリケーションが使用中のアプリケーションと一致しません。 <p>正しいAIRアプリケーションまたはFlashSWFが使用されていません。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3311 </td> 
   <td colname="col2"><span class="codeph"> AAXS_AppVersionMismatch </span> </td> 
   <td colname="col3"> 使用されていません。 この問題は、AIRのバージョン 1.x スタックで引き続き発生する可能性があります。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3312 </td> 
   <td colname="col2"><span class="codeph"> AAXS_LicenseIntegrity </span> </td> 
   <td colname="col3"> この問題を修正するには、サーバーからライセンスを再ダウンロードします。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3313 </td> 
   <td colname="col2"><span class="codeph"> AAXS_WriteMicrosafeFailed </span> </td> 
   <td colname="col3"> <p>この問題は、システムがファイルシステムに書き込めない場合に発生します。 <span class="codeph"> subErrorId</span> クライアント固有のエラーまたはラインエラーが含まれます。 </p> <p>Microsoft Windows では、暗号化されたコンテンツに licenseID または policyID が長すぎると、Active X または NPAPI プラグインフラッシュプレーヤーによってエラー 3313 がスローされる場合があります。 これは、Windows のパスの長さの最大値が原因です。 （Pepper プラグインにはこの問題はありません。） </p> <p>ワトソン3549660を参照 </p> 
    <ul id="ul_DFD527D1E1224A439766DF7BED878E3B"> 
     <li id="li_FAF8FD98A4E8478CA7A92F770676ADFC">ディストリビュータのソフトウェアは、ユーザのディレクトリがロックされていないか、またはフルまたはロックされたボリューム上にあるかをユーザに確認するように求めるプロンプトを表示します。 </li> 
     <li id="li_6D1136EA750A459BBECEEE5F73F527BB">配布者がFlashではなくAIRを使用している場合は、パスの長さ制限が原因で問題が発生する可能性があります。 <p>ディストリビューターは、AIRの申し込みを合理的なものに短縮する必要があります。 また、短時間で再度コンテンツを公開します <span class="codeph"> licenseID</span> および <span class="codeph"> policyID</span>. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3314 </td> 
   <td colname="col2"><span class="codeph"> AAXS_CorruptedDRMMetadata </span> </td> 
   <td colname="col3"> <p>このエラーは、多くの場合、コンテンツがテスト PKI 証明書でパッケージ化され、プレーヤーが実稼動 PKI でビルドされたか、またはその逆でビルドされたかを示します。 subErrorId には、クライアント固有のエラーまたは行エラーが含まれます。 </p> 
    <ul id="ul_A122EF304CAF48A8B4DA1E3F4413E29B"> 
     <li id="li_A9A1A5B23E884C22A71E2DE7535FEB3B">ディストリビューターのソフトウェアは、エラーが発生したコンテンツの一部をログに記録する必要があります。 </li> 
     <li id="li_7AD7F13A4B1B4998A7E49664E7645815">ディストリビュータは、特定のコンテンツでエラーが再現できることを確認する必要があります。 <p>壊れたコンテンツを再パッケージ化する必要がある場合があります。 </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3315 </td> 
   <td colname="col2"><span class="codeph"> AAXS_PermissionDenied </span> </td> 
   <td colname="col3"> <p>3305 が意図されているときにこのエラーコードがスローされる既知のバグがあります。 詳しくは、 <a href="https://forums.adobe.com/thread/1284947" format="https" scope="external"> DRM 3305 [ServerConnectionFailed] の原因と解決</a>. </p> <p>AIRによって読み込まれたリモートSWFは、Flash Access機能にアクセスできません。 このエラーコードは、ネットワークアクセス中にセキュリティエラーが発生した場合にもスローされます。 例えば、crossdomain.xml を使用して接続するクライアントが宛先サーバーにいない、または crossdomain.xml に接続できないなどです。 </p> <p>詳しくは、 <a href="https://forums.adobe.com/thread/1266592" format="https" scope="external"> DRM エラー 3315 考えられる根本原因と解決策</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3316 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NOTUSED_MOVED </span> </td> 
   <td colname="col3"> は <span class="codeph"> ADOBECPSHIM_MinorErr_MissingAdobeCPModule</span>. エラーコードとの競合が原因で、3344 にFlashしました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3317 </td> 
   <td colname="col2"><span class="codeph"> AAXS_LoadAdobeCPFailed </span> </td> 
   <td colname="col3"> <p>重要：これはまれなエラーであり、通常、実稼動環境では発生しません。 </p> <p>エラーが発生した場合は、次のいずれかの操作を実行できます。 
     <ul id="ul_BC435E61623444BB98A86216531DC892"> 
      <li id="li_FA433D0758B642D2AFDCF04906B3FE18">AIRを使用している場合は、再インストールします。 </li> 
      <li id="li_F08D9AAFF46244F8842DEE5FD9CBBE0A">Flash Playerを使用している場合は、 <span class="codeph"> AdobeCP</span> モジュールを再度追加しました。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3318 </td> 
   <td colname="col2"><span class="codeph"> AAXS_IncompatibleAdobeCPVersion </span> </td> 
   <td colname="col3"> Android には適用されません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3319 </td> 
   <td colname="col2"><span class="codeph"> AAXS_MissingAdobeCPGetAPI </span> </td> 
   <td colname="col3"> Android には適用されません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3320 </td> 
   <td colname="col2"><span class="codeph"> AAXS_HostAuthenticateFailed </span> </td> 
   <td colname="col3"> Android には適用されません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3321 </td> 
   <td colname="col2"><span class="codeph"> AAXS_I15nFailed </span> </td> 
   <td colname="col3"> <p>キーを使用してクライアントをプロビジョニングするプロセスが失敗しました。 subErrorId には、クライアント固有のエラー、サーバー固有のエラー、または行エラーが含まれます。 </p> 
    <ul id="ul_98D919B9060A441AACB6106F6D8E8DA7"> 
     <li id="li_DCAB00A8AC4A426CBBD377374B3F71AE">ディストリビュータのソフトウェアは、少なくとも 1 回は操作を再試行する必要があります。 <p>Windows でGoogle Chrome を使用している場合は、サンドボックスにないプラグインアクセスを許可する方法について説明します。 Google Chrome のサンドボックス解除のアクセスが拒否されました</a>. </p> </li> 
     <li id="li_7FB7681FE32D444BB1BDBA3E5953A2C3">ディストリビューターは、次のタスクのいずれかを実行する必要があります。 
      <ul id="ul_486B64F187C44AE3B4775953A6142836"> 
       <li id="li_095B1D4CD051427CB2BFA7082B454056">プラットフォーム間でエラーの一貫性がある場合は、問題をエスカレーションして、Adobeを実施する必要があります。 </li> 
       <li id="li_0C6EB7B912FA41E59657216498DA3515">エラーが Windows 上の Chrome に限定されている場合は、サンドボックス化されていないプラグインへのアクセスをユーザーに許可するように指示します。 </li> 
      </ul> <p>ディストリビューターは、SWFをバージョン 19 以降に更新する必要があり、Chrome 固有の 3321 エラーが発生すると、3368 エラーが発生します。 エラー 3368 は、ディストリビュータのソフトウェアによってより具体的に処理できます。 この変更は、Chrome 安定チャネルバージョン 26.0.1410.43 で導入されました。 </p> <p>ヒント：エラー <span class="codeph"> 3321:1090519056</span> は、Flash Playerのバージョン 11.1 ～ 11.6 で発生する場合があります。最新のFlash Playerバージョンにアップグレードすることをお勧めします。 </p> </li> 
    </ul> <p>詳しくは、 <a href="https://forums.adobe.com/thread/1277138" format="https" scope="external"> DRM エラー 3321 原因と解決</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>グローバルストアの破損エラー</b> </td> 
   <td colname="col2"> </td>
   <td colname="col3"> </td>
  </tr> 
  <tr> 
   <td colname="col1"> 3322 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DeviceBindingFailed </span> </td> 
   <td colname="col3"> <p>初期化時に存在した設定とデバイスが一致しないようです。 subErrorId には、クライアント固有のエラーまたは行エラーが含まれます。 </p> <p>ディストリビュータのソフトウェアは、次のタスクのいずれかを完了する必要があります。 
     <ul id="ul_444401051A2E407B95BC44491E9BB71C"> 
      <li id="li_93493EA05DB44CB1AEC368663F1ABA8D"> <p>デバイスがFlash Playerを使用しておらず、AIR、iOSなどを使用している場合は、を呼び出します。 <span class="codeph"> DRMManager.resetDRMVouchers()</span>. </p> <p>開発フェーズでiOSで問題が発生した場合は、開発者に問い合わせて、サードパーティのプレリリース配布システム（例：HockeyApp）からダウンロードしたビルドと Xcode からローカルビルドを切り替える際に問題が発生しているかどうかを確認します。 HockeyApp から配布されたビルドと Xcode からのビルドを切り替えると、以前のインストールの属性が完全に上書きされるわけではありません。 この状況では、3322 エラーがトリガーする場合があります。 </p> <p>この問題を解決するには、デベロッパーが新しいビルドをインストールする前に、デバイスから古いビルドを削除する必要があります。 </p> </li> 
      <li id="li_A5C9633F11584C788A2D9A23CC18FA6D">Flash Playerを使用していて、3322 または 3346 のエラーコードで使用できない場合は、Adobeの説明に従って、 <a href="https://forums.adobe.com/message/5535907#5535907" format="https" scope="external"> Chrome での DRM エラー3322/3346/3368（情報バーの問題）</a>. </li> 
     </ul> </p> <p>このエラーは頻繁に発生するとは限りません。 ローミングプロファイルを使用する企業環境で、DRM で保護されたコンテンツをユーザーが表示していた場合、ユーザーが別のマシンからログインすると、エラー 3322 が発生する可能性が高くなります。 可能な場合、ディストリビューターは、ユーザーからこの情報を取得しようとする必要があります。 </p> <p>エラーが頻繁に発生する場合は、「 」にエスカレーションしてAdobeします。 Adobeに、ライセンスストアのリセットで問題が解決したかどうかを通知し、エラーが発生しているブラウザをAdobeに知らせる必要があります。 </p> <p>詳しくは、次の記事を参照してください。 
     <ul id="ul_C468409D1EA046178CA7F54DCDCB84EA"> 
      <li id="li_20C8CA3853574CE486F21E7A3667DAB9"><a href="https://forums.adobe.com/message/5520902" format="https" scope="external"> https://forums.adobe.com/message/5520902</a> </li> 
      <li id="li_6E6F1BD6FE7843449B3E2F06F342EFF7"><a href="https://forums.adobe.com/message/5535911" format="https" scope="external"> https://forums.adobe.com/message/5535911</a> </li> 
      <li id="li_2BE40E513A0C4BAD900C7B69FEF5D690"><a href="https://forums.adobe.com/message/5748618" format="https" scope="external"> https://forums.adobe.com/message/5748618</a> </li> 
      <li id="li_9C2BD122E3874E2893DD43E082A877E0"><a href="https://forums.adobe.com/message/6061165" format="https" scope="external"> https://forums.adobe.com/message/6061165</a> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3323 </td> 
   <td colname="col2"><span class="codeph"> AAXS_CorruptGlobalStateStore </span> </td> 
   <td colname="col3"> <p>DRM クライアントが使用するファイルが予期せず変更されました。 subErrorId には、クライアント固有のエラーまたは行エラーが含まれます。 </p> 
    <ul id="ul_96EA771046CA4B2B9FAE24D493F43FF2"> 
     <li id="li_D2693CD8EFEF46108828BA17E3F54FF6">ディストリビュータのソフトウェアは、3322 と同じ方法でユーザをリセットするように指示する必要があります。 </li> 
     <li id="li_0149B82436B64E28AC2B8C9B0EB09898">GlobalStore が、ユーザーベースのハードドライブの予想される障害率を超える速度で失敗する場合は、問題をAdobeにエスカレートします。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3324 </td> 
   <td colname="col2"><span class="codeph"> AAXS_MachineTokenInvalid </span> </td> 
   <td colname="col3"> このアプリケーションの DRM ローカルストレージをリセットします。 DRMManager.resetDRM を呼び出します。 <p>ライセンスサーバーが証明書失効リスト (CRL) サーバーに接続して CRL ファイルを更新できないか、クライアントコンピューターがライセンスサーバーによって失効したライセンス/認証を要求しています。 </p> <p>サーバログでは、エラーコード 111 は MachineTokenInvalid です。 しかし、クライアントレベルでは、エラーコード 111 は、エラーコード 3324 に変換されます。 </p> <p>DRM ライセンスサーバーの管理者は、お客様のライセンスサーバーがAdobeCRL ファイルを取得できたかどうかを確認する必要があります。 お客様が Tomcat を使用している場合、<span class="filepath"> tomcat/temp/</span> ディレクトリに 4 つの CRL ファイルが存在するかどうかを確認します。 </p> 
    <ul id="ul_23B7F1A104AF49E79EA87DB8E15E337E"> 
     <li id="li_855D87F251184FE688A8D5FA0F6C9EF5">ファイルがこのディレクトリにある場合は、Windows エクスプローラーでファイルをダブルクリックし、CRL ビューアアプリケーションで、期限切れのファイルがあるかどうかを確認します。 </li> 
     <li id="li_58EC4EDA2B5146188A0FF7B33C91E2FD">tomcat/temp/にファイルがない場合は、ファイアウォール/ルーティングの問題が原因で、このライセンスサーバーがAdobeCRL サーバーに到達できなかったと見なすことができます。 </li> 
    </ul> <p>詳しくは、 <a href="https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_secure_deployment_guidelines.pdf" format="http" scope="external"> ファイアウォール規則</a>. </p> <p>CRL ファイルが使用できない場合や、期限切れの場合は、ライセンスサーバーにアクセスできるかどうかを確認する必要があります。 お客様のライセンスサーバでネットワークスニファを開き、サーバを再起動し、クライアントがサーバからライセンスを要求しようとします。 ネットワークトラフィックを観察して、次の URL エンドポイントへの呼び出しが成功したかどうかを確認できます。 <p>ヒント：次の CRL の URL をブラウザーに入力して、各ファイルを手動でダウンロードできるかどうかを確認することもできます。 </p> 
     <ul id="ul_9B65C7ABBDEC4AC9BF3755FFD3587971"> 
      <li id="li_6867A9050E8D421C9138AC853D1784C9"><a href="https://crl2.adobe.com/Adobe/FlashAccessIndividualizationCA.crl" format="http" scope="external"> crl2.adobe.com/Adobe/FlashAccessIndividualizationCA.crl</a> </li> 
      <li id="li_6431689260554EAFAFDA2EC31798DCB5"><a href="https://crl2.adobe.com/Adobe/FlashAccessIntermediateCA.crl" format="http" scope="external"> crl2.adobe.com/Adobe/FlashAccessIntermediateCA.crl</a> </li> 
      <li id="li_2939674D0F854ADEB67E45FD216288A2"><a href="https://crl2.adobe.com/Adobe/FlashAccessRootCA.crl" format="http" scope="external"> crl2.adobe.com/Adobe/FlashAccessRootCA.crl</a> </li> 
      <li id="li_96386E00BE9D4CB99D100057A5F7C6DD">crl3.adobe.com/AdobeSystemsIncorporated FlashAccessRuntime/LatestCRL.crl</li> 
     </ul> </p> <p>ファイアウォール規則が開いていて、現在の 3324 エラーがない場合は、一時的なネットワークの問題が発生していた可能性があります。 お客様のサーバーログを確認します ( おそらく、 <span class="codeph"> /tomcat/logs/</span> ディレクトリに格納され、ライセンスサーバーが証明書失効リストを取得しようとしたときにエラーが発生したかどうかを判断します。 <p>重要：CRL ファイルを更新する際に、クライアントの大量のエラー（またはバースト）が 3324 エラーを一時的なネットワークの問題に報告した場合に、エラーが発生することがあります。 ネットワークの問題が解決されると、3324 の問題も解決されました。 </p> </p> <p>CRL ファイルの 4 つすべてが <span class="filepath"> tomcat/temp/</span> ディレクトリに保存され、クライアントは依然として 3324 エラーコードを取得しています。CRL ファイルへのファイルアクセスに関する問題が発生する可能性があります。 この問題を解決するには、ログを確認し、既存の CRL ファイルをパージします。 </p> <p>サーバーに問題がない場合は、3322 の説明に従って、でリセットするように求めます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>サーバーストアの破損エラー</b> </td> 
   <td colname="col2"> </td>
   <td colname="col3"> </td>
  </tr> 
  <tr> 
   <td colname="col1"> 3325 </td> 
   <td colname="col2"><span class="codeph"> AAXS_CorruptServerStateStore </span> </td> 
   <td colname="col3"> <p>DRM クライアントが使用するファイルが予期せず変更されました。 <span class="codeph"> subErrorId</span> クライアント固有のエラーまたはラインエラーが含まれます。 </p> 
    <ul id="ul_860D2402DA61460AB0D938F1116F6D64"> 
     <li id="li_CF368C43452B4265B62ADA3E223894BA">AdobeCP が内部で問題のあるサーバーストアを削除したので、ディストリビューターのソフトウェアは操作を再試行する必要があります。再試行は成功します。 再試行が失敗した場合は、問題を記録します。 </li> 
     <li id="li_51A5803A1F754970BB4EBD6494F5DC96">再試行がユーザーベースのハードドライブの予想される障害率を超える速度で失敗する場合は、問題をAdobeにエスカレートします。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3326 </td> 
   <td colname="col2"><span class="codeph"> AAXS_StoreTamperingDetected </span> </td> 
   <td colname="col3"> 呼び出し <span class="codeph"> DRMManager.resetDRM</span>. <p>ライセンスストアが改ざんまたは破損しているため、使用できなくなりました。 </p> <p>ディストリビュータのソフトウェアは、3322 で説明したように、ユーザにリセットを指示する必要があります。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3327 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ClockTamperingDetected </span> </td> 
   <td colname="col3"> 時計を修正するか、取得します <span class="codeph"> Authn/Lic/Domain</span> ライセンスを再度取得します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><b>認証/ライセンス/ドメインサーバーエラー</b> </td> 
   <td colname="col2"> </td>
   <td colname="col3"> </td>
  </tr> 
  <tr> 
   <td colname="col1"> 3328 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ServerErrorTryAgain </span> </td> 
   <td colname="col3"> <p>これは、サーバーがクライアントからのリクエストを完了できなかったサーバー側のエラーです。 このエラーは、例えば、サーバーがビジー状態、HTTP/500、サーバーが要求を復号化するために必要なキーを持っていない場合などに発生する可能性があります。 </p> <p>クライアントでは、何が問題を引き起こしたかを判断する方法はありません。 お客様は、通常、と呼ばれるAdobe・アクセス・サーバ・ログを確認する必要があります。 <span class="codeph"> AdobeFlashAccess.log</span>、何が起こったかを判断するために。 問題を示す記述的なスタックトレースがログに常に記録されます。 <span class="codeph"> subErrorId</span> には、サーバー固有のエラーまたは行エラーが含まれます。 </p> <p>ディストリビューターは、サーバーログを調べて、このエラーを送信しているサーバーを特定する必要があります。 3328 エラーにサブエラーコード 101 が含まれる場合、サーバーはリクエストを復号化できません。 お客様は、ライセンスサーバーにインストールされているライセンス/トランスポートサーバーの証明書が、パッケージ化時に使用される証明書と一致し、対応していることを検証する必要があります。 </p> <p>また、参照実装を使用している場合、 <span class="codeph"> flashaccess-refimpl.properties</span> プライマリ証明書と追加証明書を指定するファイル。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3329 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ApplicationSpecificError </span> </td> 
   <td colname="col3"> <p>アプリケーション固有のサブエラーコードは、Flash Accessでは不明です。 <span class="codeph"> subErrorId</span> パブリッシャーがカスタマイズしたライセンスサーバーからのサーバー固有のエラーが含まれます。 サーバーがアプリケーション固有の名前空間でエラーを返しました。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3330 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NeedAuthentication </span> </td> 
   <td colname="col3"> <p>このエラーは、ライセンスを取得する前にクライアントに認証を求めるようにコンテンツが設定されている場合に発生します。 </p> 
    <ul id="ul_712D29B8B5A6401FB014C4A283918E32"> 
     <li id="li_2D56905EB50D4FDEAD69CA8EAE38AD1A">ディストリビュータのソフトウェアは、ユーザを認証し、再度ライセンスを取得する必要があります。 <p>サービスが認証を使用する意図がない場合は、このエラーの原因となっているコンテンツの識別情報をログに記録します。 </p> </li> 
     <li id="li_B3BCF899B8BE41C7A4F7CF84B0503483">コンテンツが認証を必要とするように設定されていない場合を除き、このエラーではエスカレーションを必要としないでください。 <p>この場合、問題のあるコンテンツを適切なポリシーで再パッケージ化します。 コンテンツが正しくパッケージ化されている場合は、ポリシーの診断/ライセンスの不一致を参照してください。 </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <b>上記の説明に含まれないライセンス実施エラー</b> </td> 
   <td colname="col2"> </td>
   <td colname="col3"> </td>
  </tr> 
  <tr> 
   <td colname="col1"> 3331 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ContentNotYetValid </span> </td> 
   <td colname="col3"> <p>取得したライセンスはまだ有効ではありません。 この問題を解決するには、クライアントクロックが正しく設定されていないかどうかを確認します。 クライアントクロックを設定するには、コンテンツを再パッケージ化するか、ライセンスサーバの設定を変更します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3332 </td> 
   <td colname="col2"><span class="codeph"> AAXS_CachedLicenseExpired </span> </td> 
   <td colname="col3"> サーバーからライセンスを再取得します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3333 </td> 
   <td colname="col2"><span class="codeph"> AAXS_PlaybackWindowExpired </span> </td> 
   <td colname="col3"> <p>ポリシーの期限が切れるまで、ユーザーに対してコンテンツの再生ができないことを通知する必要があります。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3334 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InvalidDRMPlatform </span> </td> 
   <td colname="col3"> <p>例えば、コンテンツプロバイダーがAdobe上のAdobeアクセスを拒否するようにアクセスを設定しているか、共有ドメインバウンドライセンスが別のパーティション用の共有ドメイントークンにバインドされているため、このプラットフォームではコンテンツを再生できません。 </p> <p>適切な（CDM 機能ゲーテッド）パッケージャーの証明書を使用してコンテンツがパッケージ化されなかった場合、CDM はこのエラーをスローする可能性があります。 </p> <p>コンテンツが間違った PHDS/PHLS 証明書でパッケージ化されている場合、コンテンツは Chrome で機能しますが、他のブラウザーでは機能しない（またはその逆も同様）可能性があります。 <p>ヒント：これは、Chrome が異なる PHDS/PHLS 証明書を使用するからです。 </p>どの証明書が使用されているかを確認するには、コンテンツメタデータの詳細をダンプし、 <i>受信者の証明書</i>. 詳しくは、 <a href="https://adobeprimetime.zendesk.com/agent/tickets/2891" format="https" scope="external"> https://adobeprimetime.zendesk.com/agent/tickets/2891</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3335 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InvalidDRMVersion </span> </td> 
   <td colname="col3"> Android 向け TVSDK の最新バージョンにアップグレードします。 <p>この問題を解決するには、次のいずれかのタスクを実行します。 
     <ul id="ul_BF1742948BC9461CB8686DE70124D3CD"> 
      <li id="li_690D440C94CC45A0AE55EC319B1C4C23">AIRをアップグレード </li> 
      <li id="li_CDD20251C881466E88BE7BBB53D61EBC">Flash Playerの場合は、AdobeCP モジュールをアップグレードして、再生を再試行してください。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3336 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InvalidRuntimePlatform </span> </td> 
   <td colname="col3"> <p>例えば、コンテンツプロバイダーがプラットフォーム上の FP/AIRに対するコンテンツを拒否するように Access を設定しているので、このプラットフォームではコンテンツを再生できません。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3337 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InvalidRuntimeVersion </span> </td> 
   <td colname="col3"> Android 向け TVSDK の最新バージョンにアップグレードします。 <p>これは、コンテンツまたはサーバーが、FlashまたはAIRランタイムの特定のバージョンへの再生を拒否するように設定されている場合に発生します。 </p> 
    <ul id="ul_B0732D941256483CABBDD30C9BF43249"> 
     <li id="li_72782B1D638F48C0B87084689FB9C798">FlashをアップグレードできるオペレーティングシステムにFlashがある場合は、ディストリビュータのソフトウェアが、ユーザーに対してユーザーに対してのアップグレードを促し、再試行する必要があります。 それ以外の場合は、別のマシンを使用するようにユーザーに通知します。 </li> 
     <li id="li_1E3FD93CE39E43F2B7D961299B1211DA">エラー 3337s の疑いがある場合は、特定のコンテンツに対してエラーが発生しているかどうかを特定し、そのコンテンツを再パッケージ化します。 コンテンツが正しくパッケージ化されている場合は、ポリシーの診断/ライセンスの不一致を参照してください。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3338 </td> 
   <td colname="col2"><span class="codeph"> AAXS_UnknownConnectionType </span> </td> 
   <td colname="col3"> <p>接続の種類を検出できません。このポリシーでは、[ 出力保護 ] をオンにする必要があります。 この問題は、デジタルまたはアナログ出力の保護を必要とするようにコンテンツがパッケージ化されている場合にのみ発生します。 </p> <p>バージョン 11.8.800.168 より前のFlash Playerのバージョンでは、コンテンツ保護を示すポリシーが適用されているコンテンツで、エラー 3338 が発生することがありました <span class="codeph"> 使用可能な場合は使用</span>. この問題は、バージョン 11.8.800.168 以降で修正されました。 </p> 
    <ul id="ul_4B6CA26A53F84838B5B95400925464D4"> 
     <li id="li_CBD890F467E449EBB5116E1561252058">ディストリビュータのソフトウェアは、出力保護を必要としないコンテンツのバリアント（例えば、HD ストリームの SD バリアント）を選択します。 <p>エラー 3338 が <span class="codeph"> USE_IF_AVAILABLE </span> コンテンツ、プレーヤーのバージョン番号を確認します。 プレーヤーのバージョンが 11.8.800.168 未満の場合は、Flash Playerをアップグレードするようにユーザーに通知します。 11.8.800.168 を超えるバージョンでエラー 3338 が発生する場合は、どのコンテンツがエラーの原因となったかを記録します。 </p> </li> 
     <li id="li_62886C1D96264B129928A7E29E6C70E1">ディストリビューターは、このエラーの原因となっているコンテンツを確認し、コンテンツのポリシーが設定されていることを検証する必要があります <span class="codeph"> NO_PROTECTION</span> または <span class="codeph"> USE_IF_AVAILABLE</span> アナログ出力とデジタル出力用。 <p>コンテンツが誤って <span class="codeph"> NO_OUTPUT</span> または <span class="codeph"> 必須</span>、コンテンツを再パッケージ化します。 コンテンツが正しくパッケージ化されている場合は、ポリシーの診断/ライセンスの不一致を参照してください。 それ以外の場合は、Adobeにエスカレーションします。 </p> </li> 
    </ul> <p>詳しくは、 <a href="https://forums.adobe.com/message/5518688" format="https" scope="external"> DRM ポリシーが USE_IF_AVAILABLE に設定されている場合、予期しない 3338 エラーが発生しましたか？</a> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3339 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoAnalogPlaybackAllowed </span> </td> 
   <td colname="col3"> アナログデバイスで再生できません。 問題を解決するには、デジタルデバイスを接続します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3340 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoAnalogProtectionAvail </span> </td> 
   <td colname="col3"> 接続されたアナログ外部ディスプレイデバイス（モニタ/TV）に正しい機能がないため（例えば、デバイスに Macrovision や ACP がない）、コンテンツを再生できません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3341 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoDigitalPlaybackAllowed </span> </td> 
   <td colname="col3"> デジタルデバイスでコンテンツを再生できません。 <p>重要：この問題は、コンテンツ発行者はデジタル再生を許可しないでください。そのため、実稼動環境では発生しません。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3342 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoDigitalProtectionAvail </span> </td> 
   <td colname="col3"> 接続されているデジタル外部ディスプレイデバイス（モニタ/TV）に正しい機能がない。 例えば、デバイスに HDCP がないとします。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3343 </td> 
   <td colname="col2"><span class="codeph"> AAXS_IntegrityVerificationFailed </span> </td> 
   <td colname="col3"> <p>Android には適用されません。 </p> <p>このエラーは、現在、新しいバージョンのエラーがリリースされた後に最初に発生することが知られています。Flash これは、Flashが開いている間にFlashがアップグレードされ、ブラウザーが再起動するまでFlashの状態が悪くなるためです。 </p> 
    <ul id="ul_A0AC4A77550E40409A04BD33748EA987"> 
     <li id="li_F41C1ABD838D41ABB0DF65093E664A29">ディストリビュータのソフトウェアは、次のタスクを完了する必要があります。 
      <ul id="ul_79B2AB1372074D448F129851AA24F985"> 
       <li id="li_B93EDD263D78434FAF198A01938D3508">ユーザーは、すべてのブラウザーを閉じるか終了してから再度開くことをお勧めします。 </li> 
       <li id="li_ADFBCFA66AD849E18DB390455458528E">バージョンのFlashが最新かどうかを確認します。 <p>バージョンが最新でない場合は、アップグレードをお客様に通知し、ブラウザーのすべてのタブを閉じてから再度開きます。 </p> </li> 
      </ul> </li> 
     <li id="li_281B54582B5949AEA7D166246917EE41">ブラウザーの再起動が成功した後にエラーが発生したと思われる場合は、Adobeにエスカレーションします。 <p>新しいバージョンがリリースされた場合は、Adobeサポートに連絡して、バックグラウンド更新の問題が修正されたかどうかを確認することをお勧めします。 </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3344 </td> 
   <td colname="col2"><span class="codeph"> AAXS_MissingAdobeCPModule </span> </td> 
   <td colname="col3"> Android には適用されません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3345 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DRMNoAccessError </span> </td> 
   <td colname="col3"> <p>Android には適用されません。 </p> <p>このエラーは、Flashの一部またはAIRが正しくインストールされなかった場合に発生します。 </p> <p>ディストリビュータのソフトウェアは、次のいずれかを実行する必要があります。 
     <ul id="ul_D1188E2D4FDF4BD89A04F5629D75D981"> 
      <li id="li_B33FBCA5D4534D668B86A5E93DB3A809">ユーザーに、AIRのアンインストールと再インストールを依頼します。 </li> 
      <li id="li_B7D2388E9FA84C26AF1C87B48AF9EF16">Flash Playerの場合は、を呼び出します。 <span class="codeph"> System.update</span>. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3346 </td> 
   <td colname="col2"><span class="codeph"> AAXS_MigrationFailed </span> </td> 
   <td colname="col3"> 
    <ul id="ul_518AD4931CC64EB3A962DD451E6C5067"> 
     <li id="li_3C44F0740B08490E9C62D89C40B57DC2">ディストリビュータのソフトウェアは、次のいずれかを実行する必要があります。 
      <ul id="ul_7D90526684BF4EB2BBADCF598AA13086"> 
       <li id="li_D15B4BEDAF7340F6B9BC886DF6E346EC">AIRの場合は、にお電話ください <span class="codeph"> DRMManager.resetDRMVouchers()</span> </li> 
       <li id="li_40A51D35408249CFA28DBC49FDA3408B">エラー 3322 または 3346 エラーコードが原因でFlashが使用できない場合、ユーザーは次の場所に移動する必要があります。 <a href="https://forums.adobe.com/message/5535907#5535907" format="http" scope="external"> https://forums.adobe.com/message/5535907#5535907</a> およびAdobe記事の指示に従って、DRM ライセンスストアをプログラムでリセットします。 </li> 
      </ul> </li> 
     <li id="li_0464471E4A094C80BF2986694341921A">このエラーが頻繁に発生する場合、ディストリビューターは、頻度プレーヤーのバージョンとブラウザーのバージョンに関する詳細をAdobeに提供する必要があります。 </li> 
    </ul> <p>詳しくは、次のフォーラム記事を参照してください。 
     <ul id="ul_44E0077FEAA749CC9549BF3846065304"> 
      <li id="li_2BE3B2443380415DA73B7AA3B6547B31"><a href="https://forums.adobe.com/message/5520902" format="https" scope="external"> Chrome での DRM エラー3322/3346/3368（情報バーの問題）</a> </li> 
      <li id="li_4E5C7414756644E1AB78BE7B8112228C"><a href="https://forums.adobe.com/message/5535911" format="https" scope="external"> ハードウェア変更後の 3322 または 3346 エラー</a> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3347 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InsufficientDeviceCapabilities </span> </td> 
   <td colname="col3"> <p>このエラーの主な意味は、ライセンスには、クライアントの DRM 証明書が満たせないと示す制約が含まれていることです。 クライアントの DRM 証明書が発行される際に、次の「ハードウェア機能」が定義されます。 
     <ul id="ul_1EB6F1469C244CF0BA52C212495C053D"> 
      <li id="li_646043CE045C4DE2BBC939E1F4963DFE"><b>非ユーザーアクセスバス</b>. If <b>true</b>では、復号化されたメディアは、バスや、アプリケーションがアクセスできるメインメモリには送られません。 <p>If <b>false</b>の場合、復号化後にコンテンツにアクセスできる可能性があります。 </p> </li> 
      <li id="li_02AAECAF4D35447BA10554541B46DE67"><b>信頼のハードウェアルート</b>. If <b>true</b>：デバイス上で起動時に読み込まれるすべてのソフトウェアが、ハードウェアでのみ使用可能なキーまたはダイジェストに対して検証されました。 <p>クライアントの DRM 証明書に対してライセンスが開かれ、失敗が直ちに発生すると、これらの両方の制約がクライアント側でチェックされます。 これらの制約は、ライセンスを発行する前に、サーバー側で確認することもできます。 </p> </li> 
     </ul> </p> <p>このエラーの二次的な意味は、ライセンスに「Jailbreak Enforcement」ポリシーが設定され、デバイスで jailbreak が検出されたことです。 このチェックは、クライアント側で定期的に行われ、サーバー側ではチェックできません。 </p> <p>ディストリビューターは、ポリシーを更新し、制限を解除できます。 デバイス機能ポリシーの場合は、 <span class="codeph"> -devCapabilitiesV1</span> フラグを設定し、引数を設定しない。 jailbreak 強制の場合、 <span class="codeph"> policy.enforceJailbreak=false</span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3348 </td> 
   <td colname="col2"><span class="codeph"> AAXS_HardStopIntervalExpired </span> </td> 
   <td colname="col3"> ハードストップ間隔が期限切れです。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3349 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ServerVersionTooHigh </span> </td> 
   <td colname="col3"> サーバーは、クライアントでサポートされている最も高いバージョンよりも高いバージョンで実行されています。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3350 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ServerVersionTooLow </span> </td> 
   <td colname="col3"> サーバーは、クライアントがサポートする最小バージョンよりも低いバージョンで実行されています。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3351 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DomainTokenInvalid </span> </td> 
   <td colname="col3"> ドメイントークンが無効でした。 この問題を解決するには、ドメインに再度登録してください。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3352 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DomainTokenTooOld </span> </td> 
   <td colname="col3"> ドメイントークンが、ライセンスで必要なトークンより古いものです。 この問題を解決するには、ドメインに再度登録します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3353 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DomainTokenTooNew </span> </td> 
   <td colname="col3"> ドメイントークンが、ライセンスで必要なトークンより新しいです。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3354 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DomainTokenExpired </span> </td> 
   <td colname="col3"> ドメイントークンが期限切れです。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3355 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DomainJoinFailed </span> </td> 
   <td colname="col3"> ドメインの参加に失敗しました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3356 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoCorrespondingRoot </span> </td> 
   <td colname="col3"> V3 リーフライセンスのルートライセンスが見つかりませんでした。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3357 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoValidEmbeddedLicense </span> </td> 
   <td colname="col3"> 有効な埋め込みライセンスが見つかりませんでした。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3358 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoACPProtectionAvail </span> </td> 
   <td colname="col3"> 接続されたアナログデバイスに ACP 保護がないため、再生できません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3359 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoCGMSAProtectionAvail </span> </td> 
   <td colname="col3"> 接続されたアナログデバイスに CGMS-A 保護がないため、再生できません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3360 </td> 
   <td colname="col2"><span class="codeph"> AAXS_DomainRegistrationRequired </span> </td> 
   <td colname="col3"> コンテンツにはドメイン登録が必要です。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3361 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NotRegisteredToDomain </span> </td> 
   <td colname="col3"> 指定されたメタデータのドメインにコンピューターが登録されていません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3362 </td> 
   <td colname="col2"><span class="codeph"> AAXS_OperationTimeoutError </span> </td> 
   <td colname="col3"> 非同期操作に時間がかかりました <span class="codeph"> maxOperationTimeout</span>. iOS DRMNative Framework からのみ返されます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3363 </td> 
   <td colname="col2"><span class="codeph"> AAXS_UnsupportedIOSPlaylistError </span> </td> 
   <td colname="col3"> 渡された M3U8 プレイリストは、コンテンツをサポートしていませんでした。 iOS DRMNative Framework からのみ返されます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3364 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoDeviceId </span> </td> 
   <td colname="col3"> <p>フレームワークがデバイス ID をリクエストしましたが、返された値は空でした。 </p> <p>ユーザーは <span class="uicontrol"> 保護されたコンテンツの識別子を許可</span> Chrome 設定の「 」チェックボックスをオンにします。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3365 </td> 
   <td colname="col2"><span class="codeph"> AAXS_IncognitoModeNotAllowed </span> </td> 
   <td colname="col3"> <p>このブラウザーとプラットフォームの組み合わせでは、匿名モードでの DRM 保護された再生は許可されません。 </p> <p>ディストリビュータのソフトウェアは、ユーザに匿名モードを終了するか、別のブラウザを使用するように通知する必要があります。 詳しくは、 <a href="https://forums.adobe.com/thread/1266622" format="https" scope="external"> DRM エラー 3365 の原因と解決</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3366 </td> 
   <td colname="col2"><span class="codeph"> AAXS_BadParameter </span> </td> 
   <td colname="col3"> <p>ホストランタイムは、無効なパラメーターを持つアクセスライブラリを呼び出しました。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3367 </td> 
   <td colname="col2"><span class="codeph"> AAXS_BadSignature </span> </td> 
   <td colname="col3"> m3u8 マニフェストの署名に失敗しました。 iOS DRMNative Framework または AVE からのみ返されます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3368 </td> 
   <td colname="col2"><span class="codeph"> AAXS_UserSettingsNoAccess</span> </td> 
   <td colname="col3"> <p>ユーザーが操作をキャンセルしたか、システムへのアクセスを許可しない設定を入力しました。 </p> <p>このエラーは、SWFのバージョンが 19 以降の場合にのみ発生します。 後方互換性を保つために、バージョンが 18 以前の場合、3321SWFがスローされます。 </p> <p>配布者のソフトウェアは、ユーザーに対し、サンドボックス化されていないプラグインアクセスを許可する方法の説明を提供する必要があります。 Google Chrome のサンドボックス解除のアクセスが拒否されました</a> および <a href="https://forums.adobe.com/message/5520902" format="https" scope="external"> Chrome での DRM エラー3322/3346/3368（情報バーの問題）</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3369 </td> 
   <td colname="col2"><span class="codeph"> AAXS_InterfaceNotAvailable</span> </td> 
   <td colname="col3"> <p>必要なブラウザーインターフェイスを使用できません。 この問題は Pepper でのみ発生します。 ブラウザープラグインとブラウザーバージョンのFlashが一致しない可能性があります。 </p> <p>配布者のソフトウェアは、ユーザーに対し、最新バージョンのブラウザがインストールされていることを確認するよう指示する必要があります。 </p> <p> このエラーの発生が増加し、リリースされるブラウザーの更新に対応している場合は、Adobeにエスカレートします。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3370 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ContentIdSettingsNoAccess</span> </td> 
   <td colname="col3"> <p>ユーザーが <span class="uicontrol"> 保護されたコンテンツの識別子を許可</span> 設定。 </p> <p>ヒント：このエラーは、Pepper バージョン 13.0.0.x 以降で発生しました。 </p> <p>配布者のソフトウェアは、ユーザーに対して <span class="uicontrol"> 保護されたコンテンツの識別子を許可</span> 設定。 </p> <p>ディストリビューターのオペレーションチームは、ユーザーに対し、 <span class="uicontrol"> 保護されたコンテンツの識別子を許可</span> 設定。 </p> <p>詳しくは、 <a href="https://forums.adobe.com/message/6518323#6518323" format="https" scope="external"> https://forums.adobe.com/message/6518323#6518323</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3371 </td> 
   <td colname="col2"><span class="codeph"> AAXS_NoOPConstraintInPixel</span><span class="codeph"> 制約</span> </td> 
   <td colname="col3"> <p>ライセンスの出力保護制約に基づく解決の形式が正しくありません。 </p> <p>ディストリビュータのソフトウェアは、エラーメッセージを表示する必要があります。 ユーザーに、問題をコンテンツのタイトルでディストリビューターに報告するように依頼します。 </p> <p>ディストリビューターは、コンテンツを有効なポリシーで再パッケージ化する必要があります。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3372 </td> 
   <td colname="col2"><span class="codeph"> AAXS_ResolutionLargerThanMaxResolution</span> </td> 
   <td colname="col3"> <p>コンテンツの解像度が、出力保護制約で指定された最大解像度を超えています。 </p> <p>配布者の運用チームがログでこのエラーを確認した場合は、解決に基づく出力保護ポリシーを確認し、必要に応じてコンテンツを再パッケージ化する必要があります。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3373 </td> 
   <td colname="col2"><span class="codeph"> AAXS_MinorErr_DisplayResolutionLargerThanConstrain</span> </td> 
   <td colname="col3"> <p>コンテンツの解像度が、現在アクティブな出力保護制約で指定された解像度よりも大きくなっています。 </p> <p>配布者の運用チームがログでこのエラーを確認した場合は、解決に基づく出力保護ポリシーを確認し、必要に応じてコンテンツを再パッケージ化する必要があります。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3374 </td> 
   <td colname="col2"><span class="codeph"> AAXS_MinorErr_ClientCommProcessFailed</span> </td> 
   <td colname="col3"> <p>クライアント側の通信処理中に失敗しました。例えば、リクエストの生成、応答の処理、認証トークンが正しくありません。 </p> <p>配布者の運用チームがログにこのエラーが表示された場合は、解決に基づく出力保護ポリシーを確認し、必要に応じてコンテンツを再パッケージ化する必要があります。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## NATIVE_ERROR:ビデオ再生値 {#section_7079501250C2487499639F92EC774525}

AVE の Video Encoder インターフェイスは、 `NATIVE_ERROR` メタデータオブジェクト。

<table id="table_5EEB1F60E5854452A8B0BABBE9B32651"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> NATIVE_ERROR_CODE メタデータキーの値 </th> 
   <th colname="col2" class="entry"> NATIVE_ERROR_NAME メタデータキーの値 </th> 
   <th colname="col3" class="entry"> 説明 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> -1 </td> 
   <td colname="col2"><span class="codeph"> END_OF_PERIOD</span> </td> 
   <td colname="col3"> 期間の終わり。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 0 </td> 
   <td colname="col2"><span class="codeph"> 成功</span> </td> 
   <td colname="col3"> 操作に成功しました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 1 </td> 
   <td colname="col2"> <span class="codeph"> ASYNC_OPERATION_IN_PROGRESS</span> </td> 
   <td colname="col3"> 非同期操作。 操作リクエストが実行されました。 成功/失敗に関する情報は、後で入手できます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 2 </td> 
   <td colname="col2"><span class="codeph"> EOF</span> </td> 
   <td colname="col3"> ファイルの終了 (EOF) 条件が原因で、操作ができません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3 </td> 
   <td colname="col2"><span class="codeph"> DECODER_FAILED</span> </td> 
   <td colname="col3"> 実行時にデコーダーが失敗しました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 4 </td> 
   <td colname="col2"><span class="codeph"> DEVICE_OPEN_ERROR</span> </td> 
   <td colname="col3"> ハードウェアデコーダーを開けませんでした。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 5 </td> 
   <td colname="col2"><span class="codeph"> FILE_NOT_FOUND </span> </td> 
   <td colname="col3"> リソースが見つかりません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 6 </td> 
   <td colname="col2"><span class="codeph"> GENERIC_ERROR </span> </td> 
   <td colname="col3"> 一般的なエラー。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 7 </td> 
   <td colname="col2"><span class="codeph"> IRRECOVERABLE_ERROR </span> </td> 
   <td colname="col3"> ビデオエンジンが復元できないエラー状態。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 8 </td> 
   <td colname="col2"><span class="codeph"> LOST_CONNECTION_RECOVERABLE </span> </td> 
   <td colname="col3"> ネットワークエラー。復元を試みています。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 9 </td> 
   <td colname="col2"><span class="codeph"> NO_FIXED_SIZE </span> </td> 
   <td colname="col3"> リソースのサイズを決定できません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 10 </td> 
   <td colname="col2"><span class="codeph"> NOT_IMPLEMENTED </span> </td> 
   <td colname="col3"> 機能が実装されていません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 11 </td> 
   <td colname="col2"><span class="codeph"> OUT_OF_MEMORY </span> </td> 
   <td colname="col3"> メモリ不足です。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 12 </td> 
   <td colname="col2"><span class="codeph"> PARSE_ERROR </span> </td> 
   <td colname="col3"> メディアファイルの解析中にエラーが発生しました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 13 </td> 
   <td colname="col2"><span class="codeph"> SIZE_UNKNOWN </span> </td> 
   <td colname="col3"> リソースのサイズが不明です。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 14 </td> 
   <td colname="col2"><span class="codeph"> UNDER_FLOW </span> </td> 
   <td colname="col3"> アンダーフロー条件。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 15 </td> 
   <td colname="col2"><span class="codeph"> UNSUPPORTED_CONFIG </span> </td> 
   <td colname="col3"> 設定はサポートされていません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 16 </td> 
   <td colname="col2"><span class="codeph"> UNSUPPORTED_OPERATION </span> </td> 
   <td colname="col3"> 操作はサポートされていません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 17 </td> 
   <td colname="col2"><span class="codeph"> WAITING_FOR_INIT </span> </td> 
   <td colname="col3"> まだ初期化されていません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 18 </td> 
   <td colname="col2"><span class="codeph"> INVALID_PARAMETER </span> </td> 
   <td colname="col3"> 無効なパラメーターです。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 19 </td> 
   <td colname="col2"><span class="codeph"> INVALID_OPERATION</span> </td> 
   <td colname="col3"> 操作が許可されていません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 20 </td> 
   <td colname="col2"><span class="codeph"> OP_ONLY_ALLOWED_IN_PAUSED_STATE</span> </td> 
   <td colname="col3"> この操作は、一時停止中にのみ許可されます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 21 </td> 
   <td colname="col2"><span class="codeph"> OP_INVALID_WITH_AUDIO_ONLY_FILE</span> </td> 
   <td colname="col3"> オーディオ専用ファイルでは操作を使用できません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 22 </td> 
   <td colname="col2"><span class="codeph"> PREVIOUS_STEP_SEEK_IN_PROGRESS</span> </td> 
   <td colname="col3"> 前のシーク操作は、まだ進行中です。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 23 </td> 
   <td colname="col2"><span class="codeph"> SOURCE_NOT_SPECIFIED </span> </td> 
   <td colname="col3"> リソースが指定されていません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 24 </td> 
   <td colname="col2"><span class="codeph"> RANGE_ERROR</span> </td> 
   <td colname="col3"> 指定された値は範囲外です。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 25 </td> 
   <td colname="col2"><span class="codeph"> INVALID_SEEK_TIME</span> </td> 
   <td colname="col3"> シーク時間が無効です。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 26 </td> 
   <td colname="col2"><span class="codeph"> FILE_STRUCTURE_INVALID</span> </td> 
   <td colname="col3"> 指定されたファイルは、想定される構文に従っていません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 27 </td> 
   <td colname="col2"><span class="codeph"> COMPONENT_CREATION_FAILURE</span> </td> 
   <td colname="col3"> 必須コンポーネントを作成できませんでした。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 28 </td> 
   <td colname="col2"><span class="codeph"> DRM_INIT_ERROR</span> </td> 
   <td colname="col3"> DRM コンテキストを作成できませんでした。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 29 </td> 
   <td colname="col2"><span class="codeph"> CONTAINER_NOT_SUPPORTED </span> </td> 
   <td colname="col3"> コンテナタイプはサポートされていません。 </td> 
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
   <td colname="col3"> ネットワークが使用できません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 33 </td> 
   <td colname="col2"><span class="codeph"> NETWORK_ERROR</span> </td> 
   <td colname="col3"> ネットワークからデータを取得中にエラーが発生しました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 34 </td> 
   <td colname="col2"><span class="codeph"> OVERFLOW</span> </td> 
   <td colname="col3"> オーバーフロー。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 35 </td> 
   <td colname="col2"><span class="codeph"> VIDEO_PROFILE_NOT_SUPPORTED</span> </td> 
   <td colname="col3"> サポートされていないビデオプロファイル。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 36 </td> 
   <td colname="col2"><span class="codeph"> PERIOD_NOT_LOADED</span> </td> 
   <td colname="col3"> HOLD 期間またはまだ読み込まれていない期間に対して操作が試行されました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 37 </td> 
   <td colname="col2"><span class="codeph"> INVALID_REPLACE_DURATION</span> </td> 
   <td colname="col3"> 指定した置き換え期間が無効か、ストリームの終わりを超えています。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 38 </td> 
   <td colname="col2"><span class="codeph"> CALLED_FROM_WRONG_THREAD</span> </td> 
   <td colname="col3"> 間違ったスレッドから API を呼び出すことはできません。 主に、API 要素はメインスレッドからのみ呼び出す必要があります。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 39 </td> 
   <td colname="col2"><span class="codeph"> FRAGMENT_READ_ERROR</span> </td> 
   <td colname="col3"> フラグメント読み取りエラー。 フェールオーバーが存在しません。 エンジンは次のフラグメントを読み取ろうとします。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 40 </td> 
   <td colname="col2"><span class="codeph"> 中止</span> </td> 
   <td colname="col3"> 操作は、明示的な Abort または Destroy の呼び出しによって中止されました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 41 </td> 
   <td colname="col2"><span class="codeph"> UNSUPPORTED_HLS_VERSION</span> </td> 
   <td colname="col3"> このバージョンの HLS メディアを再生できません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 42 </td> 
   <td colname="col2"><span class="codeph"> CANNOT_FAIL_OVER</span> </td> 
   <td colname="col3"> フェイルオーバーできません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 43 </td> 
   <td colname="col2"><span class="codeph"> HTTP_TIME_OUT</span> </td> 
   <td colname="col3"> HTTP ダウンロードがタイムアウトしました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 44 </td> 
   <td colname="col2"><span class="codeph"> NETWORK_DOWN </span> </td> 
   <td colname="col3"> ユーザーのネットワーク接続がダウンしています。 再生はいつでも停止する可能性があり、接続が可能になると再開します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 45 </td> 
   <td colname="col2"><span class="codeph"> NO_USABLE_BITRATE_PROFILE</span> </td> 
   <td colname="col3"> 使用可能なビットレートプロファイルがストリームに見つかりません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 46 </td> 
   <td colname="col2"><span class="codeph"> BAD_MANIFEST_SIGNATURE</span> </td> 
   <td colname="col3"> マニフェストに無効な署名があります。 マニフェストの署名テストに失敗しました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 47 </td> 
   <td colname="col2"><span class="codeph"> CANNOT_LOAD_PLAYLIST</span> </td> 
   <td colname="col3"> プレイリストを読み込めません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 48 </td> 
   <td colname="col2"><span class="codeph"> REPLACEMENT_FAILED</span> </td> 
   <td colname="col3"> 挿入 API で指定された置換は成功しませんでした。 これは、挿入が成功したが置き換えが成功しなかったことを意味します。 置き換えるマニフェストがタイムラインから削除されている場合、置き換えに失敗する可能性があります。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 49 </td> 
   <td colname="col2"><span class="codeph"> SWITCH_TO_ASYMMETRIC_PROFILE</span> </td> 
   <td colname="col3"> DRM が非対称プロファイルに切り替え中です。 すべてのプロファイルは、期間内に整列する必要があります。 そうでない場合は、この警告がスローされ、再生にジャンプが発生する可能性があります。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 50 </td> 
   <td colname="col2"><span class="codeph"> LIVE_WINDOW_MOVED_BACKWARD</span> </td> 
   <td colname="col3"> ライブウィンドウは前に進むことのみが想定されています。 そうでない場合は、この警告がスローされ、ウィンドウは読み取られません。 そのため、再生にジャンプ（または停止/長い一時停止）が発生する場合があります。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 51 </td> 
   <td colname="col2"><span class="codeph"> CURRENT_PERIOD_EXPIRED</span> </td> 
   <td colname="col3"> ライブウィンドウが現在の期間を超えました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 52 </td> 
   <td colname="col2"><span class="codeph"> CONTENT_LENGTH_MISMATCH</span> </td> 
   <td colname="col3"> HTTP サーバーから報告された content-length が、実際のメディアサイズと一致しませんでした。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 53 </td> 
   <td colname="col2"><span class="codeph"> PERIOD_HOLD</span> </td> 
   <td colname="col3"> setHoldAt API が設定した時間に達したので、メディアリーダーはこれ以上読み取れません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 54 </td> 
   <td colname="col2"><span class="codeph"> LIVE_HOLD </span> </td> 
   <td colname="col3">ライブウィンドウの終わりに達したので、メディアリーダーはセグメントを読み込めません。 サーバーがライブウィンドウに新しいメディアを追加すると、セグメントの読み込みが再開されます。 通常、この状態になるのは次の場合です。 
    <ul id="ul_FCFF658EDA4144E59970B317D6DEB624"> 
     <li id="li_2F6EEEB782D54CD999BC7CC7C0B78B48">この <span class="codeph"> bufferTime</span> が長すぎます（ライブウィンドウの期間以上）。 </li> 
     <li id="li_25CE97115ED64E44AA89977FB5F0DCF7">1 つ以上の挿入/消去 API の組み合わせにより、追加されたメディアより多くのメディアが置き換えられました。 </li> 
     <li id="li_1B14716B2157492AB1859306D1250523">次の期間は、（InsertBy API 呼び出しによる）保留中のメディア置き換えを含むライブ期間です </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 55 </td> 
   <td colname="col2"><span class="codeph"> BAD_MEDIA_INTERLEAVING </span> </td> 
   <td colname="col3"> メディアのオーディオおよびビデオのインターリービングが正しく行われません。 これはパッケージ化エラーです。 この警告は、差が 2 秒を超えるとディスパッチされます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 56 </td> 
   <td colname="col2"><span class="codeph"> DRM_NOT_AVAILABLE</span> </td> 
   <td colname="col3"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 57 </td> 
   <td colname="col2"><span class="codeph"> PLAYBACK_NOT_AUTHORIZED</span> </td> 
   <td colname="col3"> Flash Playerで HLS 再生が有効になっていません。 AuthorizedFeatures.enableHLSPlayback を参照してください。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 58 </td> 
   <td colname="col2"><span class="codeph"> BAD_MEDIA_SAMPLE_FOUND</span> </td> 
   <td colname="col3"> デコーダーは、デコードできない不正なサンプルを受信しました。 これは通常、致命的なエラーではありませんが、オーディオ/ビデオに問題が発生している可能性があることを示しています。 このエラーのインスタンスが多すぎる場合は、エンコーディングが正しくないか、ファイルが正しくありません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 59 </td> 
   <td colname="col2"><span class="codeph"> RANGE_SPANS_READ_RANGEHEAD</span> </td> 
   <td colname="col3"> 再生が開始した後、挿入/置換範囲に読み取りヘッドが含まれていない必要があります。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 60 </td> 
   <td colname="col2"><span class="codeph"> POSTROLL_WITH_LIVE_NOT_ALLOWED</span> </td> 
   <td colname="col3"> ポストロール挿入は、ライブメディアでは使用できません。 ただし、サーバーがメディアを完了とマークした後で使用できます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 61 </td> 
   <td colname="col2"><span class="codeph"> INTERNAL_ERROR</span> </td> 
   <td colname="col3"> 発生しないべきでない非常にまれな問題です。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 62 </td> 
   <td colname="col2"><span class="codeph"> SPS_PPS_FOUND_OUTSIDE_AVCC</span> </td> 
   <td colname="col3"> ストリームは、H264 SPS/PPS を常に AVCC に配置するというパッケージ化の推奨に従っていません。 シーク/再生の問題が発生する可能性があります。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 63 </td> 
   <td colname="col2"><span class="codeph"> PARTIAL_REPLACEMENT</span> </td> 
   <td colname="col3"> Insert API で指定された置換は部分的にのみ行われました。 この処理は、 replaceDuration がタイムライン期間にわたってまたがる場合に発生します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 64 </td> 
   <td colname="col2"><span class="codeph"> RENDITION_M3U8_ERROR</span> </td> 
   <td colname="col3"> レンディションプレイリストの読み込み中にエラーが発生しました。 これは AVE に対してのみ使用され、FlashPlayer に対しては使用されません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 65 </td> 
   <td colname="col2"><span class="codeph"> NULL_OPERATION</span> </td> 
   <td colname="col3"> 操作で何も実行されません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 66 </td> 
   <td colname="col2"><span class="codeph"> SEGMENT_SKIPPED_ON_FAILURE</span> </td> 
   <td colname="col3"> セグメントは再生できず、失敗した場合はスキップされます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 67 </td> 
   <td colname="col2"><span class="codeph"> INCOMPATIBLE_RENDER_MODE</span> </td> 
   <td colname="col3"> 非互換のレンダリングモードです。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 68 </td> 
   <td colname="col2"><span class="codeph"> PROTOCOL_NOT_SUPPORTED </span> </td> 
   <td colname="col3"> この URL で使用される Web プロトコルはサポートされていません。 </td> 
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
   <td colname="col3"> タイムラインで分割操作を実行できません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 72 </td> 
   <td colname="col2"><span class="codeph"> CANNOT_ERASE_TIMELINE</span> </td> 
   <td colname="col3"> タイムラインで消去操作を実行できません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 73 </td> 
   <td colname="col2"><span class="codeph"> DID_NOT_GET_NEXT_FRAGMENT</span> </td> 
   <td colname="col3"> 次のフラグメントを取得しませんでした。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 74 </td> 
   <td colname="col2"><span class="codeph"> NO_TIMELINE</span> </td> 
   <td colname="col3"> 内部データ構造にタイムラインが存在しません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 75 </td> 
   <td colname="col2"><span class="codeph"> LISTENER_NOT_FOUND</span> </td> 
   <td colname="col3"> 内部データ構造にリスナーが見つかりません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 76 </td> 
   <td colname="col2"><span class="codeph"> AUDIO_START_ERROR</span> </td> 
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
   <td colname="col3"> ID3 データの解析中にエラーが発生しました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 82 </td> 
   <td colname="col2"><span class="codeph"> SECURITY_ERROR </span> </td> 
   <td colname="col3"> セキュリティ上の制限により、コンテンツの読み込みに失敗しました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 83 </td> 
   <td colname="col2"><span class="codeph"> TIMELINE_TOO_SHORT</span> </td> 
   <td colname="col3"> タイムラインの期間が短すぎます。 ライブストリームの場合は、バッファリングが頻繁に発生する可能性があります。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 84 </td> 
   <td colname="col2"><span class="codeph"> AUDIO_ONLY_STREAM_START</span> </td> 
   <td colname="col3"> ストリームがオーディオ専用ストリームに切り替えられました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 85 </td> 
   <td colname="col2"><span class="codeph"> AUDIO_ONLY_STREAM_END</span> </td> 
   <td colname="col3"> ストリームがオーディオのみからビデオ付きストリームに切り替えられました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 87 </td> 
   <td colname="col2"><span class="codeph"> KEY_NOT_FOUND </span> </td> 
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
   <td colname="col3"> メインのマニフェストの更新を処理できません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 91 </td> 
   <td colname="col2"> <span class="codeph"> UNREPORTED_TIME_DISCONTINUITY_FOUND</span> </td> 
   <td colname="col3"> 報告されていない時間 (PTS) 不連続が見つかりました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 92 </td> 
   <td colname="col2"> <span class="codeph"> UNMATCHED_AV_DISCONTINUITY_FOUND</span> </td> 
   <td colname="col3"> Unmatched Audio and Video 不連続が見つかりました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 93 </td> 
   <td colname="col2"><span class="codeph"> TRICKPLAY_ENDED_DUE_TO_ERROR</span> </td> 
   <td colname="col3">でメディアを再生中にエラーが発生しました <i>トリックプレイ</i> モード。 トリック再生モードが終了し、ストリームが一時停止します。 呼び出し <span class="codeph"> Play()</span> 通常モードでメディアを再生する場合。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 95 </td> 
   <td colname="col2"><span class="codeph"> LIVE_WINDOW_MOVED_AHEAD</span> </td> 
   <td colname="col3"> プレーヤーはライブウィンドウから出ているので、追いつくには早送りする必要があります。 </td> 
  </tr> 
 </tbody> 
</table>

## NATIVE_ERROR:暗号値 {#section_39365E545CAC49B9A4D4678657BB2155}

Adobeビデオエンジンの暗号モジュールは、 `NATIVE_ERROR` メタデータオブジェクト。

| NATIVE_ERROR_CODE メタデータキーの値 | NATIVE_ERROR_NAME メタデータキーの値 | 意味 |
|---|---|---|
| 300 | `CRYPTO_ALGORITHM_NOT_SUPPORTED` | 使用中のアルゴリズムはサポートされていません。 |
| 301 | `CRYPTO_ERROR_CORRUPTED_DATA` | データが破損しています。 |
| 302 | `CRYPTO_ERROR_BUFFER_TOO_SMALL` | バッファが小さすぎます。 |
| 303 | `CRYPTO_ERROR_BAD_CERTIFICATE` | 証明書が正しくありません。 |
| 304 | `CRYPTO_ERROR_DIGEST_UPDATE` | ダイジェストの更新。 |
| 305 | `CRYPTO_ERROR_DIGEST_FINISH` | ダイジェストが完了しました。 |
| 306 | `CRYPTO_ERROR_BAD_PARAMETER` | 無効なパラメータです。 |
