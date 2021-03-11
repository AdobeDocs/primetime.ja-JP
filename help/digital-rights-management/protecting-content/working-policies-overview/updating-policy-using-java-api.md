---
title: Java APIを使用したDRMポリシーの更新
description: Java APIを使用したDRMポリシーの更新
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 0%

---


# Java API {#updating-a-drm-policy-with-the-java-api}を使用したDRMポリシーの更新

Java APIを使用してDRMポリシーを更新するには：

1. 開発環境を設定し、プロジェクトに[開発環境の設定](../../protecting-content/setting-up-the-sdk/setup-dev-env.md)に記載されているすべてのJARファイルを含めます。
1. DRM `Policy`インスタンスを作成し、ファイルまたはデータベースからDRMポリシーを読み取ります。

   ```
   Policy policy = new Policy(policyBytes);
   ```

1. DRM `Policy`オブジェクトのプロパティ（名前や使用ルールなど）を設定して、DRM オブジェクトを更新します。

   ```java
   // Change the DRM policy name.  
   policy.setName("UpdatedDemoPolicy");  
   
   // Add DRM module restrictions to the play right  
   for (Right r: policy.getRights()) {  
       if (r instanceof PlayRight) {  
           PlayRight pr = (PlayRight) r;  
           // Disallow Linux versions up to and including 1.9.  Allow  
           // all other OSes and Linux versions above 1.9  
           VersionInfo toExclude = new VersionInfo();  
           toExclude.setOS("Linux");  
           toExclude.setReleaseVersion("1.9");  
           Collection<VersionInfo> exclusions = new ArrayList<VersionInfo>();  
           exclusions.add(toExclude);  
           ModuleRequirements drmRestrictions = new ModuleRequirements();  
           drmRestrictions.setExcludedVersions(exclusions);  
           pr.setDRMModuleRequirements(drmRestrictions);  
           break;  
       }  
   }
   ```

1. 更新されたDRM `Policy`オブジェクトをシリアル化し、ファイルまたはデータベースに保存します。

   ```java
   // Serialize the DRM policy.  
   byte[] policyBytes = policy.getBytes();  
   System.out.println("New DRM policy revision number: "  
       +  policy.getRevision());      
   // Write the DRM policy to a file.   
   // Alternatively, the DRM policy may be stored in a database.  
   FileOutputStream out = new FileOutputStream("demopolicy-updated.pol");  
   out.write(policyBytes);  
   out.close();
   ```

このサンプルコードのソースについては、リファレンス実装のコマンドラインツール[!DNL samples]ディレクトリの`com.adobe.flashaccess.samples.policy.UpdatePolicy`を参照してください。
