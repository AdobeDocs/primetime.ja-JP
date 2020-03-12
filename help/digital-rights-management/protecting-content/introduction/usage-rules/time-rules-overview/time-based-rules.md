---
seo-title: 時間ベースのルールの概要
title: 時間ベースのルールの概要
uuid: 10b7766e-3b1a-4d8a-ba15-46976aa0847d
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc

---


# 時間に基づくルール {#time-based-rules}

Primetime DRMは、時間ベースのライセンス制限の「ソフト強制」を使用します。 ビデオの再生中に有効期限が切れた場合、Primetime DRMのデフォルトの動作では、ビデオストリームが次に（およびを呼び出して）再作成されるまで再生が制限され `Netstream.stop()` ませ `Netstream.play()`ん。

デフォルトの動作はソフト強制ですが、次のいずれかのタスクを実行することで、ハード強制を有効にすることもできます。

* ビデオプレーヤーで定期的にライセンスをポーリングし、時間制限が満了していないことを確認します。 これは、ローカルに保存されたライセ `DRMManager.loadVoucher(LOCAL_ONLY).` ンスが無効になったことを示すエラーコードを呼び出すことで達成できます。
* ユーザーがクリックするた **[!UICONTROL Pause]**&#x200B;びに、現在のビデオのタイムスタンプを記録し、を呼び出すことができま `Netstream.stop()`す。 再生ボタンをクリックすると、記録された場所を探し、を呼び出すことができま `Netstream.play()`す。