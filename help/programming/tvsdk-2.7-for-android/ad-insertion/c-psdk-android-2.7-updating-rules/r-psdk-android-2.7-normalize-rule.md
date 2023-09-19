---
description: 正規化ルールでは、VAST/VMAP 応答から取得されたソースクリエイティブ URL に適用する URL 変換を定義します。
keywords: ルールの標準化；クリエイティブ選択ルール
title: ルールの標準化
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---

# ルールの標準化 {#normalize-rules}

正規化ルールでは、VAST/VMAP 応答から取得されたソースクリエイティブ URL に適用する URL 変換を定義します。

## 標準化ルールには、次の属性と可能な値があります。

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
   <td>値は常に <span class="codeph"> 正規化</span>.</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> 項目</span></td> 
   <td><span class="codeph"> 文字列</span></td> 
   <td><span class="codeph"> ホスト</span></td> 
   <td>現在のみ <span class="codeph"> ホスト</span> はサポートされています。 この属性は、 <span class="codeph"> 一致する</span> および <span class="codeph"> 値</span> 属性が定義されている。</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> 一致する</span></td> 
   <td></td> 
   <td></td> 
   <td>可能な値：
    <ul id="ul_tnf_2hx_hz"> 
     <li><span class="codeph"> eq</span>  — 等しい</li> 
     <li><span class="codeph"> ne</span>  — 等しくない</li> 
     <li><span class="codeph"> co</span>  — 次を含む</li> 
     <li><span class="codeph"> nc</span>  — 次を含まない</li> 
     <li><span class="codeph"> sw</span>  — で始まる</li> 
     <li><span class="codeph"> ew</span>  — で終わる</li> 
    </ul></td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> 値</span></td> 
   <td><span class="codeph"> 配列</span></td> 
   <td></td> 
   <td>TVSDK は、 <span class="codeph"> 一致する</span> 属性 <span class="codeph"> 項目</span> ソースクリエイティブの。この配列で定義された値と一致します。</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> 検索</span></td> 
   <td><span class="codeph"> 正規表現</span></td> 
   <td></td> 
   <td> 照合するソースクリエイティブ URL に適用する正規表現です。</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> 置換</span></td> 
   <td><span class="codeph"> 正規表現</span></td> 
   <td></td> 
   <td> 一致に基づいて置き換えるソースクリエイティブ URL に適用する正規表現です。</td> 
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
