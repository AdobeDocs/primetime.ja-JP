---
seo-title: 時間型ルールの概要
title: 時間型ルールの概要
uuid: 10b7766e-3b1a-4d8a-ba15-46976aa0847d
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---


# 時間型ルール{#time-based-rules}

Primetime DRMは、時間ベースのライセンス制限の「ソフト強制」を使用します。 ビデオの再生中に有効期限が切れた場合、Primetime DRMのデフォルトの動作では、次にビデオストリームが再作成されるまで（`Netstream.stop()`と`Netstream.play()`を呼び出して）再生が制限されません。

デフォルトの動作はソフト強制ですが、次のいずれかのタスクを実行してハード強制を有効にすることもできます。

* ビデオプレーヤーで定期的にライセンスをポーリングし、時間制限がいずれも期限切れになっていないことを確認します。 これは、`DRMManager.loadVoucher(LOCAL_ONLY).`を呼び出すことで達成できます。エラーコードは、ローカルに保存されたライセンスが無効になったことを示します。
* ユーザーが&#x200B;**[!UICONTROL Pause]**&#x200B;をクリックするたびに、現在のビデオタイムスタンプを記録し、`Netstream.stop()`を呼び出すことができます。 ユーザーが再生ボタンをクリックすると、記録された場所をシークして`Netstream.play()`を呼び出すことができます。