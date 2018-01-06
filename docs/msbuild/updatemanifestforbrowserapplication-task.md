---
title: "Updatemanifestforbrowserapplication — zadanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UpdateManifestForBrowserApplication task [WPF MSBuild]
- adding the <hostInBrowser /> element to the application manifest [WPF MSBuild]
- building XBAP projects [WPF MSBuild]
- UpdateManifestForBrowserApplication task [WPF MSBuild], parameters
ms.assetid: 653339f7-654b-4d64-a26a-5c9f27036895
caps.latest.revision: "8"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: be3b239381b7b1f0afe0b284694ef18d851b313a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="updatemanifestforbrowserapplication-task"></a>UpdateManifestForBrowserApplication — Zadanie
<xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> Zadanie zostanie uruchomione, aby dodać  **\<hostinbrowser — / >** element do manifestu aplikacji (*projectname*. exe.manifest) podczas [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)] skompilować projekt.  
  
## <a name="task-parameters"></a>Parametry zadania  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`ApplicationManifest`|Wymagane **[ITaskItem]** parametru.<br /><br /> Określa ścieżkę i nazwę pliku manifestu aplikacji, które chcesz dodać `<hostInBrowser />` elementu.|  
|`HostInBrowser`|Wymagane **logiczna** parametru.<br /><br /> Określa, czy można zmodyfikować manifest aplikacji do uwzględnienia  **\<hostinbrowser — / >** elementu. Jeśli **true**, nowy `<` **hostinbrowser — / >** element znajduje się w  **\<entryPoint / >** elementu. Należy pamiętać, że element jest uwzględnienie: Jeśli  **\<hostinbrowser — / >** element już istnieje, jest ono usuwane lub zastąpione. Zamiast tego dodatkowe  **\<hostinbrowser — / >** utworzeniu elementu. Jeśli **false**, manifest aplikacji nie jest modyfikowany.|  
  
## <a name="remarks"></a>Uwagi  
 [!INCLUDE[TLA2#tla_xbap#plural](../msbuild/includes/tla2sharptla_xbapsharpplural_md.md)]są uruchamiane przy użyciu [!INCLUDE[TLA#tla_clickonce](../msbuild/includes/tlasharptla_clickonce_md.md)] wdrożenia i, w związku z tym musi przez opublikowane wraz z pomocniczymi manifesty wdrażania i aplikacji. [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)]używa [generateapplicationmanifest —](http://msdn2.microsoft.com/library/6wc2ccdc.aspx) zadań, aby wygenerować manifest aplikacji.  
  
 Następnie, aby skonfigurować aplikację ma być obsługiwana przez przeglądarkę, element dodatkowy  **\<hostinbrowser — / >** muszą zostać dodane do manifestu aplikacji jako Pokaż w poniższym przykładzie:  
  
```xml  
<!--MyXBAPApplication.exe.manifest-->  
<?xml version="1.0" encoding="utf-8"?>  
<asmv1:assembly ... >  
    <asmv1:assemblyIdentity ... />  
    <application />  
    <entryPoint>  
      ...  
      <hostInBrowser xmlns="urn:schemas-microsoft-com:asm.v3" />  
    </entryPoint>  
  ...  
/>  
```  
  
 <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> Zadanie zostanie uruchomione, gdy [!INCLUDE[TLA2#tla_xbap](../msbuild/includes/tla2sharptla_xbap_md.md)] projekt jest budowany, aby można było dodać `<hostInBrowser />` elementu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób upewnij się, że `<hostInBrowser />` element znajduje się w pliku manifestu aplikacji.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication"  
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="UpdateManifestForBrowserApplicationTask">  
    <UpdateManifestForBrowserApplication  
      ApplicationManifest="MyXBAPApplication.exe.manifest"  
      HostInBrowser="true" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/wpf-msbuild-task-reference.md)   
 [Odwołanie do MSBuild](../msbuild/msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Tworzenie aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)   
 [Aplikacje przeglądarek WPF XAML — omówienie](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)