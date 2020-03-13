---
description: ブラウザーTVSDKは、ビデオアプリケーションに機能を追加するために実装できる多数のHLS機能をサポートしています。
seo-description: ブラウザーTVSDKは、ビデオアプリケーションに機能を追加するために実装できる多数のHLS機能をサポートしています。
seo-title: サポートされるHLS機能
title: サポートされるHLS機能
uuid: 033d81f8-cea4-4687-b2fb-1524d9164d39
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# サポートされるHLS機能 {#supported-hls-features}

ブラウザーTVSDKは、ビデオアプリケーションに機能を追加するために実装できる多数のHLS機能をサポートしています。

* [HLSコア再生](#hls-core-playback)
* [HLS高度な再生機能](#hls-advanced-playback)
* [HLSコンテンツ保護機能](#hls-content-protection)
* [HLSコア広告挿入機能](#hls-core-ad-insertion)
* [HLSの高度な広告挿入機能](#hls-advanced-ad-insertion)
* [HLS統合](#hls-integrations)

>[!TIP]
>
>以下の機能マトリックスの表では、「サポ ![ート」アイコンは](assets/supported15.png) 、この機能が現在のリリースでサポートされていることを意味します。

>[!TIP]
>
>Safari列の「プラットフォームの制限」は、そのプラットフォームでサポートが実装されていないので、使用事例がサポートされないことを意味します。 挿入の場合は、SSAIを使用します。 再生に関する制限が重要な場合は、プラットフォームが広告挿入の使用例をサポートするまで、SafariでFlashに強制的にフォールバックします。

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

## HLS統合 {#hls-integrations}

| カテゴリ | コンテンツタイプ | 機能 | Flash | HTML5:FF、IE、Chrome、Android Chrome | HTML5:Safari、iOS Safari |
|--- |--- |--- |--- |--- |--- |
| 統合 | VOD + Live | Adobe Analytics VHLの統合 | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |

## HLSの高度な広告挿入機能(CSAI) {#hls-advanced-ad-insertion}

| カテゴリ | コンテンツタイプ | 機能 | Flash | HTML5:FF、IE、Chrome、Android Chrome | HTML5:Safari、iOS Safari |
|--- |--- |--- |--- |--- |--- |
| 広告挿入 | VOD | 広告のみ | 未サポート | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| 広告挿入 | VOD + Live | ターゲット設定パラメーター | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| 広告挿入 | VOD + Live | カスタム広告ポリシー | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | プラットフォームの制限 |
| 広告挿入 | VOD + Live | 遅延広告読み込み | ![サポートアイコン](assets/supported15.png) | 未サポート | プラットフォームの制限 |
| 広告挿入 | VOD | コンパニオン広告、バナー広告、クリック可能な広告 | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| 広告挿入 | VOD | VPAID 2.0 | SWF | JavaScript | JavaScript |

## HLSコア広告挿入機能(CSAI) {#hls-core-ad-insertion}

| カテゴリ | コンテンツタイプ | 機能 | Flash | HTML5:FF、IE、Chrome、Android Chrome | HTML5:Safari、iOS Safari |
|--- |--- |--- |--- |--- |--- |
| 広告挿入 | VOD + Live | プリロール | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| 広告挿入 | VOD + Live | ミッドロール | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | プラットフォームの制限 |
| 広告挿入 | VOD + Live | ポストロール | VODのみ | VODのみ | VODのみ |
| 広告挿入 | FER VOD | 広告の解像度と動作 | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | プラットフォームの制限 |
| 広告挿入 | VOD + Live | デフォルトの広告ポリシー | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | プラットフォームの制限 |
| 広告挿入 | VOD + Live | VAST 2.0/3.0 | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| 広告挿入 | VOD + Live | VMAP 1.0 | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| 広告挿入 | VOD + Live | CRS v3.1 | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |

## HLSコンテンツ保護機能 {#hls-content-protection}

| カテゴリ | コンテンツタイプ | 機能 | Flash | HTML5:FF、IE、Chrome、Android Chrome | HTML5:Safari、iOS Safari |
|--- |--- |--- |--- |--- |--- |
| コンテンツ保護 | VOD + Live | AES-128 | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| コンテンツ保護 | VOD + Live | Sample-AES | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| コンテンツ保護 | VOD | DRM | Adobe Access | 未サポート | FairPlay |

## HLS高度な再生機能 {#hls-advanced-playback}

| カテゴリ | コンテンツタイプ | 機能 | Flash | HTML5:FF、IE、Chrome、Android Chrome | HTML5:Safari、iOS Safari |
|--- |--- |--- |--- |--- |--- |
| 再生 | VOD | オフセットでの再生 | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| 再生 | VOD | オーディオのみの再生 | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| 再生 | VOD | トリック再生 | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| 再生 | VOD | 滑らかなトリック再生 | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | プラットフォームの制限 |
| 再生 | VOD + Live | ID3の解析 | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | 未サポート |
| 再生 | VOD + Live | 不連続マーカのサポート | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| 再生 | VOD + Live | トークン化ストリーム | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | プラットフォームの制限 |
| 再生 | VOD + Live | 請求 | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| 再生 | VOD + Live | ブラウズ | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |

## HLSコア再生 {#hls-core-playback}

| カテゴリ | コンテンツタイプ | 機能 | Flash | HTML5:FF、IE、Chrome、Android Chrome | HTML5:Safari、iOS Safari |
|--- |--- |--- |--- |--- |--- |
| 再生 | VOD + Live | 一般再生（再生、一時停止、シーク） | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| 再生 | FER VOD | 一般再生（再生、一時停止、シーク） | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| 再生 | VOD + Live | 可変ビットレート | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| 再生 | VOD + Live | 608/708キャプション | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| 再生 | VOD + Live | WebVTT | ![サポートアイコン](assets/supported15.png) | VODのみ | VODのみ |
| 再生 | VOD + Live | マニフェストのフェイルオーバー | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| 再生 | VOD + Live | 高度なフェイルオーバー | ![サポートアイコン](assets/supported15.png) | VODのみ | プラットフォームの制限 |
| 再生 | VOD + Live | QoSとプレイヤー通知 | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | 制限付きQoSのサポート |
| 再生 | VOD + Live | cookieヘッダーのサポート | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | プラットフォームの制限 |
| 再生 | VOD + Live | バッファ制御パラメータの設定 | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | プラットフォームの制限 |
| 再生 | VOD + Live | 可変ビットレートコントロールの設定 | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | プラットフォームの制限 |
| 再生 | VOD + Live | カスタムタグ | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | プラットフォームの制限 |
| 再生 | VOD + Live | オーディオの遅延バインディング | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | プラットフォームの制限 |
| 再生 | VOD + Live | 302リダイレクト | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | プラットフォームの制限 |