---
description: ブラウザー TVSDK は、ビデオアプリケーションに機能を追加するために実装できる多数の HLS 機能をサポートしています。
title: サポートされる HLS 機能
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '736'
ht-degree: 0%

---

# サポートされる HLS 機能 {#supported-hls-features}

ブラウザー TVSDK は、ビデオアプリケーションに機能を追加するために実装できる多数の HLS 機能をサポートしています。

* [HLS コア再生](#hls-core-playback)
* [HLS の高度な再生機能](#hls-advanced-playback)
* [HLS コンテンツ保護機能](#hls-content-protection)
* [HLS コア広告挿入機能](#hls-core-ad-insertion)
* [HLS の高度な広告挿入機能](#hls-advanced-ad-insertion)
* [HLS 統合](#hls-integrations)

>[!TIP]
>
>以下の機能マトリックスの表では、 ![サポートされているアイコン](assets/supported15.png) は、この機能が現在のリリースでサポートされていることを意味します。

>[!TIP]
>
>Safari 列の「Platform Limitation」は、プラットフォームではサポートの実装が許可されないので、使用例がサポートされていないことを意味します。 挿入の場合は、SSAI を使用します。 重要な再生制限がある場合は、プラットフォームがFlash挿入の使用例をサポートするまで、Safari で強制的に広告にフォールバックします。

<!--<a id="section_9FB9193D5763448CB228B96164661738"></a>-->

次の機能がサポートされています。

<!-- 

Removed Nielsen row 
<table id="table_D9E2D82992554905A0A551CC71AFA189"> 
 <title>HLS integrations</title> 
 <tgroup cols="6"> 
  <colspec colnum="1" colname="col1" colwidth="*" /> 
  <colspec colnum="2" colname="col2" colwidth="*" /> 
  <colspec colnum="3" colname="col3" colwidth="*" /> 
  <colspec colnum="4" colname="col4" colwidth="*" /> 
  <colspec colnum="5" colname="col5" colwidth="*" /> 
  <colspec colnum="6" colname="col7" colwidth="*" /> 
  <thead> 
   <tr> 
    <th colname="col1" morerows="1" class="entry"> Category </th> 
    <th colname="col2" morerows="1" class="entry"> Content type </th> 
    <th colname="col3" morerows="1" class="entry"> Feature </th> 
    <th colname="col4" morerows="1" class="entry"> Flash </th> 
    <th namest="col5" nameend="col7" class="entry"> HTML5 </th> 
   </tr> 
   <tr> 
    <th colname="col5" class="entry"> FF, IE, Chrome, Android Chrome </th> 
    <th colname="col7" class="entry"> Safari, iOS Safari </th> 
   </tr> 
  </thead> 
  <tbody> 
   <tr> 
    <td colname="col1"> Integrations </td> 
    <td colname="col2"> VOD + Live </td> 
    <td colname="col3"> Adobe Analytics VHL integration </td> 
    <td colname="col4">![supported icon](assets/supported15.png) </td> 
    <td colname="col5">![supported icon](assets/supported15.png) </td> 
    <td colname="col7">![supported icon](assets/supported15.png) </td> 
   </tr> 
   <tr> 
    <td colname="col1"> Integrations </td> 
    <td colname="col2"> VOD + Live </td> 
    <td colname="col3"> Nielsen support </td> 
    <td colname="col4">![supported icon](assets/supported15.png) </td> 
    <td colname="col5">![supported icon](assets/supported15.png) </td> 
    <td colname="col7">![supported icon](assets/supported15.png) </td> 
   </tr> 
  </tbody> 
 </tgroup> 
</table>

 -->

## HLS 統合 {#hls-integrations}

| カテゴリ | コンテンツタイプ | 機能 | Flash | HTML5:FF、IE、Chrome、Android Chrome | HTML5:Safari、iOS Safari |
|--- |--- |--- |--- |--- |--- |
| 統合 | VOD + Live | Adobe Analytics VHL 統合 | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) |

## HLS の高度な広告挿入機能 (CSAI) {#hls-advanced-ad-insertion}

| カテゴリ | コンテンツタイプ | 機能 | Flash | HTML5:FF、IE、Chrome、Android Chrome | HTML5:Safari、iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Ad Insertion | VOD | 広告のみ | サポート対象外 | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) |
| Ad Insertion | VOD + Live | ターゲティングパラメーター | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) |
| Ad Insertion | VOD + Live | カスタム広告ポリシー | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) | プラットフォームの制限 |
| Ad Insertion | VOD + Live | 遅延広告読み込み | ![サポートされているアイコン](assets/supported15.png) | サポート対象外 | プラットフォームの制限 |
| Ad Insertion | VOD | コンパニオン広告、バナー広告、クリック可能な広告 | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) |
| Ad Insertion | VOD | VPAID 2.0 | SWF | JavaScript | JavaScript |

## HLS コア広告挿入機能 (CSAI) {#hls-core-ad-insertion}

| カテゴリ | コンテンツタイプ | 機能 | Flash | HTML5:FF、IE、Chrome、Android Chrome | HTML5:Safari、iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Ad Insertion | VOD + Live | プリロール | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) |
| Ad Insertion | VOD + Live | ミッドロール | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) | プラットフォームの制限 |
| Ad Insertion | VOD + Live | ポストロール | VOD のみ | VOD のみ | VOD のみ |
| Ad Insertion | FER VOD | 広告の解像度と動作 | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) | プラットフォームの制限 |
| Ad Insertion | VOD + Live | デフォルトの広告ポリシー | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) | プラットフォームの制限 |
| Ad Insertion | VOD + Live | VAST 2.0/3.0 | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) |
| Ad Insertion | VOD + Live | VMAP 1.0 | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) |
| Ad Insertion | VOD + Live | CRS v3.1 | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) |

## HLS コンテンツ保護機能 {#hls-content-protection}

| カテゴリ | コンテンツタイプ | 機能 | Flash | HTML5:FF、IE、Chrome、Android Chrome | HTML5:Safari、iOS Safari |
|--- |--- |--- |--- |--- |--- |
| コンテンツ保護 | VOD + Live | AES-128 | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) |
| コンテンツ保護 | VOD + Live | Sample-AES | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) |
| コンテンツ保護 | VOD | DRM | Adobeアクセス | サポート対象外 | FairPlay |

## HLS の高度な再生機能 {#hls-advanced-playback}

| カテゴリ | コンテンツタイプ | 機能 | Flash | HTML5:FF、IE、Chrome、Android Chrome | HTML5:Safari、iOS Safari |
|--- |--- |--- |--- |--- |--- |
| 再生 | VOD | オフセットでの再生 | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) |
| 再生 | VOD | オーディオのみの再生 | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) |
| 再生 | VOD | トリック再生 | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) |
| 再生 | VOD | 滑らかなトリック再生 | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) | プラットフォームの制限 |
| 再生 | VOD + Live | ID3 の解析 | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) | サポート対象外 |
| 再生 | VOD + Live | Discontinuity マーカーのサポート | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) |
| 再生 | VOD + Live | トークン化ストリーム | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) | プラットフォームの制限 |
| 再生 | VOD + Live | 請求 | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) |
| 再生 | VOD + Live | Browserify | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) |

## HLS コア再生 {#hls-core-playback}

| カテゴリ | コンテンツタイプ | 機能 | Flash | HTML5:FF、IE、Chrome、Android Chrome | HTML5:Safari、iOS Safari |
|--- |--- |--- |--- |--- |--- |
| 再生 | VOD + Live | 一般的な再生（再生、一時停止、シーク） | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) |
| 再生 | FER VOD | 一般的な再生（再生、一時停止、シーク） | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) |
| 再生 | VOD + Live | 適応ビットレート | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) |
| 再生 | VOD + Live | 608/708キャプション | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) |
| 再生 | VOD + Live | WebVTT | ![サポートされているアイコン](assets/supported15.png) | VOD のみ | VOD のみ |
| 再生 | VOD + Live | マニフェストのフェイルオーバー | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) |
| 再生 | VOD + Live | 高度なフェイルオーバー | ![サポートされているアイコン](assets/supported15.png) | VOD のみ | プラットフォームの制限 |
| 再生 | VOD + Live | QoS とプレーヤーの通知 | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) | QoS の制限のサポート |
| 再生 | VOD + Live | cookie ヘッダーのサポート | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) | プラットフォームの制限 |
| 再生 | VOD + Live | バッファ制御パラメータの設定 | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) | プラットフォームの制限 |
| 再生 | VOD + Live | アダプティブビットレートコントロールの設定 | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) | プラットフォームの制限 |
| 再生 | VOD + Live | カスタムタグ | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) | プラットフォームの制限 |
| 再生 | VOD + Live | 遅延バインディングオーディオ | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) | プラットフォームの制限 |
| 再生 | VOD + Live | 302 リダイレクト | ![サポートされているアイコン](assets/supported15.png) | ![サポートされているアイコン](assets/supported15.png) | プラットフォームの制限 |
