---
description: CRSは、ジャストインタイム(JIT)と非同期の再パッケージングおよびHLSからHLSへの変換を提供します。 再パッケージ化の結果、元の広告クリエイティブがHLS形式にフォーマットされたバージョンになります。 CRSは、HLS形式のバージョンをコンテンツ配信ネットワーク(CDN)サーバーに配置し、必要に応じて使用します。
seo-description: CRSは、ジャストインタイム(JIT)と非同期の再パッケージングおよびHLSからHLSへの変換を提供します。 再パッケージ化の結果、元の広告クリエイティブがHLS形式にフォーマットされたバージョンになります。 CRSは、HLS形式のバージョンをコンテンツ配信ネットワーク(CDN)サーバーに配置し、必要に応じて使用します。
seo-title: CRSの主な使用方法
title: CRSの主な使用方法
uuid: df2caa67-bc94-4146-9b93-14edc060c3d5
translation-type: tm+mt
source-git-commit: e1e33d3ac0aad44859cd49566331524da72ac7e4
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---


# CRS {#main-uses-of-crs}の主な使用方法

CRSは、ジャストインタイム(JIT)と非同期の再パッケージングおよびHLSからHLSへの変換を提供します。 再パッケージ化の結果、元の広告クリエイティブがHLS形式にフォーマットされたバージョンになります。 CRSは、HLS形式のバージョンをコンテンツ配信ネットワーク(CDN)サーバーに配置し、必要に応じて使用します。

JITで、Adobe Primetimeの再パッケージングを行い、広告挿入は、非HLS広告クリエイティブに初めて遭遇すると再パッケージ化プロセスを開始します。 これは通常、再パッケージ化プロセス中に広告を実行する機会を失うことになります。

非同期再パッケージングでは、広告クリエイティブが必要になる前にトランスコードされて保存されるので、そのような失われたオポチュニティを排除できます。

HLSからHLSへの変換では、CRSは、再生の一貫性を保つために、HLSおよびクリエイティブを適切なサイズのチャンクに再フォーマットします。

## ジャストインタイム再パッケージ化{#section_1BA344F2300B49F291865A7461EDFEAE}

JIT再パッケージ化の順序は次のとおりです。

1. マニフェストサーバーは広告を取得します。
1. 広告の形式がHLSの場合、マニフェストサーバーは広告をコンテンツストリームに挿入します。
1. 形式がHLSでない場合（MP4、FLV、WebMなど）、マニフェストサーバーはCDNサーバー上でトランスコードされたバージョンを探します。 見つかった場合は、トランスコードされた広告をコンテンツストリームに挿入します。
1. 形式がHLSではなく、CDNサーバーでトランスコードされたバージョンがない場合、マニフェストサーバーは広告をCRSに渡し、CRSは広告クリエイティブをトランスコードし、結果を後で使用できるようにCDNサーバーに保存します。
1. マニフェストサーバーは、広告なしのコンテンツを返します。

## 非同期再パッケージ化{#section_ACDFB43FDA4B445CB9F2A107FEB4F2F7}

[APIの再パッケージ化](../~old-creative-repackaging-service/api-repackage.md)で説明されているAPIを使用して、非HLSクリエイティブを事前にトランスコードし、インプレッションの損失を最小限に抑え、収益化を最大化できます。

## HLSからHLSへの変換{#section_877A0E7E8FAF4C2DB086A31C24D53435}

バッファリングと遅延を回避するために、クライアントはビデオを小さなチャンクでダウンロードします。 チャンクサイズが一致しない場合、再生がぎくしゃくしている可能性があります。 HLSからHLSへの変換により、データチャンクはすべて同じ時間（例えば、6秒）になります。

>[!NOTE]
>
>CRSは、受け取るHLSバージョンに関係なく、HLSバージョン3を生成します。