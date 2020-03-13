---
description: 正規化ルールは、VAST/VMAPの応答から取得したソースクリエイティブURLに適用するURL変換を定義します。
keywords: normalize rule;creative selection rules
seo-description: 正規化ルールは、VAST/VMAPの応答から取得したソースクリエイティブURLに適用するURL変換を定義します。
seo-title: ルールの標準化
title: ルールの標準化
uuid: ae0364d2-23e2-48d6-b9b6-869cd163080d
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# ルールの標準化 {#normalize-rules}

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
   <td>値は常に正規化する必要があ <span class="codeph"> ります</span>。</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> item</span></td> 
   <td><span class="codeph"> 文字列</span></td> 
   <td><span class="codeph"> ホスト</span></td> 
   <td>現在、ホストのみ <span class="codeph"> がサポー</span> トされています。 この属性は、一致と値の属性が定義され <span class="codeph"> ている</span> 場合 <span class="codeph"> に必ず存在します</span> 。</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> 一致</span></td> 
   <td></td> 
   <td></td> 
   <td>可能な値：
    <ul id="ul_tnf_2hx_hz"> 
     <li><span class="codeph"> eq</span> — 等しい</li> 
     <li><span class="codeph"> ne</span> — 次と等しくない</li> 
     <li><span class="codeph"> co</span> — 次を含む</li> 
     <li><span class="codeph"> nc</span> — 次を含まない</li> 
     <li><span class="codeph"> sw</span> — 次で始まる</li> 
     <li><span class="codeph"> ew</span> — 次で終わる</li> 
    </ul></td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> values</span></td> 
   <td><span class="codeph"> 配列</span></td> 
   <td></td> 
   <td>TVSDKは、ソースクリエイティブの <span class="codeph"> 項目に対し</span> 、一致する属性を使用し <span class="codeph"></span> 、この配列に定義された値と照合します。</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> 検索</span></td> 
   <td><span class="codeph"> regex</span></td> 
   <td></td> 
   <td> 一致するソースクリエイティブURLに適用する正規表現です。</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> 置換</span></td> 
   <td><span class="codeph"> regex</span></td> 
   <td></td> 
   <td> 一致に基づいて置換するソースクリエイティブURLに適用する正規表現。</td> 
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

