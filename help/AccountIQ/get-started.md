---
title: アカウント IQ アカウント IQ、前提条件およびオンボーディングを開始
description: 'アカウント IQ のオンボーディング、前提条件および使用の手引き。 '
source-git-commit: 258ce10297aa15086a3ed1c1a825af2a30d34d24
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 0%

---


# アカウント IQ の使用を開始する方法 {#onboarding}

アカウント IQ を使用するための前提条件と、オンボーディングして購読者のアカウント共有スコアを調べ始める方法について説明します。

## 前提条件 {#prerequisites}

* 組織は、に登録する必要があります [!DNL Adobe Marketing Cloud] 組織。

* その組織のユーザーは、TVE ダッシュボードの読み取り/書き込みまたは TVE ダッシュボードの読み取り専用に割り当てられる必要があります。

### ブラウザーの前提条件 {#browser-prerequisites}

アカウント IQ は、ホストされる Web サービスです。 これは、次のブラウザーの最新バージョンと互換性があります。

* Google Chrome
* Mozilla Firefox
* Safari バージョン

### アカウント IQ で組織をオンボーディングする方法を教えてください。 {#steps-to-onboard}


これが今の我々の持ち物です この計画では、dma_primetime チェックを取り除き、AIQ 専用のプロファイルを持つことになります。 コンソールにアクセスする必要があるユーザーには、そのユーザープロファイルが必要になります。 ただし、現時点では実装されていません。

1. 組織をAdobe Marketing Cloud @Ericまたは@Peterでオンボーディングすると、これを利用できます。  今は「Experience Cloud」と呼ばれていますが、それはマイナーです。  これに関して詳しい事は？ これは別のグループで管理されていますか？ 該当する場合、リンクや連絡先などを提供していますか。 これには、組織が既にExperience Cloudに含まれているかどうかを確認する際に注意する必要があります。

2. http://adminconsole.adobe.com/でユーザーに「TVE ダッシュボードの読み取り/書き込み」または「TVE ダッシュボードの読み取り専用」のプロファイルを割り当てる。
@Eric、この方法を知ってる？  サブステップはありますか？  読み取り/書き込みと読み取り専用を選択した理由をお客様に説明できますか。
@Cristina、これが一時的なアプローチであり、次のバージョンでどのように機能するかについて簡単に説明できますか？

3. 組織 ID が AIQ 側@Cristinaにホワイトリストに登録されている場合、これを管理するためのプロセスを導入できますか？  例えば、組織の組織 ID などを含む「DL-AdobePass-Eng AdobePass-Eng@adobe.com」に電子メールを送信します。

<!-- these user groups set dma_primetime product context for the user accounts. In AIQ code we’re checking for this product context when providing access. Internally, in the code we have an additional condition: the org id should be whitelisted in order for the users to get access to their data. -->

Enterprise DashboardAdobeにアクセスすると、Adobe Marketing Cloud組織に新しく作成された 2 つのユーザーグループが表示されます。

TVE Dashboard 読み取り/書き込み — このグループのメンバーは、ダッシュボード TVE Dashboard 読み取り専用のすべての編集可能なセクションでフルアクセス権を持ちます — このグループのメンバーは、AdobeEnterprise Dashboard で TVE Dashboard 読み取り/書き込みユーザーグループにアカウントを追加し、Adobe Primetime TVE Dashboard でログインします。  その後、上記の 2 つのユーザーグループ内のユーザーを追加または削除することで、AdobeEnterprise Dashboard でユーザー権限を管理できるようになります。

............

指定したドキュメントには、「Primetime TVE Dashboard User Provisioning の概要」という部分が含まれています。これはAdobe Passコンソールに適用されますが、AIQ にも同様です。
http://tve.helpdocsonline.com/primetime-tve-dashboard-user-guide AIQ に興味を持つ組織は、Adobe Marketing Cloud Orgs に登録されている組織である必要があります。 その組織のユーザーは、TVE ダッシュボードの読み取り/書き込みまたは TVE ダッシュボードの読み取り専用に割り当てる必要があります。
これらのユーザーグループは、ユーザーアカウントに対して dma_primetime 製品コンテキストを設定します。 AIQ コードでは、アクセスを提供する際に、この製品コンテキストを確認しています。 内部的には、コードには追加の条件があります。ユーザーがデータにアクセスできるようにするには、組織 id がホワイトリストに登録されている必要があります。
これが今の我々の持ち物です この計画では、dma_primetime チェックを取り除き、AIQ 専用のプロファイルを持つことになります。 コンソールにアクセスする必要があるユーザーには、そのユーザープロファイルが必要になります。 ただし、現時点では実装されていません。

...........................

1. 組織をAdobe Marketing Cloudでオンボーディングする
2. http://adminconsole.adobe.com/でユーザーに「TVE ダッシュボードの読み取り/書き込み」または「TVE ダッシュボードの読み取り専用」のプロファイルを割り当てる。
3. 組織 ID が AIQ 側でホワイトリストに登録されている
