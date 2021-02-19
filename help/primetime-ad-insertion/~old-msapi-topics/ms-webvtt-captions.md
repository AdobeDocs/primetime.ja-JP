---
description: マニフェストサーバーは、パブリッシャー対応のWebVTTキャプションを、すべてのHLSビデオ形式でサポートしています。 WebVTTのキャプション付きコンテンツに広告を挿入する要求を受け取ると、正しく挿入されます。
seo-description: マニフェストサーバーは、パブリッシャー対応のWebVTTキャプションを、すべてのHLS/DASHビデオ形式でサポートしています。 WebVTTのキャプション付きコンテンツに広告を挿入する要求を受け取ると、正しく挿入されます。
seo-title: WebVTTキャプションのサポート
title: WebVTTキャプションのサポート
uuid: 1dc728b0-5aeb-4c48-8f3b-54ff4b135742
translation-type: tm+mt
source-git-commit: e437f4143fb939f46d106c64efc391137c33fe17
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---


# WebVTTキャプション{#support-for-webvtt-captions}のサポート

マニフェストサーバーは、HLS/DASHビデオ形式用に、パブリッシャー対応のWebVTTキャプションをサポートしています。 WebVTTのキャプション付きコンテンツに広告を挿入する要求を受け取ると、正しく挿入されます。

パブリッシャーがコンテンツにWebVTTキャプションを含む場合、マニフェストサーバーはキャプションを含むコンテンツストリームをクライアントに送信します。 マニフェストサーバーでキャプションをサポートするには、パブリッシャーがWebVTTを有効にする必要があります。 クライアントでWebVTTキャプションが有効になっていて、マニフェストサーバーにリクエストを送信すると、マニフェストサーバーはタイムラインとWebVTTトラックを操作し、広告とキャプションが関連付けられたコンテンツをクライアントに返します。

VODコンテンツストリームのワークフローは次のとおりです。

1. クライアントは、WebVTTキャプションが有効になっているコンテンツストリームをマニフェストサーバーに送信します。
1. マニフェストサーバーがタイムラインを操作して、広告をコンテンツストリームに結合します。
1. マニフェストサーバーはWebVTTトラックを操作して、コンテンツ（広告を含む）にキャプションを追加します。
1. マニフェストサーバーは、広告とキャプションを挿入して、コンテンツストリームをクライアントに配信します。

>[!NOTE]
>
>WebVTTキャプションセグメントがミッドロール広告内にある場合、そのミッドロール広告の時間の前後にキャプションが再生されることがビューアに示されます。 例えば、30秒のミッドロール広告が5秒のマークにある10秒のキャプションセグメントでは、ミッドロール広告の時間の前に5秒間、ミッドロールの後に5秒間、キャプションセグメントが表示されます。

>[!NOTE]
>
>クライアントが英語などの特定の言語でビデオを再生するよう要求し、その後フランス語でビデオを再生するよう要求した場合、マニフェストサーバーは、クライアントが言語をフランス語に変更するよう要求したことを検出できません。 クライアントがマニフェストサーバーと通信しないので、マニフェストサーバーは広告のM3U8マスターファイルで指定された最初の言語を使用して、ビデオストリームに広告キャプションを挿入します。