---
description: AdobeTVSDKConfig.jsonでは、特定のゾーンのルールとデフォルトのルールを指定できます。
seo-description: AdobeTVSDKConfig.jsonでは、特定のゾーンのルールとデフォルトのルールを指定できます。
seo-title: クリエイティブ選択ルールの例
title: クリエイティブ選択ルールの例
uuid: 0a079544-20c1-4e08-a7e3-7617e72da43a
translation-type: tm+mt
source-git-commit: 3fdae2b6babb578d2cacff970fd9c7b53ad2c5dc

---


# クリエイティブ選択ルールの例 {#sample-creative-selection-rules}

AdobeTVSDKConfig.jsonでは、特定のゾーンのルールとデフォルトのルールを指定できます。

## デフォルトルールの例 {#section_xy4_3fx_hz}

次に、デフォルトのルールのみを定 [!DNL AdobeTVSDKConfig.json] 義するファイルの例を示します。

```
{
    "ads": {
        "rules": {
            "default": [
                {
                    "type": "priority",
                    "stream": "vod",
                    "priority": [
                        "application/x-mpegurl",
                        "application/vnd.apple.mpegurl",
                        "application/x-shockwave-flash",
                        "video/mp4",
                        "video/m4v",
                        "video/x-flv",
                        "video/webm"
                    ]
                },
                {
                    "type": "priority",
                    "stream": "live",
                    "priority": [
                        "application/x-mpegurl",
                        "application/vnd.apple.mpegurl",
                        "video/mp4",
                        "video/m4v",
                        "video/x-flv",
                        "video/webm"
                    ]
                },
                {
                    "type": "normalize",
                    "item": "host",
                    "matches": "ew",
                    "values": [
                        "redirector.gvt1.com"
                    ],
                    "find": "videoplayback/(.*?)/expire/.*?/(.*?)/signature/.*?/",
                    "replace": "videoplayback/$1/expire//$2/signature//"
                }
            ]
        }
    }
}
```

## 追加のゾーン・ルールを含むデフォルト・ルールの例 {#section_ocv_3fx_hz}

次の例は、デフォルトの規則 [!DNL AdobeTVSDKConfig.json] を定義するファイルの例と、特定のゾーンID(この場合はzone **&quot;1234&quot;**)の追加の規則を示しています。

```
{
    "ads": {
        "rules": {
            "default": [
                {
                    "type": "priority",
                    "stream": "vod",
                    "priority": [
                        "application/x-mpegurl",
                        "application/vnd.apple.mpegurl",
                        "application/x-shockwave-flash",
                        "video/mp4",
                        "video/m4v",
                        "video/x-flv",
                        "video/webm"
                    ]
                },
                {
                    "type": "priority",
                    "stream": "live",
                    "priority": [
                        "application/x-mpegurl",
                        "application/vnd.apple.mpegurl",
                        "video/mp4",
                        "video/m4v",
                        "video/x-flv",
                        "video/webm"
                    ]
                },
                {
                    "type": "normalize",
                    "item": "host",
                    "matches": "ew",
                    "values": [
                        "redirector.gvt1.com"
                    ],
                    "find": "videoplayback/(.*?)/expire/.*?/(.*?)/signature/.*?/",
                    "replace": "videoplayback/$1/expire//$2/signature//"
                }
            ],
            
<b>"1234"</b>: [
                {
                    "type": "priority",
                    "matches": "nc",
                    "item": "host",
                    "values": [
                        "my.domain.com",
                        "a.bcd.com"
                    ],
                    "priority": [
                        "application/x-shockwave-flash",
                        "video/mp4",
                        "video/x-flv",
                        "video/quicktime",
                        "video/webm",
                        "application/x-mpegurl",
                        "application/vnd.apple.mpegurl",
                        "application/javascript"
                    ]
                }
            ]
        }
    }
}
```
