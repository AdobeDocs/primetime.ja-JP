---
title: Java API を使用した DRM ポリシーの更新
description: Java API を使用した DRM ポリシーの更新
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 0%

---

# Java API を使用した DRM ポリシーの更新 {#updating-a-drm-policy-with-the-java-api}

Java API を使用して DRM ポリシーを更新するには：

1. 開発環境を設定し、プロジェクトに、 [開発環境の設定](../../protecting-content/setting-up-the-sdk/setup-dev-env.md).
1. DRM の作成 `Policy` インスタンスを作成し、ファイルまたはデータベースから DRM ポリシーを読み取ります。

   ```
   Policy policy = new Policy(policyBytes);
   ```

1. DRM の更新 `Policy` オブジェクトに割り当てる必要があります。

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

1. 更新された DRM をシリアル化する `Policy` オブジェクトを作成し、ファイルまたはデータベースに保存します。

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

詳しくは、 `com.adobe.flashaccess.samples.policy.UpdatePolicy` （「参照実装」コマンドラインツール） [!DNL samples] このサンプルコードのソースのディレクトリ。
