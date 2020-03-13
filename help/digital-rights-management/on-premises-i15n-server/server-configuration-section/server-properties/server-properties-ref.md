---
seo-title: サーバープロパティリファレンス
title: サーバープロパティリファレンス
uuid: 24a187fe-9b7d-411f-a358-d10c70a5dd0e
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# サーバープロパティリファレンス{#server-properties-reference}

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
   <td>トランスポート証明書は、クライアントから受信した要求を復号化し、送信された応答に署名するために使用されます。 必ず、AdobeInitial.properties <span class="filepath"></span> ファイルをトランスポート秘密鍵証明書ファイルへのパスと、暗号化されたPKCS12パスワードの両方で適切に設定してください。 </td> 
   <td> 
    <ul id="ul_itx_fl2_jr"> 
     <li id="li_A2E65253F37245268A41E6B9C958C8DF"><span class="codeph"> cert.i15n.transport.file = </span> [PKCS12ファイルに個別化トランスポート証明書とキーが含まれています] </li> 
     <li id="li_28CDFC0B3D684795AF4708B6D26DF83F"><span class="codeph"> cert.i15n.transport.password =</span> [PKCS12ファイルの暗号化パスワード] </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> 個別化CA証明書 </td> 
   <td>個別化サーバーは、Individualization CA秘密鍵証明書を使用して、発行するコンピューター証明書に署名します。 必ず、AdobeInitial.properties <span class="filepath"></span> ファイルを、I15N CA秘密鍵証明書ファイルへのパスと、暗号化されたPKCS12パスワードの両方を使用して適切に設定してください。 </td> 
   <td> 
    <ul id="ul_xsj_nl2_jr"> 
     <li id="li_5A770D8A482F41A4A9AB63CA52C2EB90"><span class="codeph"> cert.i15n.ica.file =</span> [PKCS12ファイルに個別化CA証明書とキーが含まれています] </li> 
     <li id="li_C3C4A2D9AA2A4F86B6DDCFFD9CB55CBB"><span class="codeph"> cert.i15n.ica.password =</span> [PKCS12ファイルの暗号化パスワード] </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> 個別化の暗号化証明書 </td> 
   <td> 個別化サーバーは、Encryption秘密鍵証明書を使用して、個別化サーバーに送信する必要のある機密ファイルを暗号化します。 例えば、この証明書はライセンスの移行をサポートし、個別化サーバーのDRM秘密鍵の暗号化にも使用されます。 </td> 
   <td> 
    <ul id="ul_nbr_kpd_w5"> 
     <li id="li_4226AD6CC85740669DAF467EFD00BBBE"><span class="codeph"> cert.i15n.decryption.file=i15n_transport.pfx</span> </li> 
     <li id="li_F51BDD94F4724FA58CEF9470B6FEE33B"><span class="codeph"> cert.i15n.decryption.password=password</span> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> コンテンツキャッシュ </td> 
   <td>これらの設定は、個別化サーバーがコンテンツをダウンロードする場所と、コンテンツがディスク上でキャッシュされる場所を制御します。 個別化サーバーは、起動時に1回コンテンツサーバーで新しいコンテンツを確認し、次にこれらのプロパティで指定された頻度/時間で確認します。 <p>オンプレミスの個別化サーバーの場合、コンテンツキャッシュデータの初期セットが含まれています。 キャッシュフォルダーの <i>CONTENTS</i> （キャッシュフォルダー自体ではなく）を、設定済みの <span class="filepath"> AdobeInitial.properties</span> contentServer.localDirectoryの場所にコピーしてください <span class="codeph"></span> 。 </p> </td> 
   <td> 
    <ul id="ul_r4n_1r2_jr"> 
     <li id="li_CA5F562577B04B4A9966EF46E039A137"><span class="codeph"> contentServer.localDirectory =</span> [ローカルコンテンツ（通常はtomcat/temp）を保存するディレクトリ] </li> 
     <li id="li_9A78FBD6C54D47708226378340B46E8E"><span class="codeph"> contentServer.server =</span> [ECI情報に関する連絡先のWebサーバー(このリリ<i>ースではサポートされません</i>)] </li> 
     <li id="li_4E7D7F76085D411688B5003E855F860B"><span class="codeph"> contentServer.timeout =</span> [接続タイムアウト、秒数] </li> 
     <li id="li_4B751F238A1643A7AC730CD9354887B6"><span class="codeph"> contentServer.pollFrequency =</span> [サーバーのポーリング頻度（最小値は1日）] </li> 
     <li id="li_8E23C3C6E7EF46B0AFDD7993DE79F142"><span class="codeph"> contentServer.pollTime =</span> [真夜中からの経過時間（分単位）で、サーバーのポーリングにかかる時間] </li> 
    </ul> <p>キャッシュを最新の状態に保つ方法については、 <i>CRLおよびECI Filesの節を</i> 必ずお読みください。 </p> </td> 
  </tr> 
  <tr> 
   <td> 個別化CA CRL </td> 
   <td> <p>この証明書失効リスト(CRL)配布ポイントは、個別化サーバーによって発行される各コンピューター証明書に含まれます。 ライセンスサーバーでのコンピューター証明書の検証中、CRLは証明書に一覧表示されている配布ポイントからダウンロードされ（または、既にダウンロードされている場合はキャッシュから読み取られ）、証明書が失効していないことを確認します。 個別化CA CRLの作成およびデプロイのプロセスを経た後に、このサーバー設定の変更を実行することをお勧めします。 設定を変更したら、個別化サーバーを再起動します。 </p> <p>CRL配布ポイントのURLを設定するには、 <span class="filepath"> AdobeInitial.properties</span> cert.machine.crldp <span class="codeph"></span> フィールドを設定する必要があります。 </p> </td> 
   <td> 
    <ul id="ul_eq3_lv2_jr"> 
     <li id="li_5E37A9E318D742B6A5E1035120888819"><span class="codeph"> cert.machine.crldp =</span> [CRL配布ポイント] </li> 
    </ul> <p>例： </p>
    <p> <code>
      cert.machine.crldp__DEV=<span>tps://onprem-individualization.com</span>CRL/onprem-individualization-ca.crl
     </code></p>
     <p>ライセンス要求が処理されると、ライセンスサーバーはこのCRLを自動的にダウンロードする必要があります。 </p> <p importance="high">注意：この配布ポイントは、Primetime DRM <i>によって</i> 、有効性に関してチェックされません。 このURLが有効であることを確認する必要があります。 無効なURLによるエラーは、ライセンスサーバーから検証エラーが表示されるまで表示されません。 </p> </td> 
  </tr> 
  <tr> 
   <td> ログ </td> 
   <td>必要に応じて <span class="filepath"> 、AdobeInitial.propertiesを設定し</span> 、ログを記録します。 </td> 
   <td> 
    <ul id="ul_j1v_kw2_jr"> 
     <li id="li_B60002B33A3042FCBE1F694454966469"><span class="codeph"> adobe.weblogs.loc =</span> [ログファイルが作成されるディレクトリ] </li> 
     <li id="li_2DD4406FBBF047589BAAAE1C9082D8B3"><span class="codeph"> log.Level =</span> [ログに表示されるログメッセージの最下位レベル <span class="codeph"> 。 [DEBUG| INFO]</span> ] </li> 
     <li id="li_610FAF239A554CE59DAC455174F0CF0A"><span class="codeph"> log.FileName =</span> [ログファイルの接頭辞] 日付/時刻と拡張子「.log」がファイル名に追加されます] </li> 
     <li id="li_1F2913B209BE4A0E8207FAAD052D1764"><span class="codeph"> log.RollInterval =</span> [ログがロールされる頻度を指定します。] </li> 
     <li id="li_3F46C15488114BB5B41035F710E7A19F"><span class="codeph"> log.RollSize =</span> [ログがこのサイズに達するとログがロールされます(RollIntervalまたは <span class="codeph"> RollSize</span> (いずれか最初に達するとログがロールされます <span class="codeph"></span> ))] </li> 
     <li id="li_DA32E862F7B0413885DA20633B682484"><span class="codeph"> log.ReportLogging.Enabled =</span>[ [true| false ]個別化レポートの生成にアドビが使用するデータを含む別のファイルを生成するかどうかを指定します。] </li> 
     <li id="li_465CC6D81B8A484CBF4E7A39F7AF86AA"><span class="codeph"> log.ReportLogging.FileName =</span> [レポートログファイルの接頭辞] ファイル名には <span class="filepath"> 日付</span> /時間と.log拡張子が追加されます。 log.Level<span class="codeph"> プロパティはこのログファイルには適用されませんが、</span> log.RollIntervalと <span class="codeph"> log.RollSizeは適用されます</span><span class="codeph"></span> 。] </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> その他 </td> 
   <td></td> 
   <td> 
    <ul id="ul_b3b_g1f_jr"> 
     <li id="li_FACF07CB332D416E91FD34DE48152FAA"><span class="codeph"> deviceinfo.key =</span> [Encrypted Base64 encoded key used to HMAC device info before include in the machine token. 開発/ステージング/実稼働環境ではキーが異なる場合がありますが、特定の環境のすべてのサーバーで同じにする必要があります。] </li> 
     <li id="li_B19C77FD6F91496294DBF836A1922EE1"><span class="codeph"> keys.kgs.server =</span> [キー生成サーバーの場所（キーサーバーのプールを表す単一のホスト/ポート）] </li> 
     <li id="li_5DA3C89770804B148EF6FAF01A5AD958"><span class="codeph"> keys.MinQueueSize =</span> [キューに多数のキーが残っている場合に、KGSから別のキーのバッチを取得する] </li> 
     <li id="li_0C2E5F2FDB824182A6BE418B041D2F28"><span class="codeph"> status.Timeout =</span> [ステータスページでKGSに対してpingを実行し、サーバーに到達できるかどうかを確認します。 指定された時間内に応答が返されない場合はタイムアウトします。] </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## 鍵生成サーバ {#section_37FA8EEBA258461F8CFA3ADF37714577}

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
   <td> 鍵の生成 </td> 
   <td></td> 
   <td> 
    <ul id="ul_nlj_ydf_jr"> 
     <li id="li_E4347D572F004BF0B237A662BFE7F3ED"><span class="codeph"> kgs.Threads =</span> [キーの生成に使用するスレッドの数（マシン上で使用可能なプロセッサの数と等しくなる必要があります）] </li> 
     <li id="li_EDBC2535D48E4A66AEB240DB337187FC"><span class="codeph"> kgs.BatchSize =</span> [バッチごとに生成するキーの数] </li> 
     <li id="li_07B41546D94F42349103BF8AF4605E14"><span class="codeph"> kgs.KeyDirectory =</span> [キーバッチファイルを保存するディレクトリ] </li> 
     <li id="li_F4962C97DC3D491DA7FAC826E38A4459"><span class="codeph"> kgs.MaxQueueSize =</span> [生成するキーバッチファイルの最大数] </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> ログ </td> 
   <td></td> 
   <td> 
    <ul id="ul_kwq_12f_jr"> 
     <li id="li_5E5D34FE5EB44BB898090494C7DDEBD8"><span class="codeph"> adobe.weblogs.loc =</span> [ログファイルが作成されるディレクトリ] </li> 
     <li id="li_0E34CD32CD5E47729B69B50414F93678"><span class="codeph"> log.FileName =</span> [ログファイルの接頭辞] 日付/時刻と <span class="filepath"> .log</span> 拡張子がファイル名に追加されます] </li> 
     <li id="li_8AB15ACEC39041A2A04C7301154C6EDB"><span class="codeph"> log.Level =</span> [ログに表示されるログメッセージの最下位レベル] </li> 
     <li id="li_A17E84DA3ED243F381FF3A6184A3CAA0"><span class="codeph"> log.RollInterval =</span> [ログがロールされる頻度を指定します。] </li> 
     <li id="li_C2B3D111608945DA9D1428BE98D61664"><span class="codeph"> log.RollSize =</span> [ログがこのサイズに達するとログがロールされます(RollIntervalまたは <span class="codeph"> RollSize</span> (いずれか最初に達するとログがロールされます <span class="codeph"></span> ))] </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
