---
description: 正規化ルールは、VAST/VMAPの応答から取得したソースクリエイティブURLに適用するURL変換を定義します。
keywords: normalize rule;creative selection rules
seo-description: 正規化ルールは、VAST/VMAPの応答から取得したソースクリエイティブURLに適用するURL変換を定義します。
seo-title: ルールの標準化
title: ルールの標準化
uuid: b3ca2c8e-133a-4630-8109-17bf0a91843d
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---


# ルールの標準化{#normalize-rules}

正規化ルールは、VAST/VMAPの応答から取得したソースクリエイティブURLに適用するURL変換を定義します。

## 正規化ルールには、次の属性と可能な値が含まれます。

<table id="table_ljp_tgx_hz">  
 <thead> 
  <tr> 
   <th class="entry"> キー</th> 
   <th class="entry"> タイプ</th> 
   <th class="entry"> 値</th> 
   <th class="entry"> 説明</th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td><span class="codeph"> type</span></td> 
   <td><span class="codeph"> 文字列</span></td> 
   <td><span class="codeph"> 正規化</span></td> 
   <td>値は常に<span class="codeph"> normalize</span>にする必要があります。</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> item</span></td> 
   <td><span class="codeph"> 文字列</span></td> 
   <td><span class="codeph"> ホスト</span></td> 
   <td>現在、<span class="codeph"> host</span>のみがサポートされています。 <span class="codeph">が</span>と一致し、<span class="codeph">の値</span>が定義されている場合、この属性が存在する必要があります。</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> 一致</span></td> 
   <td></td> 
   <td></td> 
   <td>可能な値：
    <ul id="ul_tnf_2hx_hz"> 
     <li><span class="codeph"> eq</span>  — 等しい</li> 
     <li><span class="codeph"> ne</span>  — 次に等しくない</li> 
     <li><span class="codeph"> co</span>  — 次を含む</li> 
     <li><span class="codeph"> nc</span>  — 次を含まない</li> 
     <li><span class="codeph"> sw</span> -開始</li> 
     <li><span class="codeph"> ew</span>  — 次で終わる</li> 
    </ul></td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> values</span></td> 
   <td><span class="codeph"> 配列</span></td> 
   <td></td> 
   <td>TVSDKは、ソースクリエイティブの<span class="codeph">アイテム</span>の<span class="codeph"> matches</span>属性を使用し、この配列で定義されている値と照合します。</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> find</span></td> 
   <td><span class="codeph"> regex</span></td> 
   <td></td> 
   <td> 一致するソースクリエイティブURLに適用する正規式。</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> 置換</span></td> 
   <td><span class="codeph"> regex</span></td> 
   <td></td> 
   <td> 一致に基づいて置換するソースクリエイティブURLに適用する正規式。</td> 
  </tr> 
 </tbody> 
</table>

```
{
    "ads": {
        "rules": {
            "default": [
                {
                ...
                }
                {
                    "
<b>type</b>": "
<b>normalize</b>",
                    "
<b>item</b>": "host",
                    "
<b>matches</b>": "ew",
                    "
<b>values</b>": [
                        "redirector.gvt1.com"
                    ],
                    "
<b>find</b>": "videoplayback/(.*?)/expire/.*?/(.*?)/signature/.*?/",
                    "
<b>replace</b>": "videoplayback/$1/expire//$2/signature//"
                }                
            ]
        }
    }
}
```

