---
description: システムがハードウェアアシストデコードにアクセスできる場合、iFrame形式を使用する純粋なソフトウェアTVSDK実装よりもスムーズなトリック再生を実現できます。
seo-description: システムがハードウェアアシストデコードにアクセスできる場合、iFrame形式を使用する純粋なソフトウェアTVSDK実装よりもスムーズなトリック再生を実現できます。
seo-title: よりスムーズなトリック再生操作
title: よりスムーズなトリック再生操作
uuid: 959d6c67-b64f-4666-8de7-54d247459fd1
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 0%

---


# よりスムーズなトリック再生操作{#smoother-trick-play-operations}

システムがハードウェアアシストデコードにアクセスできる場合、iFrame形式を使用する純粋なソフトウェアTVSDK実装よりもスムーズなトリック再生を実現できます。

<!--<a id="section_3DBFD7A3D1C7453096D3D3885E786263"></a>-->

iFrame形式を使用すると、トリック再生操作がスムーズでなくなります。 スムーザーなトリック再生操作では、通常の（iFrameではなく）プロファイル、ハードウェアデコードのサポートおよびフレームレートの向上が使用されます。 ハードウェアアシストのデコード装置が異なると、機能も異なります。 重複速度には60 fps（フレーム/秒）が必要で、4倍の速度には120 FPSが必要です。

>[!IMPORTANT]
>
>Adobeでは、新しいAndroidデバイスでは再生速度を重複速度に制限し、古いAndroidデバイスではこの機能を使用しないことをお勧めします。

よりスムーズなトリック再生を実現するには、`ABRControlParameters.maxPlayoutRate`を通常の速度の目的の倍数(例えば、重複速度が2.0)に設定します。 `MediaPlayer.setRate()`への後続の呼び出しに、`maxPlayoutRate`に対して設定した値以下の引数がある場合、TVSDKは通常のプロファイルを使用して、よりスムーズなトリック再生を実現します。 それ以外の場合は、iFrameプロファイルを使用してトリック再生操作が行われます。