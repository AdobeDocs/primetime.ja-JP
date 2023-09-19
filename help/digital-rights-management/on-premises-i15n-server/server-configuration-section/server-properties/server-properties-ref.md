---
title: サーバーのプロパティのリファレンス
description: サーバーのプロパティのリファレンス
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '870'
ht-degree: 0%

---

# サーバーのプロパティのリファレンス{#server-properties-reference}

<!--<a id="section_EC8810492A454BDBA6013FE376360F4E"></a>-->

## 個別化サーバー

<table id="table_ats_tk2_jr">  
 <thead> 
  <tr> 
   <th class="entry"> 設定 </th> 
   <th class="entry"> 説明 </th> 
   <th class="entry"> 例 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td> Transport Credential </td> 
   <td>トランスポート秘密鍵証明書は、クライアントから受信した要求を復号化し、送り返された応答に署名するために使用されます。 必ず <span class="filepath"> AdobeInitial.properties</span> ファイルは、暗号化された PKCS12 パスワードと、トランスポート秘密鍵証明書ファイルへのパスの両方を使用して適切に指定します。 </td> 
   <td> 
    <ul id="ul_itx_fl2_jr"> 
     <li id="li_A2E65253F37245268A41E6B9C958C8DF"><span class="codeph"> cert.i15n.transport.file = </span> [ 個別化トランスポートの証明書とキーを含む PKCS12 ファイル ] </li> 
     <li id="li_28CDFC0B3D684795AF4708B6D26DF83F"><span class="codeph"> cert.i15n.transport.password =</span> [PKCS12 ファイルの暗号化パスワード ] </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> 個別化 CA 資格情報 </td> 
   <td>個別化サーバーは、個別化 CA の資格情報を使用して、発行するコンピューター証明書に署名します。 必ず <span class="filepath"> AdobeInitial.properties</span> I15N CA 秘密鍵証明書ファイルへのパスと、暗号化された PKCS12 パスワードの両方を使用して、ファイルを適切に保存します。 </td> 
   <td> 
    <ul id="ul_xsj_nl2_jr"> 
     <li id="li_5A770D8A482F41A4A9AB63CA52C2EB90"><span class="codeph"> cert.i15n.ica.file =</span> [ 個別化 CA の証明書とキーを含む PKCS12 ファイル ] </li> 
     <li id="li_C3C4A2D9AA2A4F86B6DDCFFD9CB55CBB"><span class="codeph"> cert.i15n.ica.password =</span> [PKCS12 ファイルの暗号化パスワード ] </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> 個別化暗号化秘密鍵証明書 </td> 
   <td> 個別化サーバーは暗号化秘密鍵証明書を使用して、個別化サーバーに送信する必要のある機密ファイルを暗号化します。 例えば、この証明書は、ライセンスの移行をサポートし、個別化サーバーの DRM 秘密鍵の暗号化にも使用されます。 </td> 
   <td> 
    <ul id="ul_nbr_kpd_w5"> 
     <li id="li_4226AD6CC85740669DAF467EFD00BBBE"><span class="codeph"> cert.i15n.decryption.file=i15n_transport.pfx</span> </li> 
     <li id="li_F51BDD94F4724FA58CEF9470B6FEE33B"><span class="codeph"> cert.i15n.decryption.password=password</span> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> コンテンツキャッシュ </td> 
   <td>これらの設定は、個別化サーバーがコンテンツをダウンロードする場所と、コンテンツをディスク上のキャッシュする場所を制御します。 個別化サーバーは、起動時に 1 回、次にこれらのプロパティで指定された頻度と時間に、コンテンツサーバーで新しいコンテンツをチェックします。 <p>オンプレミスの個別化サーバーの場合、コンテンツキャッシュデータの初期セットが含まれています。 必ず <i>内容</i> （キャッシュフォルダー自体ではなく）キャッシュフォルダーの、設定済みの <span class="filepath"> AdobeInitial.properties</span> <span class="codeph"> contentServer.localDirectory</span> 場所。 </p> </td> 
   <td> 
    <ul id="ul_r4n_1r2_jr"> 
     <li id="li_CA5F562577B04B4A9966EF46E039A137"><span class="codeph"> contentServer.localDirectory =</span> [ ローカルコンテンツを格納するディレクトリ（通常は tomcat/temp）] </li> 
     <li id="li_9A78FBD6C54D47708226378340B46E8E"><span class="codeph"> contentServer.server =</span> [ECI 情報 (<i>このリリースではサポートされていません</i>)] </li> 
     <li id="li_4E7D7F76085D411688B5003E855F860B"><span class="codeph"> contentServer.timeout =</span> [ 接続タイムアウト（秒）] </li> 
     <li id="li_4B751F238A1643A7AC730CD9354887B6"><span class="codeph"> contentServer.pollFrequency =</span> [ サーバーをポーリングする頻度（日数）（最小は 1 日）] </li> 
     <li id="li_8E23C3C6E7EF46B0AFDD7993DE79F142"><span class="codeph"> contentServer.pollTime =</span> [ サーバーをポーリングする時刻（午前 0 時からの分単位）] </li> 
    </ul> <p>節を必ずお読みください <i>CRL および ECI ファイル</i> キャッシュを最新の状態に保つ方法について </p> </td> 
  </tr> 
  <tr> 
   <td> 個別化 CA CRL </td> 
   <td> <p>この証明書失効リスト (CRL) 配布ポイントは、個別化サーバーによって発行された各コンピューター証明書に含まれます。 ライセンスサーバーでのコンピューター証明書の検証中に、CRL は証明書に一覧表示されている配布ポイントからダウンロードされ（既にダウンロードされている場合はキャッシュから読み取られ）、証明書が失効していないか確認されます。 個別化 CA CRL の作成とデプロイのプロセスを完了した後に、このサーバー設定の変更を行うことをお勧めします。 設定を変更した後、個別化サーバーを再起動します。 </p> <p>CRL 配布ポイントの URL を設定するには、 <span class="filepath"> AdobeInitial.properties</span> <span class="codeph"> cert.machine.crldp</span> フィールドに入力します。 </p> </td> 
   <td> 
    <ul id="ul_eq3_lv2_jr"> 
     <li id="li_5E37A9E318D742B6A5E1035120888819"><span class="codeph"> cert.machine.crldp =</span> [CRL 配布ポイント ] </li> 
    </ul> <p>例： </p>
    <p> <code>
      cert.machine.crldp__DEV=<span>tps://onprem-individualization.com</span>CRL/onprem-individualization-ca.crl
     </code></p>
     <p>ライセンス要求が処理されると、ライセンスサーバーはこの CRL を自動的にダウンロードする必要があります。 </p> <p importance="high">注意：この配布ポイントは、 <i>not</i> Primetime DRM によって有効性が確認されました。 この URL が有効であることを確認する必要があります。 無効な URL に起因するエラーは、ライセンスサーバーから検証エラーが表示されるまで表示されません。 </p> </td> 
  </tr> 
  <tr> 
   <td> ログ </td> 
   <td>を設定します。 <span class="filepath"> AdobeInitial.properties</span> 必要に応じてログに記録します。 </td> 
   <td> 
    <ul id="ul_j1v_kw2_jr"> 
     <li id="li_B60002B33A3042FCBE1F694454966469"><span class="codeph"> adobe.weblogs.loc =</span> [ ログファイルが作成されるディレクトリ ] </li> 
     <li id="li_2DD4406FBBF047589BAAAE1C9082D8B3"><span class="codeph"> log.Level =</span> [ ログに表示されるログメッセージの最下位レベル <span class="codeph"> [ デバッグ |情報 ]</span> ] </li> 
     <li id="li_610FAF239A554CE59DAC455174F0CF0A"><span class="codeph"> log.FileName =</span> [ ログファイルのプレフィックス。 日時と拡張子".log"がファイル名に追加されます ] </li> 
     <li id="li_1F2913B209BE4A0E8207FAAD052D1764"><span class="codeph"> log.RollInterval =</span> [ ログをロールする頻度を指定します。] </li> 
     <li id="li_3F46C15488114BB5B41035F710E7A19F"><span class="codeph"> log.RollSize =</span> [ このサイズに達したログをロールします ( <span class="codeph"> RollInterval</span> または <span class="codeph"> RollSize</span> 「到達済み、いずれか先 )」) </li> 
     <li id="li_DA32E862F7B0413885DA20633B682484"><span class="codeph"> log.ReportLogging.Enabled =</span>[ [true] | false ] 個別化レポートの生成にAdobeが使用するデータを含む別のファイルを生成するかどうかを指定します。] </li> 
     <li id="li_465CC6D81B8A484CBF4E7A39F7AF86AA"><span class="codeph"> log.ReportLogging.FileName =</span> [ レポートログファイルのプレフィックス。 日時および <span class="filepath"> .log</span> 拡張子がファイル名に追加されます。 l<span class="codeph"> og.Level</span> プロパティはこのログファイルには適用されませんが、 <span class="codeph"> log.RollInterval</span> および <span class="codeph"> log.RollSize</span> do.] </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> その他 </td> 
   <td></td> 
   <td> 
    <ul id="ul_b3b_g1f_jr"> 
     <li id="li_FACF07CB332D416E91FD34DE48152FAA"><span class="codeph"> deviceinfo.key =</span> [ 暗号化された Base64 エンコードされたキーは、マシントークンに含める前に HMAC デバイス情報に使用されます。 開発/ステージング/実稼動環境ではキーが異なる場合がありますが、特定の環境のすべてのサーバーで同じにする必要があります。] </li> 
     <li id="li_B19C77FD6F91496294DBF836A1922EE1"><span class="codeph"> keys.kgs.server =</span> [ キー生成サーバの場所（キーサーバのプールを表す単一のホスト/ポート）] </li> 
     <li id="li_5DA3C89770804B148EF6FAF01A5AD958"><span class="codeph"> keys.MinQueueSize =</span> [ キューにこの数の鍵が残っているときに、KGS から別の鍵のバッチを取り出す ] </li> 
     <li id="li_0C2E5F2FDB824182A6BE418B041D2F28"><span class="codeph"> status.Timeout =</span> [ ステータスページで KGS に ping を送信し、サーバーに到達できるかどうかを確認します。 指定された時間内に応答が返されなかった場合は、タイムアウトになります。] </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## キー生成サーバー {#section_37FA8EEBA258461F8CFA3ADF37714577}

<table id="table_ats_tk2_js"> 
 <thead> 
  <tr> 
   <th class="entry"> 設定 </th> 
   <th class="entry"> 説明 </th> 
   <th class="entry"> 例 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td> キーの生成 </td> 
   <td></td> 
   <td> 
    <ul id="ul_nlj_ydf_jr"> 
     <li id="li_E4347D572F004BF0B237A662BFE7F3ED"><span class="codeph"> kgs.Threads =</span> [ キーの生成に使用するスレッドの数（マシン上で使用可能なプロセッサの数と同じ）] </li> 
     <li id="li_EDBC2535D48E4A66AEB240DB337187FC"><span class="codeph"> kgs.BatchSize =</span> [ バッチごとに生成するキーの数 ] </li> 
     <li id="li_07B41546D94F42349103BF8AF4605E14"><span class="codeph"> kgs.KeyDirectory =</span> [ キーのバッチファイルを保存するディレクトリ ] </li> 
     <li id="li_F4962C97DC3D491DA7FAC826E38A4459"><span class="codeph"> kgs.MaxQueueSize =</span> [ 生成するキーバッチファイルの最大数 ] </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> ログ </td> 
   <td></td> 
   <td> 
    <ul id="ul_kwq_12f_jr"> 
     <li id="li_5E5D34FE5EB44BB898090494C7DDEBD8"><span class="codeph"> adobe.weblogs.loc =</span> [ ログファイルが作成されるディレクトリ ] </li> 
     <li id="li_0E34CD32CD5E47729B69B50414F93678"><span class="codeph"> log.FileName =</span> [ ログファイルのプレフィックス。 日時および <span class="filepath"> .log</span> ファイル名に拡張子が追加されます ] </li> 
     <li id="li_8AB15ACEC39041A2A04C7301154C6EDB"><span class="codeph"> log.Level =</span> [ ログに表示されるログメッセージの最下位レベル ] </li> 
     <li id="li_A17E84DA3ED243F381FF3A6184A3CAA0"><span class="codeph"> log.RollInterval =</span> [ ログをロールする頻度を指定します。] </li> 
     <li id="li_C2B3D111608945DA9D1428BE98D61664"><span class="codeph"> log.RollSize =</span> [ このサイズに達したログをロールします ( <span class="codeph"> RollInterval</span> または <span class="codeph"> RollSize</span> 「到達済み、いずれか先 )」) </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
